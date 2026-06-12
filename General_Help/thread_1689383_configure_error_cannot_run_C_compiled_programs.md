---
title: "configure: error: cannot run C compiled programs"
date: 2011-02-16
forum: General Help
---

### Post by Dimesh on 2011-02-16
when trying to install program by compiling it that what i got:

```
sudo sh configure

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... configure: error: in `/media/pro-gam/2-my-download/cairo-dock-2.1.0':
configure: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.
```

i see in my ubuntu installed software that there is a g++ installed in my pc.

??!!

---

### Post by asmoore82 on 2011-02-16
You should never `configure` or `make` with `sudo`,
only `make install` may require admin privilege - and not even then
if you are installing to your own personal software collection.

Make sure you have the "build-essential" package installed.

And, again, the conventional build looks like:
```
./configure
make
sudo make install
```

---

### Post by Dimesh on 2011-02-16
Thanks to you MR.asmoore82

> **asmoore82 said:**
> You should never `configure` or `make` with `sudo`

i do but:
```
./configure
bash: ./configure: Permission denied
```

> **asmoore82 said:**
> 
Make sure you have the "build-essential" package installed.


```
sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by asmoore82 on 2011-02-16
> **Dimesh said:**
> ```
./configure
bash: ./configure: Permission denied
```

Excellent! It's really important not to mask other errors…

Now I'm thinking that either the source code was extracted as `root` or
is stored on a non-Linux filesystem. Neither of these is ideal.

---

### Post by Dimesh on 2011-02-16
> **asmoore82 said:**
> 
Now I'm thinking that either the source code was extracted as `root` or
is stored on a non-Linux filesystem. Neither of these is ideal.

Sorry i do not understand Mr.

---

### Post by psusi on 2011-02-16
> **Dimesh said:**
> Sorry i do not understand Mr.

You extracted the tar file with sudo.  Don't do that.

---

### Post by Dimesh on 2011-02-16
but i did right click and choose extract here
i do not extract with terminal
!

---

### Post by hawkmage on 2011-02-16
I do this all the time.  

I have created a build directory under my home:
```
mkdir ~/build
```Change into the directory:
```
cd ~/build
```Assume I downloaded openssl-1.0.0d.tar.gz and it was saved in my Downloads directory I would extract it to the build directory that you are currently in:
```
tar zxf ~/Downloads/openssl-1.0.0d.tar.gz
```When you get your command prompt back you will have a directory for the openssl code.  CD in to that directory:
```
cd ~/build/openssl-1.0.0d
```Run the configure script:
```
./config
```Make the application:
```
make
```Install the application (If you want):
```
sudo make install
```

---

### Post by psusi on 2011-02-16
> **Dimesh said:**
> but i did right click and choose extract here
i do not extract with terminal
!

Did you run nautilus with gksu or something?  What does ls -l configure show?

---

### Post by Dimesh on 2011-02-17
that is :

