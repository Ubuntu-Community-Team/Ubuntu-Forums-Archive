---
title: "Unable to boot ubuntu, unable to access root drive from live CD"
date: 2010-07-16
forum: General Help
---

### Post by PhoenixDream on 2010-07-16
Hi,

Im having a serious issue with booting ubuntu 10.04, the issue being it wont boot up at all, after working so well for so long (i suspect some recent dodgy system updates are responsible) so I decided to just reinstall ubuntu from scratch again but wanted to retrieve some important files from my root device. 
So I am running the live desktop and I can see my previous filesystems under places but cannot mount or open my original root device where the files I want to recover are located, I receive this error msg:

"Unable to mount 77 GB Filesystem

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

Any insight or help is most appreciated.

---

### Post by dcstar on 2010-07-16
> **PhoenixDream said:**
> Hi,

Im having a serious issue with booting ubuntu 10.04, the issue being it wont boot up at all, after working so well for so long (i suspect some recent dodgy system updates are responsible) so I decided to just reinstall ubuntu from scratch again but wanted to retrieve some important files from my root device. 
So I am running the live desktop and I can see my previous filesystems under places but cannot mount or open my original root device where the files I want to recover are located, I receive this error msg:

"Unable to mount 77 GB Filesystem

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

Any insight or help is most appreciated.

Do a fsck on the drive, if something corrupted it then you cannot mount it until that is resolved.

---

### Post by PhoenixDream on 2010-07-16
Hi,

I was able to do that and this is output from that command:

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda1: clean, 329528/4685824 files, 15063218/18730240 blocks

In the meantime I have been able to mount the drive in question via live desktop but it still wont boot up even though it appears to be 'clean'.

---

