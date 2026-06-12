---
title: "Add Windows XP to dual boot setup with Vista and Ubuntu"
date: 2011-03-07
forum: General Help
---

### Post by tblom on 2011-03-07
Hi all,

I 'm currently using grub to dual boot Windows Vista and Ubuntu 10.10.
These are some of my partitions:

- one NTFS partition for Vista
- one NTFS partition for my Vista Data (shared with Ubuntu)
- one ext3 partition for Ubuntu (mounted at /)
- one very large ext3 partition for my Ubuntu home folder (mounted at /home)

I would now like to add Windows XP to this setup, but I am not sure where to start.

I know I need to somehow shrink the large ext3 partition so I have an extra partition for XP, which should be NTFS.

Then I assume I need to install XP on this partition, and somehow make XP appear in grub.

I have no idea how to do these things. Can anyone help? Please keep the instructions very basic, do not assume that I know anything. 

Thank you!

tblom

---

### Post by lithopsian on 2011-03-07
Yes, shrinking partitions.  Always scares me!  Back up anything you can't afford to lose.  Shrink the partition that you want.  Format the spare space as NTFS.  Install XP

Sounds easy.  It isn't.  Windows will want to be on a primary partition, but the new NTFS partition will be an extended partitions.  You'll have to post more detailed gparted output to get instructions on exactly how to sort that out.

Fixing grub afterwards is very easy.  sudo update-grub will usually take care of it.

---

### Post by oldfred on 2011-03-07
It is much better if you use a primary partition for all windows installs. A second windows install will go into a logical partition. Windows second installs move boot files to first install (active partition or boot flag). But if in a logical partition and you delete first install the logical is usually not repairable. Some here have work arounds to directly boot XP from a logical but not Vista/7. 

Do you want to directly boot either windows from grub. Normally you have to boot the one active partition windows and it will then give you the choice to boot the other installs.

[http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products](http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products)
louieb's suggestion:
Just a note about dual booting 2 MS products. When you install the 2nd one - the installer will put its boot loader in the partition with the boot flag on (usually the partition holding the 1st MS product). And the 2nd product can only be booted thru the boot loader in the 1st product.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

