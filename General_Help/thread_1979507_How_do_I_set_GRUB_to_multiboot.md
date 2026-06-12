---
title: "How do I set GRUB to multiboot?"
date: 2012-05-13
forum: General Help
---

### Post by pohlhaus59 on 2012-05-13
This is my first post.
I am trying to setup GRUB to multiboot Windows 7, Ubuntu and Puppy Linux.  I have Windows 7 and Puppy loaded.

GParted shows: 

/dev/sda1  NTFS  System reserved  100mb  boot

/dev/sda2  NTFS  WIN 7             37GB


/dev/sda5  ext2  PUPPY             19GB

/dev/sdb2  ext2  (Plan to put UBUNTU on second disk).


How do I set GRUB to multiboot?
It has been 7 years since I worked with UBUNTU.

I eventually want to add other Linux DISTROs.

JP

---

### Post by idoitprone on 2012-05-13
> **pohlhaus59 said:**
> This is my first post.
I am trying to setup GRUB to multiboot Windows 7, Ubuntu and Puppy Linux.  I have Windows 7 and Puppy loaded.

GParted shows: 

/dev/sda1  NTFS  System reserved  100mb  boot

/dev/sda2  NTFS  WIN 7             37GB


/dev/sda5  ext2  PUPPY             19GB

/dev/sdb2  ext2  (Plan to put UBUNTU on second disk).


How do I set GRUB to multiboot?
It has been 7 years since I worked with UBUNTU.

I eventually want to add other Linux DISTROs.

JP


WHenever you install another os
Just make sure that your main os that has grub in the mbr.

```
sudo update-grub
``` should do the trick

---

### Post by hal8000 on 2012-05-13
When you install another distribution, it will usually install grub or grub2
and will therefore replace the existing installation that controlled the boot process.

Grub2 is usually smart enough to pick up the extra distributions, so a new
install should go smoothly.

If you want the original distro to control the boot, reboot into this distro and run sudo update-grub

---

### Post by pohlhaus59 on 2012-05-13
GRUB is not yet installed.  I loaded puppy from the LIVE CD.

If I install it to /dev/sda1 will it pick up the Win7 boot record?
 
Do I go to the console in PUPPY and just type in the sudo command?

JP

---

### Post by oldfred on 2012-05-14
Do not install grub to any Windows partition as Window has to have its boot code in its NTFS partitions. You want to install grub2's boot loader to sdb and set BIOS to boot from sdb.

You should use ext4 (or at least ext3) for Ubuntu.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by nothingspecial on 2012-05-14
Title changed to reflect the question.

---

