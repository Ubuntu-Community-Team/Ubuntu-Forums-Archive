---
title: "installing ubuntu with windows 7, slide the divider"
date: 2012-06-06
forum: General Help
---

### Post by bpb101 on 2012-06-06
When i go into install ubuntu alongside windows 7, im asked 
"allocate drive space by dragging the divider"
But what side of the divider is which,

---

### Post by holycow131415 on 2012-06-06
[http://www.youtube.com/watch?v=ulpaWPDWwHs](http://www.youtube.com/watch?v=ulpaWPDWwHs)

---

### Post by wilee-nilee on 2012-06-06
> **bpb101 said:**
> When i go into install ubuntu alongside windows 7, im asked 
"allocate drive space by dragging the divider"
But what side of the divider is which,

Do not do the resize this way, use the W7 partitioner to resize it, reboot to make sure you are running then install.

Here is why I see this everyday on the forum.
[http://ubuntuforums.org/showthread.php?t=1998454](http://ubuntuforums.org/showthread.php?t=1998454)

Back up/clone W7 before you do anything.

---

### Post by wilee-nilee on 2012-06-06
> **holycow131415 said:**
> [http://www.youtube.com/watch?v=ulpaWPDWwHs](http://www.youtube.com/watch?v=ulpaWPDWwHs)

That is a very deciving video it is a install of ubuntu in a virtual in windows it does not mention this and magically a ext4 shows up. YOU would not make a NTFS for a ubuntu install, or ever format a partition for Ubuntu or any open source in windows.

Although it does say to resize the windows in windows.

A badly made video at the least.

---

### Post by Mark Phelps on 2012-06-07
> **wilee-nilee said:**
> Do not do the resize this way, use the W7 partitioner to resize it, reboot to make sure you are running then install.

Strong +1 on this advice!  Using the slider risks corrupting the Win7 OS partition, and if that happens, you won't be able to boot into Win7 to fix it.

IF you're going to dual-boot with Win7, suggest you read through the material below BEFORE you do that ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space. When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by holycow131415 on 2012-06-07
> **wilee-nilee said:**
> That is a very deciving video it is a install of ubuntu in a virtual in windows it does not mention this and magically a ext4 shows up. YOU would not make a NTFS for a ubuntu install, or ever format a partition for Ubuntu or any open source in windows.

Although it does say to resize the windows in windows.

A badly made video at the least.

1. Done in VM to record it and it doesnt matter if its in a VM...
2. In windows cannt format to ext4 first after shrinking it within windows, so i chose ntfs.
3. No harm formatting new volume to ntfs first while in windows, though it may not be needed.
4. Its explained to change to ext 4 as its shown when choosing root partition, and when you click ok it changes the display from ntfs to ext4. Need to format it to ext 4 from ntfs.
5. Not a bad video at all, shows how to properly shrink your hdd to dual boot. You shouldnt miss guide people as its helped many people already. K thx.

---

### Post by bpb101 on 2012-06-07
> **holycow131415 said:**
> [http://www.youtube.com/watch?v=ulpaWPDWwHs](http://www.youtube.com/watch?v=ulpaWPDWwHs)

what do you mean create another partition, swap 
In the Ubuntu Partition options do i just tick dev/sba3 ex4 (in the video case) and click install?

---

### Post by wilee-nilee on 2012-06-07
> **holycow131415 said:**
> 1. Done in VM to record it and it doesnt matter if its in a VM...
2. In windows cannt format to ext4 first after shrinking it within windows, so i chose ntfs.
3. No harm formatting new volume to ntfs first while in windows, though it may not be needed.
4. Its explained to change to ext 4 as its shown when choosing root partition, and when you click ok it changes the display from ntfs to ext4. Need to format it to ext 4 from ntfs.
5. Not a bad video at all, shows how to properly shrink your hdd to dual boot. You shouldnt miss guide people as its helped many people already. K thx.

Terrible example of correct technique it is not even there.
[B]
Do not make your own bad videos and post them here or I will report you next time.

[/B]I do not care if others claims it has helped I know this stuff and that is a very convoluted example and totally confusing.

---

### Post by holycow131415 on 2012-06-08
> **bpb101 said:**
> what do you mean create another partition, swap 
In the Ubuntu Partition options do i just tick dev/sba3 ex4 (in the video case) and click install?

While in ubuntu installer, in the partition you made, you have to make it root (/), with file system of ext 4 and resize it (shrink it) to allow you to make a swap partition. Size of your swap is usually at least the size of your ram.

> **wilee-nilee said:**
> Terrible example of correct technique it is not even there.
[B]
Do not make your own bad videos and post them here or I will report you next time.

[/B]I do not care if others claims it has helped I know this stuff and that is a very convoluted example and totally confusing.

LoL ok dude. If you are confused by the video then you really dont know your stuff. You arent the internet police. This isnt my first time helping people on these forums with videos... Also, it shows how much you really want to help the OP as you skipped his latest question.

---

