---
title: "update-manager kernel header issue"
date: 2012-07-05
forum: General Help
---

### Post by homeriq5 on 2012-07-05
Dear all, 

I am currently having problems with my Atheros 9300 wireless adaptor in connecting to secured networks.  I am attempting to install compat-wireless however it appears that a bigger issue seems to be impeding my progress.  

When I try to install the downloaded package following [http://linuxwireless.org/en/users/Download/](http://linuxwireless.org/en/users/Download/) , I get the following message:

```

homeriq5@cr-48-ubuntu:~/compat-wireless-2012-05-10$ make
make -C /lib/modules/3.4.0/build M=/home/user/compat-wireless-2012-05-10 modules
make: *** /lib/modules/3.4.0/build: No such file or directory.  Stop.
make: *** [modules] Error 2

```

I also check to see that I am running kernel version 3.4.0 and have the latest linux headers installed.  

```

homeriq5@cr-48-ubuntu:~$ uname -r
3.4.0

```

However, when I try to install the latest linux headers it only downloads those for kernel 3.2!  Update-manager recently had a new kernel in its list of updates, so I had installed that recently.

```

homeriq5@cr-48-ubuntu:~$ sudo apt-get install linux-headers-generic
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-headers-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2,610 B of archives.
After this operation, 31.7 kB of additional disk space will be used.
Selecting previously unselected package linux-headers-generic.
(Reading database ... 354973 files and directories currently installed.)
Unpacking linux-headers-generic (from .../linux-headers-generic_3.2.0.26.28_i386.deb) ...
Setting up linux-headers-generic (3.2.0.26.28)

```

This could explain why the make command is not working since the header version does not match the kernel version, but I am confused as to why it would let me install 3.4.0 for the kernel but not for the headers.  I really need to fix this so I can get my wireless working properly on campus, any help would be very much appreciated.  Thanks!

---

### Post by Redblade20XX on 2012-07-05
How did you install the 3.4 kernel? From just glancing at the repositories there are only the 3.2 versions so trying to install headers from the repositories will only install the 3.2 versions.

Did you check the location the error threw, to see if there is such a directory?

- Red

---

### Post by homeriq5 on 2012-07-05
Oftentimes I see kernel updates only in update-manager but these updates are "kept back" when I try to update through the command line using "sudo apt-get upgrade".  This time I elected to update through update-manager, and it installed some a new kernel.  Is it possible that I may have a respository enabled that allowed this?

The location does exist, however in the /usr/src/ folder I dont see anything corresponding to 3.4.0 in terms of headers.  This is pretty strange:

```

homeriq5@cr-48-ubuntu:~$ sudo ls /lib/modules/3.4.0/build 
/lib/modules/3.4.0/build
homeriq5@cr-48-ubuntu:~$ sudo ls /usr/src
linux-headers-3.2.0-23		       linux-headers-3.2.0-24-virtual
linux-headers-3.2.0-23-generic	       linux-headers-3.2.0-25
linux-headers-3.2.0-23-generic-pae     linux-headers-3.2.0-25-generic
linux-headers-3.2.0-23-lowlatency      linux-headers-3.2.0-25-generic-pae
linux-headers-3.2.0-23-lowlatency-pae  linux-headers-3.2.0-25-virtual
linux-headers-3.2.0-23-virtual	       linux-headers-3.2.0-26
linux-headers-3.2.0-24		       linux-headers-3.2.0-26-generic
linux-headers-3.2.0-24-generic	       linux-headers-3.2.0-26-generic-pae
linux-headers-3.2.0-24-generic-pae     linux-headers-3.2.0-26-virtual

```

---

### Post by stderr on 2012-07-05
To help clear up where this kernel's from from, can you post the output of the following:

```
cat /etc/apt/sources.lst
```
```
sudo dpkg -l linux-image-*
```
```
ls -l /boot/
```

---

### Post by homeriq5 on 2012-07-05
Here is the output of sudo dpkg -l linux-image-*
```

homeriq5@cr-48-ubuntu:~$ sudo dpkg -l linux-image-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                            Version                         Description
+++-===============================-===============================-==============================================================================
un  linux-image-2.6                 <none>                          (no description available)
un  linux-image-2.6.38-8-generic    <none>                          (no description available)
un  linux-image-3.0                 <none>                          (no description available)
un  linux-image-3.0.0-21-generic    <none>                          (no description available)
un  linux-image-3.2.0-25-generic    <none>                          (no description available)
un  linux-image-3.2.0-26-generic    <none>                          (no description available)
un  linux-image-generic             <none>                          (no description available)

```

This is the output from ls -l /boot/, however I should mention that the grub bootloader isn't used on my laptop as its a hacked google chromebook (boots straight into ubuntu after running a particular command in chromeOS's shell [http://chromeos-cr48.blogspot.com/2011/04/ubuntu-1104-for-cr-48-is-ready.html):](http://chromeos-cr48.blogspot.com/2011/04/ubuntu-1104-for-cr-48-is-ready.html):)
```

homeriq5@cr-48-ubuntu:~$ ls -l /boot/
total 364
drwxr-xr-x 3 root root  12288 Jul  5 13:49 grub
-rw-r--r-- 1 root root 176764 Nov 27  2011 memtest86+.bin
-rw-r--r-- 1 root root 178944 Nov 27  2011 memtest86+_multiboot.bin

```

Here's the output of cat /etc/apt/sources.list:
```

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://linux.dropbox.com/ubuntu precise main
deb-src http://linux.dropbox.com/ubuntu precise main

```

Thanks again!

---

### Post by stderr on 2012-07-06
This is Ubuntu on top of Chrome OS? Interesting.

You haven't got any Linux kernels installed via your repositories. This means you either built 3.4 yourself, or there's an additional update mechanism from the ChrUbuntu guys, or Ubuntu is piggybacking off of the Chrome OS kernel.

Seen as it sounds like you didn't compile the kernel (you'd know if you did :)), and I doubt there's a funky oddball kernel update mechanism built into ChrUbuntu, I guess it must be the latter. Which is interesting in itself, as I think the Chrome OS team modify the base kernel in their own way.

If this is true, then you're going to have to build these drivers against 3.4, and rebuild each time you upgrade the kernel on Chrome OS. To do this you'll need the sources for 3.4. 

If they're available on your Chrome OS partition, it would be wise to use those. If not, you'll have to either a) download the base 3.4.0 sources from [kernel.org]("http://kernel.org"), build against those, and hope that it works; or, preferably, b) [download]("http://getchrome.eu/download") the version of chrome OS which you have currently, copy off the kernel headers/sources, and build against those.

---

