---
title: "G++ Codeblocks Error"
date: 2012-07-08
forum: General Help
---

### Post by vokevybez on 2012-07-08
Trying to compile a java file using codeblocks. Says I need G++, after i install try to compile again it outputs ```
Compiling: /home/vokevybez/Desktop/FindCost.java
g++: error trying to exec 'ecj1': execvp: No such file or directory
Process terminated with status 1 (0 minutes, 0 seconds)
0 errors, 0 warnings

``` What am I doing wrong?

---

### Post by Crafty Kisses on 2012-07-08
I take it you have build-essential installed? If not try

```
apt-get build-essential
``` The files that make gcc usable are in glibc-devel, glibc-headers, kernel-headers. You might also want to read the [ORACLE]("http://www.oracle.com/technetwork/products/clustering/overview/index.html?origref=http://www.linuxquestions.org/questions/linux-software-2/gcc-error-trying-to-exec-as-execvp-no-such-file-or-directory-906750/") documentation.

---

