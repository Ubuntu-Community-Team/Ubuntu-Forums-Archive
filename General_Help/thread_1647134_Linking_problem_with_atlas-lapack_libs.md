---
title: "Linking problem with atlas-lapack libs"
date: 2010-12-16
forum: General Help
---

### Post by someguynameddave on 2010-12-16
Hey gang,

I am trying to write some linear algebra software on Karmic, and am getting some pure evil at link time. Here is a simple test problem I wrote up:

#include <clapack.h>
#include <iostream>

using namespace std;

int main()
{
  double matrix[] = { 1, 0, 0, 0, 1, 0, 0, 0, 1 };
  const int info = clapack_dpotrf( CblasRowMajor, CblasUpper, 3, matrix, 3 ); 

  cout << "info: " << info << ", matrix: " <<  endl;
  cout << "(" << matrix[0] << ",\t" << matrix[3] << ",\t" << matrix[6] << "," << endl;
  cout << " " << matrix[1] << ",\t" << matrix[4] << ",\t" << matrix[7] << "," << endl;
  cout << " " << matrix[2] << ",\t" << matrix[5] << ",\t" << matrix[8] << ")" << endl;

  return 0;
}

If I try compiling that with the following command:

$ g++ -llapack -lblas lapacktest.cc

I get 

lapacktest.cc:(.text+0xd9): undefined reference to `clapack_dpotrf(CBLAS_ORDER, CBLAS_UPLO, int, double*, int)'

So, that function doesn't appear to be in the library. Sure enough, if I do 

$ objdump -T /usr/lib/liblapack.so | grep clapack_dpotrf

I get nothing. However, if I do 

$ ls -la /usr/lib/liblapack*.so

I get:

lrwxrwxrwx 1 root root 32 2010-12-16 17:22 /usr/lib/liblapack-3.so -> /etc/alternatives/liblapack-3.so
lrwxrwxrwx 1 root root 22 2010-12-16 17:22 /usr/lib/liblapack_atlas.so -> liblapack_atlas.so.3gf
lrwxrwxrwx 1 root root 34 2010-12-16 17:22 /usr/lib/liblapackgf-3.so -> /etc/alternatives/liblapackgf-3.so
lrwxrwxrwx 1 root root 16 2010-12-16 17:22 /usr/lib/liblapack.so -> liblapack.so.3gf

Sure enough, doing 

$ objdump -T /usr/lib/liblapack_atlas.so | grep clapack_dpotr

gives

0000000000014ff4 g    DF .text  0000000000000134  Base        clapack_dpotrf

So, that has the symbol I need, right? Wrong. If I compile with that lib like so:

$ g++ -llapack_atlas -lblas lapacktest.cc

I still get

lapacktest.cc:(.text+0xd9): undefined reference to `clapack_dpotrf(CBLAS_ORDER, CBLAS_UPLO, int, double*, int)'

So, what is going on there? Any help would be greatly appreciated.

Dave

---

