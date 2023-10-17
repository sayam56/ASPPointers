#include <stdio.h>
#include <stdlib.h>

//int (*m1)(int,int);
//int (*m2)(int);

int n;

int maxnum(int *n1,int *n2)
{
    if(n1>n2)
        return (void *)n1;
    else
        return (void *)n2;
}


int maxarray(int *ar)
{
    int max = *ar;

    for (int i=0; i<n ;i++){
        if (*ar > max){
            max = *ar;
        }
        ar++;
    }

    return max;
}


int prod(int (*m1)(int *, int *),int (*m2)(int *),int *n1,int *n2, int *ar)
{

    int maxnum_return, maxarray_return;

    //calling the passed method m1 -> maxnum
    maxnum_return=m1((void *) n1, (void *) n2);
    printf(" maxnum_return: %d \n",maxnum_return);

    //calling the passed method m2 -> maxarray
    maxarray_return=m2((void *)ar);
    printf(" maxarray_return: %d \n",maxarray_return);

    return maxnum_return*maxarray_return;
}

int main(void)
{
    // creating dynamic array
    int *dynar;

    //taking the size of array as user input
	printf("\nEnter the number of elements in the array\n");
	scanf("%d",&n);

	//dyunamically allocating the array size
	dynar=malloc(n*sizeof(int));

	//taking user input as array
	printf("\n\n");
	for(int i=0;i<n;i++)
	{
		printf("Enter element %d\n", i+1);
		scanf("%d",&dynar[i]);
	}


	//printing the array in reverse order using deferencing
	printf("\nThe elements of the array in reverse order:\n");

	for(int i=(n-1); i>=0; i--)
	{
		printf("\n%d",*(dynar+i));
	}
	printf("\n\n");

	//static assignment of num1 and num2
	int num1 = 5, num2 = 3;

	//calling prod
    int return_value= prod(&maxnum,&maxarray, num1, num2, dynar);

    printf("\n return value from prod is: %d\n",return_value);

}








