---
title: "GRUB won't show Vista"
date: 2011-02-02
forum: General Help
---

### Post by HHBones on 2011-02-02
Right, so I had Ubuntu 10.04LTS installed on my system, dual-booting with Vista. However, I ran out of space on it, so I decided to do a fresh install of Ubuntu. I used LXF-DVD 138, which came with Ubuntu 10.10. I partitioned some extra space in Windows as well. So, I installed it, all was well, until I rebooted to go back to Windows. It was gone from the GRUB menu. It's still accessible from Ubuntu: I can still see the files, and it still shows the partition as being mounted under /dev/sda1. Gparted is giving me this weird warning, however, when I select the partition:

Warning:
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name: /dev/sda1
NTFS volume version: 3.1
Cluster size: 4096 bytes
Current volume size: 483450491392 bytes (483451 MB)
Current device size: 483450491392 bytes (483451 MB)
Checking filesystem consistency...
Cluster 69905721 is referenced multiple times!
Cluster 69905722 is referenced multiple times!
Cluster 69905723 is referenced multiple times!
Cluster 69905724 is referenced multiple times!
Cluster 69905725 is referenced multiple times!
Cluster 69905726 is referenced multiple times!
Cluster 69905719 is referenced multiple times!
Cluster 69905720 is referenced multiple times!
ERROR: Filesystem check failed!
ERROR: 8 clusters are referenced multiply times.
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.

Unable to read the contents of this file system!
Because of this some operations may be unavailable.

The following list of software packages is required for ntfs file system support: ntfsprogs.

Because I can't boot into Windows, I tried running chkdsk /f from the install disk. It didn't work.

Also, for some reason, it says that it isn't mounted, but it isn't giving me an option to mount it, and the terminal command won't work.

How can I re-mount this and make it bootable? The 'boot' flag is still active in Gparted. How can I make this work?

---

### Post by hansolo4949 on 2011-02-02
try doing "Chkdsk c:/f" to have it look at your primary (c) partition. It does sound like something may have corrupted some sectors on the drive, and chkdsk will help fix that. Now, if that doesn't work, I suggest you immedately whip out the recovery cd, open up a cmd, and type BOOTREC /fixmbr (note the space!) and BOOTREC/fixmbr. That way, you will at least be able to us Windows to boot Vista again. Now, this means Ubuntu will be axed, but then again, I doubt thaty really matters, as potential data loss here is very high. Now, if Vista won't boot itself, you should fool around with the program on the recovery cd to fix boot problems (if it is on a Vista recovery disk, I am speaking from experience with Windows 7). Now, if anyone else has another solution, I suggest you go with that, since this is a little extreme, unless you are okay with pulling your sensitive data off of Vista via Ubuntu, before mucking around with trying to fix Vista. Remember, safety first, especially when it comes to files!:D

---

### Post by coffeecat on 2011-02-02
> **HHBones said:**
> Because I can't boot into Windows, I tried running chkdsk /f from the install disk. It didn't work.

I presume you mean from the Windows install disk. I believe that sometimes you have to run chkdsk several times to clean up a corrupted NTFS filesystem.

> **HHBones said:**
> Also, for some reason, it says that it isn't mounted, but it isn't  giving me an option to mount it, and the terminal command won't work.

Linux will refuse to mount a NTFS filesystem that it detects is damaged, in order to prevent further damage. You will not be able to mount it until you've repaired it.

> **HHBones said:**
>  So, I installed it, all was well, until I rebooted to go back to Windows. It was gone from the GRUB menu.

To get Windows back into the grub menu, there are two things to try. First, in Ubuntu, from the terminal:

```
sudo update-grub
```If that doesn't work, have a look in Synaptic to see if os-prober is installed. It should be - it's part of a default installation - but I've come across a handful of threads where it seems to have gone missing somehow. If it's not on your system install it and run 'sudo update-grub' again. Hopefully, if you can get Vista into the grub menu, it will do a chkdsk to itself when you try to boot it.

---

### Post by HHBones on 2011-02-02
Looks like os-prober indeed went missing. Installing nao...

---

### Post by hansolo4949 on 2011-02-02
+1 for sudo update-grub, I forgot about that.

