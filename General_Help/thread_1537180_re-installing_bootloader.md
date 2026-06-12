---
title: "re-installing bootloader"
date: 2010-07-23
forum: General Help
---

### Post by sundays211 on 2010-07-23
hi

GRUB has not updated properly for some reason, and now I am left with an un-bootable system. I would like to know how to re-install grub without needing to re-install Ubuntu.

thanks

---

### Post by mdramige on 2010-07-23
The instructions at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) should work. Follow the instructions for Grub2 if you are using Lucid. (You will need a Live CD/USB)

---

### Post by sundays211 on 2010-07-23
didn't work

---

### Post by Butthead on 2010-07-24
Hmm, sudo install-grub (in the terminal) perhaps? :confused:

---

### Post by Mark Phelps on 2010-07-24
Read through the Reinstalling GRUB2 in the link below:

[ttps://help.ubuntu.com/community/Grub2]("ttps://help.ubuntu.com/community/Grub2")

---

### Post by yetiman64 on 2010-07-24
> **Mark Phelps said:**
> Read through the Reinstalling GRUB2 in the link below:

[ttps://help.ubuntu.com/community/Grub2](ttps://help.ubuntu.com/community/Grub2)

@Mark Phelps, your link needs a "h" at the start to be useable. yetiman64

> Firefox doesn't know how to open this address, because the protocol (ttps) isn't associated with any program.

---

### Post by sundays211 on 2010-07-25
I'll be more specific as to how it doesn't work. installing grub on /dev/sdb works perfectly fine, with the message:
 ```
ubuntu@ubuntu:~$ sudo grub-install /dev/sdb
Installation finished. No error reported.
ubuntu@ubuntu:~$ 

```appearing after the installation. the problem is: when i go to restart, the blinking curser appears, and stays up where the boot-loader would normally appear, just like before. attempting to install grub2 onto /dev/sda comes up with the following message:
```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

```. 
both of these disks are working properly, and ubuntu is installed between them (/boot and / on sdb; /home on sda).

I have a feeling that the problem has something to do with the partion table of sda.
the attachment is the partion table for sda, it shows that my home directory (sda6) is under an extended partion which is too small for it, no idea whether this has anything to do with anything, but might as well add it on

---

### Post by sundays211 on 2010-07-26
by fixing my partion table, I was able to re-install grub, and can now boot ubuntu again.
thanks for all you're help.

---

