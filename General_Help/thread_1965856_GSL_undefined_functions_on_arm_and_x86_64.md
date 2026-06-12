---
title: "GSL undefined functions on arm and x86_64"
date: 2012-04-26
forum: General Help
---

### Post by andradx on 2012-04-26
I'm running ubuntu 11.10 on a beagle board and was using the gsl to do some stuff.


I have the following code:

```
void stdoutMatrix(gsl_matrix *);
int main(int argc,char *argv[]){

        gsl_matrix *A=gsl_matrix_alloc(matrixSize,matrixSize);

        gsl_matrix_set_identity(A);

        stdoutMatrix(A);
        // do some row and column operations
        gsl_swap_rows(A,2,5);
        stdoutMatrix(A);
        gsl_swap_columns(A,1,3);
        stdoutMatrix(A);
        gsl_matrix_free(A);

        return -1;
}

void stdoutMatrix(gsl_matrix *A){

        int i,j;
        for(i=0;i<matrixSize;i++){
                for(j=0;j<matrixSize;j++)
                        printf("%g ",gsl_matrix_get(A,i,j));
                printf("\n");
        }
        printf("\n");
}



```


If I comment the gsl_swap_XXXXXX lines, then it compiles, if they're not compiled I get the following error:

gcc main.c -L/usr/lib `pkg-config --libs gsl`

main.c:(.text+0x5d): undefined reference to `gsl_swap_rows'
main.c:(.text+0x84): undefined reference to `gsl_swap_columns'


I thought the definitions were compiled into the dynamic or static library libgsl and libgslcblas (they both exist), but apparently not.

This error is consistent on the beaglebone running linux-3.2.0-psp6 and on a x86_64 system.


I'm manually compiling the gsl on the beagle, but I was hoping some help would arrive before the compile is over.

TY.


Function is gsl_matrix_swap_rows and gsl_matrix_swap_columns and not what I had before, but since the compilation yield no error I thought I was in the clear with the syntax. My bad.

---

