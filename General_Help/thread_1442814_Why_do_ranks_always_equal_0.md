---
title: "Why do ranks always equal 0?"
date: 2010-03-30
forum: General Help
---

### Post by ThanhNghiaCNTT on 2010-03-30
I use ubuntu-9.04-desktop-i386.iso on Virtual Machine VMware Workstation. I install MPI but when run MPI then result doesn't true.
[B]#include <mpi.h>
#include  <stdio.h>
int main(int argc, char* argv[]) {
    int rank,  nprocs;
    MPI_Init(&argc, &argv);
     MPI_Comm_rank(MPI_COMM_WORLD, &rank);
     MPI_Comm_size(MPI_COMM_WORLD, &nprocs);
    char s[30];
     gethostname(s, 30);
    printf("Hello world from: host@process_rank =  %s@%d nprocess = %d\n", s, rank,nprocs);
    MPI_Finalize();
     return 0;
}[/B]
command
[B]mpicc  simple.c -o simple
mpirun -np 4 simple[/B]
result
[B]Hello world from: host@process_rank =  ubuntu@0 nprocess = 1
Hello world from: host@process_rank = ubuntu@0  nprocess = 1
Hello world from: host@process_rank = ubuntu@0 nprocess =  1
Hello world from: host@process_rank = ubuntu@0 nprocess = 1[/B]
Why **rank=0,      ****if true 0,1,2,3** ?
I don't understand. 
Thanks,
Peter

---

