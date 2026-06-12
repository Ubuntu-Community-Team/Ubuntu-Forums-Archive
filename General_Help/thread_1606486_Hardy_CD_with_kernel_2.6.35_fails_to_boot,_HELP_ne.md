---
title: "Hardy CD with kernel 2.6.35 fails to boot, HELP needed!"
date: 2010-10-26
forum: General Help
---

### Post by domi007 on 2010-10-26
Hey everyone,
So I just finished doing a Hardy based LiveCD. I made an installation in VirtualBox, installed some packages, and then compiled a totally new kernel, 2.6.35, actually this one:
[http://dect.osmocom.org/trac/dect](http://dect.osmocom.org/trac/dect)

I compiled squashfs support in the kernel naturally

Everything seems to be fine, the system boots up normally etc.

But here comes the trouble: I make the iso file with remasterys (2.0.12-latest for Hardy) but this iso isn't able to boot.

It drops to busybox shell, casper.log says:
/init: 1 /dev/sr0: no such file or directory
Unable to find medium with the livesystem.

My /dev folder is totally empty, it contains only the shells (8 pieces of tty).

I don't know what's wrong...my rootfs is surely mounted, mount shows
rootfs rw /

Please help me, I really need this thing working.

Thanks,
DOMy

mod: Exactly the same system, but with SquashFs 3 and kernel 2.6.24 (default Hardy kernel) works and boots...

---

### Post by domi007 on 2010-10-26
It gets even stranger: in dmesg I do have the kernel recognizing the CD-Drive, saying: Attached SCSI CD-ROM sr0

It seems that the kernel finds the CD-drive but doesn't add it to the /dev or it adds it there, but then there is a change in filesystems, and it doesn't gets carried on or IDK.

BTW, now I do have a full /dev tree, except for sr0...(just switched to the latest 2.0.17 remastersys).

---

