---
title: "Windows 7 + Ubuntu Dual Boot Fail, Repartition?"
date: 2010-04-17
forum: General Help
---

### Post by xaurex on 2010-04-17
This has probably been posted before, but I haven't had much luck finding it.

O.k. I already had Windows 7 installed and decided to try out Ubuntu--just to, you know, mess around with stuff. During the partitioning part of the installation, I didn't pay attention as to how much space/volume I would shrink Windows down to, so I just went ahead and pressed forward with the default amount already on there (all of of the space went to Ubuntu, I'm thinking).

Now whenever I turn on my computer, I get a grub menu. On the list is Linux xxxx, Linux etc (blah blah blah), and then Windows 7 loader. It doesn't work, and suggests that I put in the Windows installation disc.

This is what my partitions look like on Gparted:

[CENTER][IMG]http://img651.imageshack.us/content_round.php?page=done&l=img651/3339/screenshotmttr.png[/IMG][IMG]http://img651.imageshack.us/content_round.php?page=done&l=img651/3339/screenshotmttr.png[/IMG][IMG]http://img580.yfrog.com/img580/3916/screenshot2x.png[/IMG]
[/CENTER]
 
I have the installation disc. Somewhere.

I'd like to keep the dual boot on Ubuntu and Windows 7 if that's possible.
But since Ubuntu is already working, if it's easier to just delete Windows 7, I'd like to know how to do that, too.

What should I do? (Answers or links to existing solutions are all appreciated)

---

### Post by toystory on 2010-04-17
Unfortunately, from what i'm seeing, your Windows 7 files are not there, just the Backup partition you had. If you want to Windows 7 and Ubuntu, in my experience, backup everything and start from scratch. 

Install Windows 7 First, and leave unallocated space, and then install Ubuntu, pick manual partition, and make a /, /home and linux-swap partition. 

Best regards,

Luis

---

### Post by wilee-nilee on 2010-04-17
> **xaurex said:**
> This has probably been posted before, but I haven't had much luck finding it.

O.k. I already had Windows 7 installed and decided to try out Ubuntu--just to, you know, mess around with stuff. During the partitioning part of the installation, I didn't pay attention as to how much space/volume I would shrink Windows down to, so I just went ahead and pressed forward with the default amount already on there (all of of the space went to Ubuntu, I'm thinking).

Now whenever I turn on my computer, I get a grub menu. On the list is Linux xxxx, Linux etc (blah blah blah), and then Windows 7 loader. It doesn't work, and suggests that I put in the Windows installation disc.

This is what my partitions look like on Gparted:

[CENTER][IMG]http://img651.imageshack.us/content_round.php?page=done&l=img651/3339/screenshotmttr.png[/IMG][IMG]http://img651.imageshack.us/content_round.php?page=done&l=img651/3339/screenshotmttr.png[/IMG][IMG]http://img580.yfrog.com/img580/3916/screenshot2x.png[/IMG]
[/CENTER]
 
I have the installation disc. Somewhere.

I'd like to keep the dual boot on Ubuntu and Windows 7 if that's possible.
But since Ubuntu is already working, if it's easier to just delete Windows 7, I'd like to know how to do that, too.

What should I do? (Answers or links to existing solutions are all appreciated)

So to me it looks like you installed Ubuntu in the spot where W7 was. The 100mb bootloader is there and the ntfs sda3 is a media backup. Is this correct you should be able to access the W7 partition sda3 from Ubuntu.

So what I notice also is that you have ubuntu in a primary partition, usually with a swap also installed they are both in a extended partition. Theoretically you can reinstall the W7 and leave the Ubuntu as it is, but if it was me I would pull everything off the HD and do a custom install of W7 into a ntfs partition pre-formatted with gparted. You don't want to resize W7 with gparted but W7 will install into a partition made by gparted. Then install ubuntu afterward.

I would do it this way inspite of knowing how to reload the bootloaders for either OS. In the end it will clean up your system and it should look like this.
[ATTACH]153534[/ATTACH]

---

### Post by john newbuntu on 2010-04-17
Yeah, it looks like /dev/sda2 probably was your former win7.  That has now been formatted as ext4.  So you have lost the ability to run win OS.  Plus you have used up all your primary partitions.

I'd say start clean like toystory suggested.  Wipe out all partitions except /dev/sda3 (You could even shrink this later or just move it out of the way - i.e, copy it to an external device and restore later).  Then create one primary NTFS partition for win7 and the rest in extended partitions.  One ext4 partition for Ubuntu, a swap partition approx = twice your RAM size and leave some empty space for future expansion or shares. (You could create more partitions if you need your /home and /opt to be in separate partitions)
Then install Win7 first followed by Ubuntu using manual partitioning from liveCD.

---

### Post by xaurex on 2010-04-17
Woah. That was quick.

But yeah, thanks. I'll probably leave it alone for a while 'til I find the time to wipe it totally clean.

---

