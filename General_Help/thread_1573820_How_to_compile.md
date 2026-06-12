---
title: "How to compile?"
date: 2010-09-13
forum: General Help
---

### Post by zrzhu on 2010-09-13
How do I compile? I downloaded a file, ***. tar.gz. I know its a compressed file, so I unzip it first. In the terminal, I put "make", but it din't work. Do I need to install anything before? I'm using ubuntu 10.04.1. Thanks.

---

### Post by Vigh on 2010-09-13
you may need the build-essentials package

sudo apt-get install build-essentials

then ./configure
then sudo make
then sudo make install 

in terminal

---

### Post by zrzhu on 2010-09-13
> **Vigh said:**
> you may need the build-essentials package

sudo apt-get install build-essentials

then ./configure
then sudo make
then sudo make install 

in terminal

thanks. Ill try it later.

---

### Post by 3Miro on 2010-09-13
What Vigh suggests is what people usually do. Also, every .tar file usually comes with README file that you can open and it will have any specific instructions (if there are any).

---

### Post by BigCityCat on 2010-09-13
I think it's actually sudo apt-get install build-essential

---

### Post by WorMzy on 2010-09-13
Also, you don't need sudo to run "make". Just "make install".

so

```
./configure
```
Look for errors in the output this command generates, it'll alert you to any libraries that the program needs, but you're missing.
```
make
```
This compiles the software in a directory relative to the source code, and is used to check that the program will compile correctly.

```
sudo make install
```
This compiles the program and installs it into the system directories. Don't do this if you got an error during the first run of make.


Of course, this all depends on the type of source code, and what build files it comes with; so there's no guarantee that these commands will work for the source code you've downloaded.

The best way to install programs is through apt-get, Synaptic Package Manager, or Ubuntu Software Centre. Use compilation as a last resort.

---

