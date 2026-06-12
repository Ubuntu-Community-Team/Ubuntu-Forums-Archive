---
title: "install from tarball"
date: 2011-08-31
forum: General Help
---

### Post by Phil Binner on 2011-08-31
Hi

I think I'd be called an Ubuntu improver, but I still have a long way to go.  This mainly seems to be because Ubuntu is coming to meet me half way; i.e. most things can be done in the GUI now, rather than having to mess about in a terminal.

I am stuck with some of the software I want only being available in tarballs, however. I have read other threads involving this, and none of the solutions suggested seem to work for me. I suspect that, as usual, it's a conceptual fault, and as soon as I know the right way what I'm doing will probably seem ridiculous.

Currently I'm trying to install TrueCrypt, which requires me to test a signiture so I'm trying to install PGPcmdln first. If I solve one I guess I'll solve them all.  I have downloaded tarballs for both applications, and unpacked PGPcmdln into a directory of it's own. I then open a terminal into that directory and try to install. I have tried both methods below, with the same result:

bigbin@Middlebin-Ubuntu:~/PGPcmdln$ ./configure
bash: ./configure: No such file or directory

and

bigbin@Middlebin-Ubuntu:~/PGPcmdln$ ./configure PGPcmdln_6.5.8.Lnx_FW.tar.gz
bash: ./configure: No such file or directory

I presume there should be something else on the command line, but that seems to be as it's shown on the guides. Can anybody help please.

Phil B

---

### Post by nothingspecial on 2011-08-31
Well you can't configure a tarball.

What are the contents of the PGPcmdln directory?

Is there are README file?

---

### Post by 3xp10r3r|X13 on 2011-08-31
> 

bigbin@Middlebin-Ubuntu:~/PGPcmdln$ ./configure
bash: ./configure: No such file or directory
it simply means, that there is no "configure" file to execute. Just have a look in the folder, there should be some executable called "install" or something similar.

(as you suggested)

so why don't you try:
```

# ./install

```
while you're located in the directory

tell me if it works :)

---

### Post by Phil Binner on 2011-08-31
Files in the directory are:

PGPcmdln_6.5.8.Lnx_FW.tar.gz
PGPcmdln_6.5.8_Lnx_FW.tar.gz (not sure why that's there twice)
PGPcmdln_6.5.8_Lnx_FW.tar.gz.sig
WhatsNew.htm
WhatsNew.txt

I looked in the whatsNew.htm and was given the instruction "rpm -iv PGPcmdfw_x.x.x_linux.i386.rpm"

Following is the result:

bigbin@Middlebin-Ubuntu:~$ cd PGPcmdln
bigbin@Middlebin-Ubuntu:~/PGPcmdln$ rpm -iv PGPcmdfw_6.5.8_linux.i386.rpm
The program 'rpm' is currently not installed.  You can install it by typing:
sudo apt-get install rpm
bigbin@Middlebin-Ubuntu:~/PGPcmdln$ sudo apt-get install rpm
[sudo] password for bigbin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  librpm1 librpmbuild1 librpmio1 rpm-common rpm2cpio
Suggested packages:
  alien elfutils rpm-i18n
The following NEW packages will be installed
  librpm1 librpmbuild1 librpmio1 rpm rpm-common rpm2cpio
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 494 kB of archives.
After this operation, 1,720 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/main librpmio1 i386 4.8.1-6ubuntu1 [75.7 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/main rpm-common i386 4.8.1-6ubuntu1 [21.1 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/main librpm1 i386 4.8.1-6ubuntu1 [180 kB]
Get:4 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/main librpmbuild1 i386 4.8.1-6ubuntu1 [66.6 kB]
Get:5 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/main rpm2cpio i386 4.8.1-6ubuntu1 [6,216 B]
Get:6 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/main rpm i386 4.8.1-6ubuntu1 [145 kB]
Fetched 494 kB in 1s (460 kB/s)
Selecting previously deselected package librpmio1.
(Reading database ... 192640 files and directories currently installed.)
Unpacking librpmio1 (from .../librpmio1_4.8.1-6ubuntu1_i386.deb) ...
Selecting previously deselected package rpm-common.
Unpacking rpm-common (from .../rpm-common_4.8.1-6ubuntu1_i386.deb) ...
Selecting previously deselected package librpm1.
Unpacking librpm1 (from .../librpm1_4.8.1-6ubuntu1_i386.deb) ...
Selecting previously deselected package librpmbuild1.
Unpacking librpmbuild1 (from .../librpmbuild1_4.8.1-6ubuntu1_i386.deb) ...
Selecting previously deselected package rpm2cpio.
Unpacking rpm2cpio (from .../rpm2cpio_4.8.1-6ubuntu1_i386.deb) ...
Selecting previously deselected package rpm.
Unpacking rpm (from .../rpm_4.8.1-6ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up librpmio1 (4.8.1-6ubuntu1) ...
Setting up rpm-common (4.8.1-6ubuntu1) ...
Setting up librpm1 (4.8.1-6ubuntu1) ...
Setting up librpmbuild1 (4.8.1-6ubuntu1) ...
Setting up rpm2cpio (4.8.1-6ubuntu1) ...
Setting up rpm (4.8.1-6ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
bigbin@Middlebin-Ubuntu:~/PGPcmdln$ rpm -iv PGPcmdfw_6.5.8_linux.i386.rpm
rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
error: open of PGPcmdfw_6.5.8_linux.i386.rpm failed: No such file or directory
bigbin@Middlebin-Ubuntu:~/PGPcmdln$ 

So that's how I've got on.  Nil desporandum, however. I am bound to come out of this knowing something new.

Thanks again. I'll be watching.

---

### Post by nothingspecial on 2011-08-31
[COLOR="Blue"][SIZE="3"]Thank You[/SIZE][/COLOR]

You've just found where I got the quote in my sig from. :KS I remember reading it somewhere but have never remembered where.

Anyway, you are trying to install a package built for a redhat/fedora based system rather than a debian one. Look to see if you can find a package with a .deb extension. If not, do like the warning suggests and install alien.

---

### Post by Phil Binner on 2011-08-31
Thanks for that, but could you please give me the line to install alien. 

Another thing, one of the previous posts said why not try:

# ./install

I assume the "#2 is redundant - or is it.

---

### Post by nothingspecial on 2011-08-31
I'd try and find a deb file first.

sudo apt-get install alien

---

