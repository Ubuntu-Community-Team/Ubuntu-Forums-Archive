---
title: "Python Development Version"
date: 2011-04-17
forum: General Help
---

### Post by phueaz on 2011-04-17
Hi all,
I've been trying to install MPI4py for a student project I'm working on but I've been having some trouble. I followed some instructions to install open MPI 


[http://auriza.site40.net/notes/mpi/openmpi-on-ubuntu-904/]("http://auriza.site40.net/notes/mpi/openmpi-on-ubuntu-904/")

But when I try to install mpi4py it asks me to install the development version of python. Can anyone tell me how to install this as I can't find anything in the python webpages. 

I'm new to this so not really sure what I should be doing. Any information would be really useful. Thanks in advance.

Error when trying to install mpi4py

python setup.py build
running build
running build_py
running build_ext
MPI C compiler:    /usr/bin/mpicc
MPI C++ compiler:  /usr/bin/mpicxx
MPI linker:        /usr/bin/mpicc
checking for MPI compile and link ...
/usr/bin/mpicc -fPIC -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -I/usr/include/python2.6 -c _configtest.c -o _configtest.o
/usr/bin/mpicc _configtest.o -o _configtest
success!
removing: _configtest.c _configtest.o _configtest
writing build/lib.linux-x86_64-2.6/mpi4py/mpi.cfg
building 'mpi4py.MPI' extension
/usr/bin/mpicc -fPIC -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -I/usr/include/python2.6 -c src/MPI.c -o build/temp.linux-x86_64-2.6/src/MPI.o
In file included from src/MPI.c:3:
src/mpi4py.MPI.c:4:20: error: Python.h: No such file or directory
src/mpi4py.MPI.c:6:6: error: #error Python headers needed to compile C extensions, please install development version of Python.
error: command '/usr/bin/mpicc' failed with exit status 1

---

### Post by phueaz on 2011-04-17
Think I've fixed it

used

[HTML]sudo aptitude install python-dev[/HTML]

and 

[HTML]sudo python setup.py install[/HTML]

works

---

