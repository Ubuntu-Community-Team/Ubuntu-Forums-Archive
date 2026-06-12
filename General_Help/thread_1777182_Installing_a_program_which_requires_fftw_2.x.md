---
title: "Installing a program which requires fftw 2.x"
date: 2011-06-07
forum: General Help
---

### Post by matteo86bo on 2011-06-07
Hi,
I hope you can help with this little situation that I have. I know it
might be not fair to ask you help me but it's a month I've been trying
to install MPGrafic (google it to open the package) without succeeding.
 (I also have in my home
directory).
The problem is that, in order to install it, I need the 2 version of
the fftw (I've downloaded the 2.1.5 from the fftw website). I install
everything in the folder /libraries (I don't have writing permission on the /usr/lib folder)
 
./configure --enable-mpi --enable-type-prefix --enable-float
--prefix=/libraries
make install
make clean
./configure --enable-mpi --enable-type-prefix --prefix=/libraries
make install
 
But when I try to install MPGrafic:
 
./configure --prefix=/users/mtomas/bin LDFLAGS=-L/libraries/lib/ CPPFLAGS=-I/libraries/include/
 
I got an error: I need the fftw with double precision.
 
So I think the ./configure does not read the library properly, or I need another version of the library or I need other flags.
 
Can you please help me?
 
Cheers

---

### Post by sanderj on 2011-06-07
Why not install fftw-dev via the Ubuntu Software Center, or just "sudo apt-get install fftw-dev"?

---

### Post by matteo86bo on 2011-06-07
Because I do not have permission to write in any /usr folder, I am using a network ...

---

### Post by sanderj on 2011-06-07
> **matteo86bo said:**
> Because I do not have permission to write in any /usr folder, I am using a network ...

And can you ask the system admin to install the fftw-dev package?

---

### Post by matteo86bo on 2011-06-07
Ok, maybe you don't get the question, I'm sorry it must have been my fault.

Anyway, no, the system has an updated version of the fftw I need the old one to get mpgrafic work.

The problem is with the mpgrafic software and its installation flags.

---