```
ahmed@ahmed-Lenovo-G460:~$ cd /media/pro-gam/2-my-download/cairo-dock-2.1.0
ahmed@ahmed-Lenovo-G460:/media/pro-gam/2-my-download/cairo-dock-2.1.0$ sudo ./configure
[sudo] password for ahmed: 
sudo: ./configure: command not found
ahmed@ahmed-Lenovo-G460:/media/pro-gam/2-my-download/cairo-dock-2.1.0$ ./configure
bash: ./configure: Permission denied
ahmed@ahmed-Lenovo-G460:/media/pro-gam/2-my-download/cairo-dock-2.1.0$ sudo sh configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... configure: error: in `/media/pro-gam/2-my-download/cairo-dock-2.1.0':
configure: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.
ahmed@ahmed-Lenovo-G460:/media/pro-gam/2-my-download/cairo-dock-2.1.0$ ls -l
total 1462
-rw------- 1 ahmed ahmed 342469 2009-09-29 15:13 aclocal.m4
-rw------- 1 ahmed ahmed  12172 2009-09-27 18:09 cairo-dock-package-theme
-rw------- 1 ahmed ahmed    525 2009-09-27 18:09 cairo-dock.pc.in
-rw------- 1 ahmed ahmed   3707 2009-06-30 11:21 compile
-rw------- 1 ahmed ahmed  44892 2008-11-05 03:01 config.guess
-rw------- 1 ahmed ahmed   2311 2009-09-29 15:13 config.h.in
-rw------- 1 ahmed ahmed   8623 2011-02-17 17:22 config.log
-rw------- 1 ahmed ahmed  33387 2008-11-05 03:01 config.sub
-rw------- 1 ahmed ahmed 511428 2009-09-29 15:13 configure
-rw------- 1 ahmed ahmed   4474 2009-09-28 10:55 configure.ac
-rw------- 1 ahmed ahmed   3696 2009-09-27 18:09 copyright
drwx------ 1 ahmed ahmed   8192 2009-09-30 10:23 data
-rw------- 1 ahmed ahmed  15936 2009-06-30 11:21 depcomp
-rw------- 1 ahmed ahmed   1138 2009-09-27 18:09 INSTALL
-rw------- 1 ahmed ahmed   9233 2009-06-30 11:21 install-sh
-rw------- 1 ahmed ahmed  22493 2009-09-27 18:09 intltool-extract.in
-rw------- 1 ahmed ahmed  35219 2009-09-27 18:09 intltool-merge.in
-rw------- 1 ahmed ahmed  28061 2009-09-27 18:09 intltool-update.in
-rw------- 1 ahmed ahmed    158 2009-09-27 18:09 launch-cairo-dock-after-compiz
-rw------- 1 ahmed ahmed  25284 2009-09-27 18:09 LGPL-2
-rw------- 1 ahmed ahmed  35147 2009-09-27 18:09 LICENSE
-rw------- 1 ahmed ahmed 243454 2009-01-16 12:58 ltmain.sh
-rw------- 1 ahmed ahmed    346 2009-09-27 18:09 Makefile.am
-rw------- 1 ahmed ahmed  23691 2009-09-29 15:13 Makefile.in
-rw------- 1 ahmed ahmed  11014 2009-06-30 11:21 missing
drwx------ 1 ahmed ahmed   4096 2009-09-30 10:22 po
drwx------ 1 ahmed ahmed  28672 2009-09-30 10:22 src
```

chmod command does not work 

```
ahmed@ahmed-Lenovo-G460:/media/pro-gam/2-my-download/cairo-dock-2.1.0$ chmod a+x configure
ahmed@ahmed-Lenovo-G460:/media/pro-gam/2-my-download/cairo-dock-2.1.0$ ll
total 1514
drwx------ 1 ahmed ahmed   4096 2011-02-17 17:22 ./
drwx------ 1 ahmed ahmed  49152 2011-02-17 03:40 ../
-rw------- 1 ahmed ahmed 342469 2009-09-29 15:13 aclocal.m4
-rw------- 1 ahmed ahmed  12172 2009-09-27 18:09 cairo-dock-package-theme
-rw------- 1 ahmed ahmed    525 2009-09-27 18:09 cairo-dock.pc.in
-rw------- 1 ahmed ahmed   3707 2009-06-30 11:21 compile
-rw------- 1 ahmed ahmed  44892 2008-11-05 03:01 config.guess
-rw------- 1 ahmed ahmed   2311 2009-09-29 15:13 config.h.in
-rw------- 1 ahmed ahmed   8623 2011-02-17 17:22 config.log
-rw------- 1 ahmed ahmed  33387 2008-11-05 03:01 config.sub
-rw------- 1 ahmed ahmed 511428 2009-09-29 15:13 configure
-rw------- 1 ahmed ahmed   4474 2009-09-28 10:55 configure.ac
-rw------- 1 ahmed ahmed   3696 2009-09-27 18:09 copyright
drwx------ 1 ahmed ahmed   8192 2009-09-30 10:23 data/
-rw------- 1 ahmed ahmed  15936 2009-06-30 11:21 depcomp
-rw------- 1 ahmed ahmed   1138 2009-09-27 18:09 INSTALL
-rw------- 1 ahmed ahmed   9233 2009-06-30 11:21 install-sh
-rw------- 1 ahmed ahmed  22493 2009-09-27 18:09 intltool-extract.in
-rw------- 1 ahmed ahmed  35219 2009-09-27 18:09 intltool-merge.in
-rw------- 1 ahmed ahmed  28061 2009-09-27 18:09 intltool-update.in
-rw------- 1 ahmed ahmed    158 2009-09-27 18:09 launch-cairo-dock-after-compiz
-rw------- 1 ahmed ahmed  25284 2009-09-27 18:09 LGPL-2
-rw------- 1 ahmed ahmed  35147 2009-09-27 18:09 LICENSE
-rw------- 1 ahmed ahmed 243454 2009-01-16 12:58 ltmain.sh
-rw------- 1 ahmed ahmed    346 2009-09-27 18:09 Makefile.am
-rw------- 1 ahmed ahmed  23691 2009-09-29 15:13 Makefile.in
-rw------- 1 ahmed ahmed  11014 2009-06-30 11:21 missing
drwx------ 1 ahmed ahmed   4096 2009-09-30 10:22 po/
drwx------ 1 ahmed ahmed  28672 2009-09-30 10:22 src/
```

---

### Post by psusi on 2011-02-17
Then the directory you are in is on an NTFS disk, which does not support permissions.

---

### Post by Dimesh on 2011-02-17
thanks to allah, i solved it,
the problem that my files does not have the permissions to be executed and i tried to use chmod command but does not work.
now i found this page that makes NTFS partitions have the read and write permissions

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

---

### Post by psusi on 2011-02-17
> **Dimesh said:**
> thanks to allah, i solved it,
the problem that my files does not have the permissions to be executed and i tried to use chmod command but does not work.
now i found this page that makes NTFS partitions have the read and write permissions

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

That has nothing to do with anything.  That is for the version of Ubuntu from 2007.  Write support is already enabled, which is why you were able to extract the files there in the first place.  As we have been trying to tell you, NTFS does not support file permissions, so you can not build software there.

---

### Post by Dimesh on 2011-02-17
Sorry but i do and all of my programs are built

---

### Post by psusi on 2011-02-17
> **Dimesh said:**
> Sorry but i do and all of my programs are built

You do what?  Since chmod does't work, you can't flag the file as executable.

---

### Post by Dimesh on 2011-02-19
Yes Mr.psusi, you are right.
after applying what in the page i mention, i found that the owner of all files in the partitions is root , not ahmed .
and still chmod command does not work, anyway i can now execute any thing, i will learn tomorrow how to solve this problem, may be trying another partition format.

Thanks

---

### Post by moijdikssekool on 2011-08-24
> 
Now I'm thinking that either the source code was extracted as `root` or
is stored on a non-Linux filesystem
great, i extract the file to my home and it works fine
++1:guitar:

---

### Post by MasterCATZ on 2012-07-14
You may not be able to set an NTFS file permissions but you can set the ENTIRE NTFS drive to be exec with 
fmask=0022 
ie)


sudo mkdir (where ever you will mount it)  sudo mount -t ntfs -o fmask=0022,dmask=0000,uid=1000,gid=1000     /dev/(what ever drive is) /(where ever you mounted it)



the thumbdrive I was using for xbmc ran out of space so used one of my NTFS thumbdrives for building new version

---

### Post by wildmanne39 on 2012-07-14
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

