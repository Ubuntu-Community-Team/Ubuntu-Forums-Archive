---
title: "How to build gcc/g++ compilers in ubuntu8.04"
date: 2012-06-21
forum: General Help
---

### Post by kingkong22 on 2012-06-21
I downloaded the source package of gnu-gcc4.7.1 and want to install the gcc/g++ compilers in my ubuntu8.0.4. if I type ./configure; make; from a terminal, it will compile all of compilers, such as java,fortran,...compilers. However, I am only interested in gcc/g++ compilers only. How can I do that for it ?

one more question: I don't want to install the new one compiler to overwrite the current one, how can I do it so that I can switch the compiler between the new one and the current one ? Thank you very much !!!

---

### Post by d.atanasov on 2012-06-21
Hi, 

This is only idea but you can search for the  .deb files of gcc/g++ and then use the dpkg command. What do you think ?

---

### Post by kingkong22 on 2012-06-21
my souce file ended with *.tar.bz2 . how can I use dpkg commands ? Thanks !

---

### Post by 3Miro on 2012-06-21
> **kingkong22 said:**
> my souce file ended with *.tar.bz2 . how can I use dpkg commands ? Thanks !

This a tarball, i.e. a bunch of archived files like .zip. You need to extract the files and then run commands like ./configure and make. There is usually a README or INSTALL file with instructions.

Are you really using 8.04, the desktop version lost support over a year ago. If you install the latest Ubuntu 12.04 you will get gcc 4.7 in the software center.

---

### Post by kingkong22 on 2012-06-21
> **3Miro said:**
> This a tarball, i.e. a bunch of archived files like .zip. You need to extract the files and then run commands like ./configure and make. There is usually a README or INSTALL file with instructions.

Are you really using 8.04, the desktop version lost support over a year ago. If you install the latest Ubuntu 12.04 you will get gcc 4.7 in the software center.
 
Yes! I have used Dell-8.04 desktop version. I don't know how I can upgrade it. thus I just want to install gcc/g++-v4.7 version, not all compilers of other languages. Thanks a lot !

---

