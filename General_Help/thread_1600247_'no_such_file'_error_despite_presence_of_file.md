---
title: "'no such file' error despite presence of file"
date: 2010-10-18
forum: General Help
---

### Post by shadowofgrael on 2010-10-18
I just installed a program and do not know what is causing this error.
When I run it from the applications menu I get the following error "Could not launch 'FirstClass Client' :Failed to execute child process "/opt/firstclass/fcc" (No such file or directory)". I opened up a terminal and looked at the location. The file is there.
I do not know much at all in this area but do not understand why this error is occurring. Any help would be nice.

Terminal output: <will@will-Latitude-E6400:/opt/firstclass$ ls -al
total 15128
drwxr-xr-x 10 root root    4096 2009-11-18 13:22 .
drwxr-xr-x  3 root root    4096 2010-10-18 17:51 ..
drwxr-xr-x  3 root root    4096 2009-08-06 01:15 download
-rw-r--r--  1 root root     867 2009-11-18 12:29 fcapps
-rwxr-xr-x  1 root root 7521991 2009-11-18 13:22 fcc
-rwxr-xr-x  1 root root 5315334 2009-11-18 13:22 fccicons.rez
-rw-r--r--  1 root root 2587680 2009-11-18 13:22 fcc.rez
drwxr-xr-x  3 root root    4096 2009-08-06 01:15 fcctemp
-rw-r--r--  1 root root     141 2009-11-18 12:29 fcfonts
drwxr-xr-x  3 root root    4096 2009-11-18 13:22 fcp
-rw-r--r--  1 root root   10281 2009-11-18 12:29 firstclass.png
drwxr-xr-x  3 root root    4096 2009-08-06 01:15 Images
drwxr-xr-x  3 root root    4096 2009-08-06 01:15 plugins
drwxr-xr-x  3 root root    4096 2009-11-18 13:22 settings
drwxr-xr-x  6 root root    4096 2009-11-18 13:22 .svn
drwxr-xr-x  3 root root    4096 2009-11-18 13:22 tools>

---

### Post by Rubi1200 on 2010-10-19
Hi,
try running the program in the terminal and post the errors.

Also, is it possible this program requires root privileges to run?

Try prefacing the command with sudo.

---

### Post by dcstar on 2010-10-20
> **shadowofgrael said:**
> I just installed a program and do not know what is causing this error.
When I run it from the applications menu I get the following error "Could not launch 'FirstClass Client' :Failed to execute child process "/opt/firstclass/fcc" (No such file or directory)". I opened up a terminal and looked at the location. The file is there.
I do not know much at all in this area but do not understand why this error is occurring. Any help would be nice.
.........

Let me guess, you have a 64-bit system and you are trying to install a 32-bit app?

---

### Post by shadowofgrael on 2010-10-26
I know its been a while since I gave up on this project but after installing the 32libs I am still getting install errors from the .deb. The program is also available in a "generic" form tar.bz which installed, though cannot be launched succesfully
The error: <
will@will-Latitude-E6400:~$ sudo dpkg -i /home/will/Downloads/fcc-10.009-Linux.i686.deb
dpkg: error processing /home/will/Downloads/fcc-10.009-Linux.i686.deb (--install):
 unable to open file '/var/lib/dpkg/tmp.ci//.svn': Is a directory
Errors were encountered while processing:
 /home/will/Downloads/fcc-10.009-Linux.i686.deb
>
while this may be program specific I would like to know if I'm missing something within my control. I have already tried --force-architecture and received the same output.

---

### Post by dcstar on 2010-10-27
> **shadowofgrael said:**
> I know its been a while since I gave up on this project but after installing the 32libs I am still getting install errors from the .deb. The program is also available in a "generic" form tar.bz which installed, though cannot be launched succesfully
.........
while this may be program specific I would like to know if I'm missing something within my control. I have already tried --force-architecture and received the same output.

No matter what libraries you load, if code is compiled for the wrong architecture then it will **not** run.

Compile it from source on your own system.

---

