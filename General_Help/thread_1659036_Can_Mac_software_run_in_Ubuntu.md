---
title: "Can Mac software run in Ubuntu?"
date: 2011-01-03
forum: General Help
---

### Post by Sunrock on 2011-01-03
Recently, I read that the Apple Operating System is just another Linux distro like Ubuntu.  If this is true, can any Mac software run in Ubuntu?

Sunrock

---

### Post by psusi on 2011-01-03
No it isn't, and no it can't.

---

### Post by dnguyen1963 on 2011-01-03
> **Sunrock said:**
> Recently, I read that the Apple Operating System is just another Linux distro like Ubuntu.  If this is true, can any Mac software run in Ubuntu?

Sunrock

Where did you read?  That info is completely wrong.

---

### Post by Sunrock on 2011-01-04
Since I just received two negative replies, I hope someone would clarify the results I found on Wikipedia.  All I am trying to do is understand what I have read.  

The first line for the definition of "Mac OS X" on Wikipedia is "Mac OS X (pronounced /&#712;mæk &#716;o&#650; &#716;&#603;s &#712;t&#603;n/ mak oh es ten)[6] is a series of Unix-based operating systems and graphical user interfaces developed, marketed, and sold by Apple Inc."

The first line for the definition of "Linux" on Wikipedia is "Linux (commonly pronounced /&#712;l&#618;n&#601;ks/ LIN-&#601;ks in American English,[4][5] also pronounced /&#712;l&#618;n&#650;ks/ LIN-ooks[6] in Europe) refers to the family of Unix-like computer operating systems using the Linux kernel. Linux can be installed on a wide variety of computer hardware, ranging from mobile phones, tablet computers and video game consoles, to mainframes and supercomputers.[7][8][9][10]"

Finally on Wikipedia it displays a flow chart ([http://en.wikipedia.org/wiki/File:Unix_history-simple.svg](http://en.wikipedia.org/wiki/File:Unix_history-simple.svg)) of the Unix history and it appears that both Linux and Apple OS X are based on the Unix OS.  

Since I am learning Ubuntu I have been able to run Unix commands that I am familiar with and they all work great. About a year ago before I installed my Ubuntu I ran the same type of commands on the Mac OS on my friend's Mac and they all worked.  According to the two replies I received, I now know that I can't run any Mac apps on Ubuntu.   So, if these operating systems are based on Unix why am I not able to run Mac software on Ubuntu?  I am just trying to find an answer.  Thanks for the replies. 

Sunrock

---

### Post by psusi on 2011-01-04
They are both unix like kernels, which is not at all the same as saying mac is a Linux distro.

Since they both implement the POSIX apis, any POSIX compliant app can be built and run on either system.  For the most part, this means that Linux apps can be built to run on Mac, but Mac apps that use the Mac gui apis can only run on Mac.  In either case, a program can not be run on one system if it was built for the other; it has to be rebuilt.

---

### Post by hawkmage on 2011-01-04
OS X uses a hybrid kernel (Darwin) based on the Mach and BSD kernels, it is not a linux kernel.  OS X programs are not binary compatable with Linux anymore than they are with Solaris or AIX.  As has been said the same applications can often be built on the the various systems but that is about all.  Most versions of Linux and Unix use some implimation of X for it GUI where as OS X uses Coca.

Just because two things came from a common origins doesn't make them compatible.   Both the Ford Fusion and the Ford F350 Truck both can tract their history back to the Model T Ford but they are not the same.

---

### Post by Sunrock on 2011-01-04
My questions have been answered.  Thanks!!!

---

