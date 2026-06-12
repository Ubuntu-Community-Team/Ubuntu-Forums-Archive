---
title: "where is gcc installed? newb here"
date: 2012-08-30
forum: General Help
---

### Post by Streetguru2 on 2012-08-30
hey there, new to ubuntu and coding as i will be using it to learn how to code in C(self too gunna be fun...)

i used this to install gcc i think
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
gcc --version

now my only question is...where is it installed? how can i run it? and can it be used to compile programs written in C?

thanks for any answers

---

### Post by coldcritter64 on 2012-08-30
Try in the terminal the commands,

```
which gcc
```and/or

```
locate gcc
```The first one should detect the location of gcc itself, the second should show a list of all files/directories with gcc in the path/filename. Cheers.

---

### Post by taras.kuzyo on 2012-08-30
To find out where its installed:'
```
type gcc
```To compile .c file just run: 
```
gcc foo.c
```
This will produce executable a.out (If you wouldn't have errors)
```
./a.out
```
To run a program.

---

### Post by pgmer6809 on 2012-08-30
> **Streetguru2 said:**
> hey there, new to ubuntu and coding as i will be using it to learn how to code in C(self too gunna be fun...)

i used this to install gcc i think
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
gcc --version

now my only question is...where is it installed? how can i run it? and can it be used to compile programs written in C?

thanks for any answers

In addition to the answers below 
a) most executables are installed in /usr/bin, /usr/local/bin etc.
b) since you installed via a package manager, you can go into the pkg manager (synaptic or ubuntu software center) and type gcc in the search bar. This will find the pkg. You can then click on one of the properties tabs and it will tell you all of the files that that pkg installed; not just the binary executble, but the man pages, and any other scripts and configs. 
This can be very useful indeed.
pgmer6809

---

### Post by Streetguru2 on 2012-09-01
ok! i have found where its installed...now my next question...how do i run it and start writing code/compiling/debugging? =/

---

### Post by jerome1232 on 2012-09-01
> **Streetguru2 said:**
> ok! i have found where its installed...now my next question...how do i run it and start writing code/compiling/debugging? =/

First you get your trusty text editor out and start writing some code, then you use gcc to compile it.

If your looking for an IDE (which is what it sounds like you think gcc is, which it isn't) try Eclipse. it's in the repositories.

---

### Post by dodo3773 on 2012-09-01
> **coldcritter64 said:**
> Try in the terminal the commands,

```
which gcc
```and/or

```
locate gcc
```The first one should detect the location of gcc itself, the second should show a list of all files/directories with gcc in the path/filename. Cheers.

Probably worth mentioning:

```

whereis gcc

```

---

