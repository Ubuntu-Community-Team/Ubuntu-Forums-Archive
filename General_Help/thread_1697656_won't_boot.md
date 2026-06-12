---
title: "won't boot"
date: 2011-03-01
forum: General Help
---

### Post by F104G on 2011-03-01
Aaaargh!  Ubuntu was working fine when I switched off the machine 2 days ago, when I tried to turn it on the following day I couldn't get past the initial black screen.  Here's what it says:


[B]GNU GRUB version 1.98+20100804-5ubuntu3

Ubuntu with Linux 2.6.35-23-generic
Ubuntu with Linux 2.6.35-23-generic 9recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial cpnsole 115200[/B]

I have tried all options but either of the first two give me a scrolling screen full of text which is moving too fast to read.  It finishes on a screen which says (amongst other things) :

[B]mount:mounting /dev on /root/dev failed: No such file or directory
mount:mounting /sys on /root/sys failed: No such file or directory
mount:mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have requested /sbin/init.
No init found.  Try passing init= bootarg.[/B]


Either of the bottom two options goes into blue screen test mode and, after a while, tells me that memory test is complete and there are no errors.

Looking around, I have seen similar problems where the fix seems to be to boot from a CD or USB stick and then fix it once in, but I am unable to do this.  I downloaded the disc image from the web on my partner's MAC and wrote it onto the USB stick as directed, but when I tried to start my machine with the USB stick it just says:

[B]Disk error
Press any key to restart[/B]

:confused: any ideas?

---

### Post by F104G on 2011-03-01
Update: I managed to burn a CD, which WOULD boot.  Ran this on the sick machine and did the following in terminal:

**sudo fdisk -l**

which reveals
[I]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Disk identifier: 0x000ee3a2

Device         Boot         Start           End         Blocks               Id     System
/dev/sda1     *                 1           19275      154821632    83     Linux
/dev/sda2                19275          19458      1466369          5      Extended
/dev/sda5                19275          19458      1466368        82     Linux swap / Solaris[/I]


**sudo fsck /dev/sda1**

which gives me
[I]fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open another program?[/I]

...and I'm stuck (again)

---

### Post by F104G on 2011-03-04
Working with the people over at Launchpad, I tried this:

**sudo mount /dev/sda1 /mnt**

nothing much happened after that.  I'm then advised to go
**sudo grub-install --root-directory=/mnt /dev/sda**
but do I do it straight away or wait until my first line of text gives me some sort of result?  How long does it take?  Been waiting about 15 minutes so far...

---

