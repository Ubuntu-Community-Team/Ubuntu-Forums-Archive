---
title: "How to remove OPEN SUSE????"
date: 2011-07-26
forum: General Help
---

### Post by Drazer on 2011-07-26
Hello Guys......I am new to this Forum...
I have installed Windows 7 and OPEN SUSE 9.0 32-bit on my machine...
and Now I wish to remove OPEN SUSE and instal Ubuntu!
So can u pls tell me how to uninstal OPEN SUSE ??????
I have first installed Windows 7 and then Open Suse.


Thanks..

---

### Post by dim_hyder on 2011-07-26
Hi Drazer,

You just need to download the Ubuntu ISO from the website, burn to CD/DVD. Boot from the CD/DVD drive (assuming BIOS is already bootable since OpenSUSE was installed).

Once loaded there should be an icon on the desktop to "Install Ubuntu 11.04"

Double click this icon and following the screens prompts through to the "Allocate drive space" screen.

Select "something else"

You should see how the HDD is partitioned. An NTFS partition for windows 7 and the partitions created for the OpenSUSE install.

WARNING ***** If unsure do not proceed. ********

At this point you need to delete the partitions created by OpenSUSE and leave the windows 7 partitions.

If you get the wrong partition your windows 7 data will be lost and you will need to re-install.

What partitions do you have displayed on this screen?

Cheers,

Pete

---

### Post by Quackers on 2011-07-26
Welcome to UF.
Download your chosen iso and burn the image to disc or USB flash drive.
Boot from it and choose "try Ubuntu" to make sure your hardware works. When you're happy click on the install icon on the desktop.
During installation choose "manual" partitioning (or if it's 11.04 choose "something else") then choose your openSUSE partition(s) and install Ubuntu there, over-writing openSUSE.

---

### Post by nothingspecial on 2011-07-26
Hi, boot up a ubuntu live cd/usb

Choose install

During the process, it will ask you how you want to install Ubuntu.

Choose "something else" or "manual" depending on which version you install.

It will list your partitions. Make sure you know which one is windows and which one is suse. Choose the suse one. Click "edit" or "change".

Choose to use it as an ext4 journaling file system.

Check the format box

Give it a mountpoint of /
[COLOR="Red"]
Do not do anything with the windows partition[/COLOR]

Back up before you do this.

---

### Post by Drazer on 2011-07-26
[COLOR="Red"]Thanks Guys....:)[/COLOR]

---