Thank you for helping me out with this, coffeecat. I have fortunately never needed to have any experience with chkdsk except for occasional maintenance, since I usually am not a risk-taker when it comes to my computer, since spending 2 1/2 days setting my computer completely back up, and spending a week afterwards installing/configuring things I forgot about can be quite a headache after my computer fails because of something. So, if all else fails, use the recovery cd, and if chkdsk or another option works, congratulations!

---

### Post by HHBones on 2011-02-02
Ran chkdsk c:/f over and over until it stopped showing errors. Now it works fine in Ubuntu, and it's giving me the option to mount it in the file browser, but when I click 'mount' it does nothing. I REALLY don't want to axe Ubuntu, because then I have to spend two days setting everything up again- I can even switch between GNOME and KDE on the fly.

---

### Post by coffeecat on 2011-02-02
> **HHBones said:**
> Ran chkdsk c:/f over and over until it stopped showing errors.

First things first. Can you boot into Vista? If you can't, I don't think it's a good idea to mount the Vista C: partition.

> **HHBones said:**
>  Now it works fine in Ubuntu, and it's giving me the option to mount it in the file browser, but when I click 'mount' it does nothing.

I don't follow: what works fine in Ubuntu? I presume that by giving you the option to mount in the File Browser, you mean that it's listed in the left pane of the browser and in the Places menu. (By the way, I'm referring to gnome here - I haven't used KDE for ages so I can't remember how it behaves with automounting partitions.)

What do you mean by 'click on mount'? In gnome you simply click on the name of the partition. If that's what you mean and it won't mount then something may still be wrong with the filesystem. Also - check that you don't have gparted open. If it's open you can't mount a partition from the file browser.

---

### Post by HHBones on 2011-02-02
If I backed up Ubuntu on my external drive by copying all the files to it manually, then axed it, reinstalled it, and pasted all the files back, I would have the same stuff, and I'd get to boot up with no time wasted on configuring everything again, right?

---

### Post by coffeecat on 2011-02-02
You've lost me now. I thought the problem was trying to get Vista into the grub menu and get it booting. Why are you wanting to backup and restore Ubuntu? :|

---

### Post by HHBones on 2011-02-02
> **coffeecat said:**
> First things first. Can you boot into Vista? If you can't, I don't think it's a good idea to mount the Vista C: partition.



I don't follow: what works fine in Ubuntu? I presume that by giving you the option to mount in the File Browser, you mean that it's listed in the left pane of the browser and in the Places menu. (By the way, I'm referring to gnome here - I haven't used KDE for ages so I can't remember how it behaves with automounting partitions.)

What do you mean by 'click on mount'? In gnome you simply click on the name of the partition. If that's what you mean and it won't mount then something may still be wrong with the filesystem. Also - check that you don't have gparted open. If it's open you can't mount a partition from the file browser.

Right, sorry, Gparted has stopped showing errors with the NTFS partition. So, I find it in the file browser (Don't remember the name in GNOME) and right-click. There's an option 'mount'. When I click it, it doesn't do anything. Whatsmore, I can't access it anymore, or my 500GB external drive, for that matter.

---

### Post by coffeecat on 2011-02-02
Can you boot into Vista?

---

### Post by HHBones on 2011-02-02
I've got all my stuff backed up, now it's time to axe Ubuntu. Thanks.

---

### Post by HHBones on 2011-02-02
I don't refresh often enough. I cannot boot into Vista, and I'm backing up Ubuntu so that I can axe it and fix the master boot record. Then, I'll reinstall Ubuntu and restore from the backup. That'll give me a nice clean GRUB screen, too.

---

### Post by coffeecat on 2011-02-02
> **HHBones said:**
> I cannot boot into Vista,

Which possibly means that there is still filesystem corruption whatever gparted tells you. And that might explain why you can't mount the partition.

> **HHBones said:**
>  and I'm backing up Ubuntu so that I can axe it and fix the master boot record.



Two comments:

Repairing the Windows mbr has no effect on Ubuntu at all, except to overwrite grub stage 1 which is a trivial issue. Therefore there is no need to backup and 'axe' Ubuntu.

I don't think that restoring the Windows mbr is going to help at all. The problem with Vista is in the Vista C: partition. The mbr is in the first 400 or so bytes of the hard disk - nowhere near the C: partition. Actually the first 512 bytes - the mbr includes the partition table, but the Windows mbr boot code occupies the first little over 400 bytes.

---

