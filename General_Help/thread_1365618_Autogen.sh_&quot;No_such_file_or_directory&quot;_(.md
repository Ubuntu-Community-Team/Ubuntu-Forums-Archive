---
title: "Autogen.sh: &quot;No such file or directory&quot; (Mouse trap installation)"
date: 2009-12-27
forum: General Help
---

### Post by rva1945 on 2009-12-27
I'm trying to install the MouseTrap universal access. Reached this stage:

**Installation**

 Navigate to the directory where you cloned the repository and run the following command to begin installation: 
$ ./autogen.sh

But I get:

bash: ./autogen.sh: No such file or directory
[email]robert@rvasystem:~/mousetrap/.git[/email]$
I'm new to Linux so please, if you think you can help me, I'd appreciate your help.

---

### Post by Leppie on 2009-12-27
did you check if it's set to be executable?

you can set it to executable like this (while your in the directory where you put this script):
```
$sudo chmod +x autogen.sh
```

---

### Post by The Secret on 2009-12-27
```
ls -al ~/mousetrap/.git
```

What's the output ?

---

### Post by rva1945 on 2009-12-27
> **The Secret said:**
> ```
ls -al ~/mousetrap/.git
```What's the output ?

I verified that I have a mousetrapa folder in my home/robert folder, and there's an autogen.sh

this is the output you requested:

robert@rvasystem:~/mousetrap$ ls -al ~/mousetrap/.git
total 68
drwxr-xr-x 8 robert robert  4096 2009-12-27 15:07 .
drwxr-xr-x 8 robert robert  4096 2009-12-27 15:07 ..
drwxr-xr-x 2 robert robert  4096 2009-12-27 15:07 branches
-rw-r--r-- 1 robert robert   254 2009-12-27 15:07 config
-rw-r--r-- 1 robert robert    73 2009-12-27 15:07 description
-rw-r--r-- 1 robert robert    23 2009-12-27 15:07 HEAD
drwxr-xr-x 2 robert robert  4096 2009-12-27 15:07 hooks
-rw-r--r-- 1 robert robert 18688 2009-12-27 15:07 index
drwxr-xr-x 2 robert robert  4096 2009-12-27 15:07 info
drwxr-xr-x 3 robert robert  4096 2009-12-27 15:07 logs
drwxr-xr-x 4 robert robert  4096 2009-12-27 15:07 objects
-rw-r--r-- 1 robert robert   365 2009-12-27 15:07 packed-refs
drwxr-xr-x 5 robert robert  4096 2009-12-27 15:07 refs
robert@rvasystem:~/mousetrap$ 

I follow the installation guide from here:

[http://live.gnome.org/MouseTrap/Installation](http://live.gnome.org/MouseTrap/Installation)

but this
./autogen.sh

I can't make it work

I feel as in kindergarten trying to understand nuclear physics. But I'll not surrender without a fight.

---

### Post by rva1945 on 2009-12-27
I did it and it seeed to work, but the problem remains.

---

### Post by The Secret on 2009-12-27
Re-clone the repository - apparently autogen.sh is missing. Tried it and everything works as expected.

```
drwxr-xr-x 8 dainis dainis   4096 2009-12-27 20:54 .
drwxr-xr-x 8 dainis dainis   4096 2009-12-27 20:53 ..
-rwxr-xr-x 1 dainis dainis   4868 2009-12-27 20:54 acinclude.m4
-rwxr-xr-x 1 dainis dainis 343186 2009-12-27 20:54 aclocal.m4
-rwxr-xr-x 1 dainis dainis     65 2009-12-27 20:54 AUTHORS
[COLOR=Green]**-rwxr-xr-x 1 dainis dainis    560 2009-12-27 20:54 autogen.sh**[/COLOR]
-rw-r--r-- 1 dainis dainis    185 2009-12-27 20:54 ChangeLog
-rw-r--r-- 1 dainis dainis   2272 2009-12-27 20:54 configure.in
-rwxr-xr-x 1 dainis dainis  18023 2009-12-27 20:54 COPYING
drwxr-xr-x 8 dainis dainis   4096 2009-12-27 20:54 docs
drwxr-xr-x 8 dainis dainis   4096 2009-12-27 20:54 .git
-rw-r--r-- 1 dainis dainis    141 2009-12-27 20:54 .gitignore
-rwxr-xr-x 1 dainis dainis     67 2009-12-27 20:54 HACKING
drwxr-xr-x 2 dainis dainis   4096 2009-12-27 20:54 images
-rwxr-xr-x 1 dainis dainis   9512 2009-12-27 20:54 INSTALL
-rw-r--r-- 1 dainis dainis     67 2009-12-27 20:54 MAINTAINERS
-rwxr-xr-x 1 dainis dainis   1389 2009-12-27 20:54 Makefile.am
-rwxr-xr-x 1 dainis dainis    209 2009-12-27 20:54 mousetrap.desktop.in
-rw-r--r-- 1 dainis dainis    788 2009-12-27 20:54 mousetrap.doap
-rwxr-xr-x 1 dainis dainis      0 2009-12-27 20:54 NEWS
drwxr-xr-x 3 dainis dainis   4096 2009-12-27 20:54 po
-rw-r--r-- 1 dainis dainis    363 2009-12-27 20:54 .project
-rw-r--r-- 1 dainis dainis    421 2009-12-27 20:54 .pydevproject
-rwxr-xr-x 1 dainis dainis  10233 2009-12-27 20:54 pylintrc
-rw-r--r-- 1 dainis dainis     68 2009-12-27 20:54 README
-rwxr-xr-x 1 dainis dainis   1111 2009-12-27 20:54 run_pylint.sh.in
drwxr-xr-x 2 dainis dainis   4096 2009-12-27 20:54 samples
drwxr-xr-x 3 dainis dainis   4096 2009-12-27 20:54 src
```

---

### Post by rva1945 on 2009-12-27
> **The Secret said:**
> Re-clone the repository - apparently autogen.sh is missing. Tried it and everything works as expected.

```
drwxr-xr-x 8 dainis dainis   4096 2009-12-27 20:54 .
drwxr-xr-x 8 dainis dainis   4096 2009-12-27 20:53 ..
-rwxr-xr-x 1 dainis dainis   4868 2009-12-27 20:54 acinclude.m4
-rwxr-xr-x 1 dainis dainis 343186 2009-12-27 20:54 aclocal.m4
-rwxr-xr-x 1 dainis dainis     65 2009-12-27 20:54 AUTHORS
[COLOR=Green]**-rwxr-xr-x 1 dainis dainis    560 2009-12-27 20:54 autogen.sh**[/COLOR]
-rw-r--r-- 1 dainis dainis    185 2009-12-27 20:54 ChangeLog
-rw-r--r-- 1 dainis dainis   2272 2009-12-27 20:54 configure.in
-rwxr-xr-x 1 dainis dainis  18023 2009-12-27 20:54 COPYING
drwxr-xr-x 8 dainis dainis   4096 2009-12-27 20:54 docs
drwxr-xr-x 8 dainis dainis   4096 2009-12-27 20:54 .git
-rw-r--r-- 1 dainis dainis    141 2009-12-27 20:54 .gitignore
-rwxr-xr-x 1 dainis dainis     67 2009-12-27 20:54 HACKING
drwxr-xr-x 2 dainis dainis   4096 2009-12-27 20:54 images
-rwxr-xr-x 1 dainis dainis   9512 2009-12-27 20:54 INSTALL
-rw-r--r-- 1 dainis dainis     67 2009-12-27 20:54 MAINTAINERS
-rwxr-xr-x 1 dainis dainis   1389 2009-12-27 20:54 Makefile.am
-rwxr-xr-x 1 dainis dainis    209 2009-12-27 20:54 mousetrap.desktop.in
-rw-r--r-- 1 dainis dainis    788 2009-12-27 20:54 mousetrap.doap
-rwxr-xr-x 1 dainis dainis      0 2009-12-27 20:54 NEWS
drwxr-xr-x 3 dainis dainis   4096 2009-12-27 20:54 po
-rw-r--r-- 1 dainis dainis    363 2009-12-27 20:54 .project
-rw-r--r-- 1 dainis dainis    421 2009-12-27 20:54 .pydevproject
-rwxr-xr-x 1 dainis dainis  10233 2009-12-27 20:54 pylintrc
-rw-r--r-- 1 dainis dainis     68 2009-12-27 20:54 README
-rwxr-xr-x 1 dainis dainis   1111 2009-12-27 20:54 run_pylint.sh.in
drwxr-xr-x 2 dainis dainis   4096 2009-12-27 20:54 samples
drwxr-xr-x 3 dainis dainis   4096 2009-12-27 20:54 src
```

Now things get worse (I started from the beginning)

robert@rvasystem:/$ sudo apt-get install git-core
[sudo] password for robert: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git-core is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
robert@rvasystem:/$ git clone git://git.gnome.org/mousetrap
**fatal: could not create work tree dir 'mousetrap': Permission denied.**
robert@rvasystem:/$ 

Maybe the folder already exists?
When the installation guide tells me to

Navigate to the directory where you cloned the repository and run the following command to begin installation: 
$ ./autogen.shwhat is the directory where I cloned the repository?

---

### Post by The Secret on 2009-12-27
You were in the root directory - of course it didn't allowed you to create a new directory there.

```
cd $HOME && git clone git://git.gnome.org/mousetrap && cd mousetrap && ./autogen.sh
```

This line should clone the repository, cd to the right directory and launch autogen.sh.

---

### Post by rva1945 on 2009-12-27
> **The Secret said:**
> You were in the root directory - of course it didn't allowed you to create a new directory there.

```
cd $HOME && git clone git://git.gnome.org/mousetrap && cd mousetrap && ./autogen.sh
```This line should clone the repository, cd to the right directory and launch autogen.sh.

It worked, then, following the Mousetrap installation guidelines:

If you run into errors, see the section entitled “Troubleshooting.” Next you need to compile the source code. To do this, run the following command: 
$ makeOnce this completes, you will need to install Mousetrap with the following command: 
$ sudo make install
It is possible to modify the installation path using *--prefix=/non/standard/path*. After installing, you can run the program by typing: 
$ mousetrap

In fact I run into errors and did what the guidelines intruct to do. This is the terminal lines:

robert@rvasystem:~$ cd mousetrap
robert@rvasystem:~/mousetrap$ ./autogen.sh
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.64
checking for automake >= 1.9...
  testing automake-1.11... found 1.11
checking for libtool >= 1.5...
  testing libtoolize... found 2.2.6
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... not found.
***Error***: You must have glib-gettext >= 2.2.0 installed
  to build mouseTrap.  Download the appropriate package for
  from your distribution or get the source tarball at
    [ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz](ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz)

robert@rvasystem:~/mousetrap$ sudo apt-get install libglib2.0-dev
[sudo] password for robert: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
robert@rvasystem:~/mousetrap$ sudo apt-get install libglib2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  libglib2.0-doc
The following NEW packages will be installed:
  libglib2.0-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,043kB of archives.
After this operation, 4,284kB of additional disk space will be used.
Get:1 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) karmic-updates/main libglib2.0-dev 2.22.3-0ubuntu1 [1,043kB]
Fetched 1,043kB in 43s (23.7kB/s)                                                                                                           
Selecting previously deselected package libglib2.0-dev.
(Reading database ... 137374 files and directories currently installed.)
Unpacking libglib2.0-dev (from .../libglib2.0-dev_2.22.3-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up libglib2.0-dev (2.22.3-0ubuntu1) ...
[B]robert@rvasystem:~/mousetrap$ make
make: *** No targets specified and no makefile found.  Stop.
robert@rvasystem:~/mousetrap$ 
[/B]
Do I have to clone the repository and all again? I didn't try it thinking of duplicating or ruining all the installation.

---

### Post by rva1945 on 2009-12-27
> **The Secret said:**
> You were in the root directory - of course it didn't allowed you to create a new directory there.

```
cd $HOME && git clone git://git.gnome.org/mousetrap && cd mousetrap && ./autogen.sh
```This line should clone the repository, cd to the right directory and launch autogen.sh.

THanks man, I could make it work.

Now my problem is, the USB webcam, is not working in Ubuntu, although detected:

robert@rvasystem:~/mousetrap$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 002: ID 093a:2624 Pixart Imaging, Inc. WebCam**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
robert@rvasystem:~/mousetrap$

---

