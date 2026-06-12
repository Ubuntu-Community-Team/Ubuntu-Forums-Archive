---
title: "hi I want to run mpi"
date: 2006-05-05
forum: General Help
---

### Post by ebekir on 2006-05-05
I want to run mpi program but &#305; dont know in ubuntu.can you help me to install and boot mpi

---

### Post by xuying2006 on 2006-09-17
Hello:
    I installed mpich2 on a ubuntu 6.06 machine, then share the install directory with a FC5 machine by using NFS. These two machines were connected to each other directly by a cable. The ubuntu machine is connected to a router which connects to internet.

    My problem is that "when I 'mpdcheck -s' on ubuntu machine, "mpdcheck -c ubuntu-machine port " on FC5 succeed. But I can't do it reversely. I mean "when I 'mpdcheck -s' on FC5 machine, "mpdcheck -c fc5 port" failed with the following error:
--------------------------------------------------------------------------------------------
Traceback (most recent call last):
  File "/home/xuying/mpich2-install/bin/mpdcheck", line 103, in ?    sock.connect((argv[argidx+1],int(argv[argidx+2])))  # note double parens
  File "<string>", line 1, in connect
socket.error: (113, 'No route to host')
--------------------------------------------------------------------------------------------

seems a network configuration problem. please help!

---

### Post by arkangel on 2006-09-17
[http://www-unix.mcs.anl.gov/mpi/mpich2/index.htm#download](http://www-unix.mcs.anl.gov/mpi/mpich2/index.htm#download)

donwload  the  tar.gz all sources
unpack it and 

if you want  support for f90  type in a terminal 
export F90=[fortran 90 path here ]   

ex: /usr/bin/g90, but i am using intel fortran 

then type 
./configure --enable-f90 --prefix=[path where to install]

I have it in /opt/mpich2, just an example 
 
make 
make install

you may run  ./configure --help  ,before doing something,  to see what else you can do or read the quick installation guide in the site 

do the same for all your computers , good luck !
if you have a problem post it here

---

### Post by Alason on 2006-10-07
Hello guys,

I download the sources from your link (mpich2-1.0.4p1.tar.gz). And get an error after: ./configure --prefix=/opt/mpich2 

checking whether the compiler implements namespaces... no
configure: error: Namespaces are required for the MPI C++ interface

I try to solve the problem with: apt-get install namespaces and found: libxml-namespacesupport-perl

I installed this package and got the same ./configure error as before. What can I do?

I'm a newbie of kubuntu, but I used SuSE five years before. So please, make it slowly ;)

Thanks for your help.

Greetings,
Alason

---

