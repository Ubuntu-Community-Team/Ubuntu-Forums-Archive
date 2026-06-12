---
title: "Permission denied to execute even being root"
date: 2011-02-11
forum: General Help
---

### Post by chethan123 on 2011-02-11
Hi,
I am trying to compile this open source code called libupnp. It has automake and I have to run a binary called ./configure in the main directory with required options to generate make files. Here I am facing some "mind blowing" problems, described below. 

I can't run ./configure under user mode it says => Permission denied. 

After this I did, 
> 
sudo ./configure 

It said => sudo: ./configure: command not found


So, I did **sudo su **to become super-user and did ./configure 
It said **"bash: ./configure: Permission denied"** 

Being a root and being denied of permission is **"depressingly funny"** :confused: 

All this time I was working in a directory in one of the mounted drive. So, just to try something I copied the same library to my home directory and to my surprise, I am able to run this ./configure binary even as a normal user!!! 

What Should I makeout of all this? What was the problem? Any Clue? How to comprehend this!

I am using Ubuntu-10.10 by the way... 

PS: Being Root and denied of permission to execute a binary!!! Made me suspect that my was HAL-9000 :D

---

### Post by psusi on 2011-02-11
You don't have execute permission for that file.  Give it to yourself:

chmod a+x configure

---

### Post by chethan123 on 2011-02-11
No, I had done chmod 777 ./configure too!!!
Sorry forgot to mention in post... 
 
Also as mentioned before, When I copied same buildtree to home directory it worked perfectly fine!!! even in normal user mode!

---

### Post by GrantStoner on 2011-02-11
Don't do ```
chmod 777 ./configure
```do ```
chmod 777 configure
```(assuming you're in the right directory)

---

### Post by gmargo on 2011-02-11
Where did you get your source code?  

I downloaded version 1.6.12:
[http://sourceforge.net/projects/pupnp/files/pupnp/libUPnP%201.6.12/libupnp-1.6.12.tar.bz2/download]("http://sourceforge.net/projects/pupnp/files/pupnp/libUPnP%201.6.12/libupnp-1.6.12.tar.bz2/download")
and it configures and compiles just fine.

BTW, _***never***_ compile as root. Enough things can go wrong already; don't make it potentially worse.

> 
When I copies same buildtree to home directory it worked perfectly fine!!!

What filesystem are you using?  Are you trying to do this on a Windows filesystem?

---

### Post by gmargo on 2011-02-11
> **GrantStoner said:**
> Don't do ```
chmod 777 ./configure
```do ```
chmod 777 configure
```(assuming you're in the right directory)

I beg to differ; there is no difference between the two.

---

### Post by chethan123 on 2011-02-11
@gmargo, 
 
Yes same project, but I am using 1.6.10. 
 
My source code was on my pen drive which is FAT32 File system. it matters! Didn't know :) 
 
Compiling as a root was a desperate attempt to compile the code :D

---

### Post by psusi on 2011-02-11
Yea, chmod doesn't work on fat or ntfs.  You should have seen it report an error.

---

### Post by chethan123 on 2011-02-12
Hi psusi,

chmod didn't report any error! I checked again, none!!!

gmargo and psusi, thanks for the help :)[]("http://ubuntuforums.org/member.php?u=1009937")

---

### Post by psusi on 2011-02-12
> **chethan123 said:**
> Hi psusi,

chmod didn't report any error! I checked again, none!!!

gmargo and psusi, thanks for the help :)[]("http://ubuntuforums.org/member.php?u=1009937")

Hrm.. I just tried it and also did not get an error.  Seems to be a bug in ntfs-3g; the kernel NTFS driver correctly reports an error.

---

