---
title: "command line locale problem?"
date: 2010-02-17
forum: General Help
---

### Post by abnobuntu on 2010-02-17
Hi All,

I installed a headless server to use as my file server. Some of the files has filnames in chinese.  when i tried plug in my external hd to move the files over, i noticed that I was not able to see a lot of the files in chinese. it was showing as "???" instead.  The weird thing is, I was able to see some in chinese, just not all.  The locale i have is en_US.UTF8. I even tried zh_CN.UTF8 but still doesn't work. I'm kinda lost as to what else i can do.  Please help! :confused:

---

### Post by dcstar on 2010-02-17
> **abnobuntu said:**
> Hi All,

I installed a headless server to use as my file server. Some of the files has filnames in chinese.  when i tried plug in my external hd to move the files over, i noticed that I was not able to see a lot of the files in chinese. it was showing as "???" instead.  The weird thing is, I was able to see some in chinese, just not all.  The locale i have is en_US.UTF8. I even tried zh_CN.UTF8 but still doesn't work. I'm kinda lost as to what else i can do.  Please help! :confused:

I would guess that you have to set the /etc/fstab line with the appropriate locale option for the filesystem type you are mounting.

---

### Post by abnobuntu on 2010-02-19
I tried to mount with UTF charset but ended up getting the following error:

> $ sudo mount -iocharset=utf8 /dev/sde1 /mnt/sde
mount: wrong fs type, bad option, bad superblock on /dev/sde1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


am i missing something?  I was able to mount fine without the iocharset options

---

