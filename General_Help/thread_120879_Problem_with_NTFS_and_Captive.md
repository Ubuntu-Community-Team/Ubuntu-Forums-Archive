---
title: "Problem with NTFS and Captive"
date: 2006-01-23
forum: General Help
---

### Post by l0cke on 2006-01-23
Okay, i need to do a windows repair and to do that i have to acess the NTFS drive in Linux. I am running the latest version of ubuntu 64 bit. 

For some reason whenever I try to mount my sata drive \dev\sda1 I get this error
```
paul@ubuntu:~$ sudo mount -t captive-ntfs /dev/sda /mnt/dosc
/usr/bin/fusermount: unknown option --
Try `/usr/bin/fusermount -h' for more information

Captive-ERROR **: FUSE fuse_setup() failed!
You may need Linux kernel 2.6.14 or higher with its 'fuse.ko' enabled.
You may also need to install or upgrade 'fuse' package to your system.
aborting...
paul@ubuntu:~$
Captive-WARNING **: CORBA Exception occured: id="IDL:omg.org/CORBA/COMM_FAILURE:1.0", value=0x8395d9c
aborting...
```

but it reports that fuse is alredy installed

```
paul@ubuntu:~$ sudo apt-get install fuse-utils libfuse2
*password*
Reading package lists... Done
Building dependency tree... Done
fuse-utils is already the newest version.
libfuse2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

So i'm thinking it could either be a problem with 64-bit of sata

I did try some Linux32 with this
```
sudo apt-get install ia32-libs ia32-libs-gtk linux32
```

and then tried to mount with this

```
paul@ubuntu:/$ sudo linux32 mount -t captive-ntfs /dev/sda1 /mnt/dosc

/usr/bin/fusermount: unknown option --
Try `/usr/bin/fusermount -h' for more information

Captive-ERROR **: FUSE fuse_setup() failed!
You may need Linux kernel 2.6.14 or higher with its 'fuse.ko' enabled.
You may also need to install or upgrade 'fuse' package to your system.
aborting...
paul@ubuntu:/$
paul@ubuntu:/$
Captive-WARNING **: CORBA Exception occured: id="IDL:omg.org/CORBA/COMM_FAILURE:1.0", value=0x8395d74

```

So i need your help! please? [-o<

---

### Post by l0cke on 2006-01-23
please? I REALLY need to get this working before friday!!  Icould try to compile fuse for mthe source too but i don't think that would help.
[-o< [-o< [-o< [-o< [-o< [-o< [-o<

---

### Post by izzydahedgehog on 2006-01-28
Support for FUSE wasn't added until the 2.6.14 kernel, and the latest kernel in the Ubuntu repositories is 2.6.12.  You'll have to compile your own.

I wrote a (very sketchy and unpolished) howto for getting Captive to work with Ubuntu. [https://wiki.ubuntu.com/CaptiveHowTo](https://wiki.ubuntu.com/CaptiveHowTo)

---

