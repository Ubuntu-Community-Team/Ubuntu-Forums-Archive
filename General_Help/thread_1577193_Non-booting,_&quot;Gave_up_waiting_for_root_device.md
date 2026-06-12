---
title: "Non-booting, &quot;Gave up waiting for root device&quot; problem"
date: 2010-09-18
forum: General Help
---

### Post by peterx14 on 2010-09-18
Hi all,

This problem is now "solved", but I wanted to post it here (1). for the benefit of anyone else, and (2). in case it happens to me again I'll know what to do!

Yesterday, I booted my Ubuntu 9.10 machine from cold and after going through the Grub menu and getting the Ubuntu splash/loading logo, I got a page saying "Gave up waiting for root device. Common problems:" blah blah "ALERT! /dev/disk/by-uuid/-long id here- does not exist. Dropping to shell!". See attached image for a photo!

I tried booting with the same kernel version in recovery mode, but it made no difference. I booted with my live CD, and Disk Utility said the root partition was "unrecognized". My other partitions (/home /srv and an NTFS partition for WinXP dual-boot) were all fine. GParted showed the partition correctly however and showed it formated as EXT4... so I guess the two utilities draw their information from different places.

I opened a terminal and ran "sudo fdisk -l" and made a note of the device path for each partition. My root partition is on /dev/sda2.

One thing to note -- I'm not one for diving in and changing things before I understand the problem especially when it relates to file-systems. So I next ran "sudo e2fsck -n /dev/sda2" to check the file-system without risking any attempts to fix it. This showed the fs as being "clean" anyway. Same when I tried "sudo e2fsck -nf /dev/sda2". Unlike my other partitions, my root partition did not show in the "Places" menu, so if I wanted to mount it, I'd need to do this manually.... and since I didn't want to damage anything, I mounted it read-only using: "sudo mount -r -t ext4 /dev/sda2 /media/mp" (I'd created the /media/mp mount point before!). The file-system looked completely intact to me.

So further googling suggested I should press "e" at the Grub menu and change the line "root=UUID= -long-ID-" to the device path as "root=/dev/sda2". I did this, and it did indeed boot correctly.

The same page also suggested that to fix this permanently I'd need to use tune2fs to reset the UUID that had presumably got damaged somehow. Again, not wanting to change anything unnecessarily, I checked this first using "sudo tune2fs -l /dev/sda2" but I found it already had the correct UUID!!

So... I didn't change anything. I rebooted, expecting it would fail again, but it didn't. Whatever the problem was, "it fixed itself"... kind of.

For reference, this machine was a clean install of 9.10 that I installed in either November or December 2009 and it has been working fine ever since and is booted every day. My /, /home and /srv partitions and all EXT4 and there is a separate swap partition. Prior to this problem, the system seemed to shut down cleanly. I can think of no reason *why* it decided to not work the day it failed.

Oh, also, before "fixing" the problem, I physically powered the machine off to ensure no bit of hardware was left in some weird state.

I'm not really any wiser as to what actually caused the problem though. I suspect something is coded in a way that makes it more fragile than it need be.... I'm basing this on the fact that this error seems not uncommon.

Hope this helps someone anyway!! :D

---

### Post by peterx14 on 2010-10-02
Just had exactly the same thing happen! I'd booted to Ubuntu from cold, used Thunderbird, Chromium browser and edited an OpenOffice spreadsheet and then shutdown. When I next started the computer, I got the same error as before, and resolving it was the same as before also.

I *think* there was an fsck on my first boot of the day, although I've just looked in /var/log/fsck/checkfs and checkroot and both files say "(Nothing has been logged yet.)" -- maybe there's a log elsewhere?

I've just tried "sudo tune2fs -l /dev/sda2" and can confirm this filesystem was checked on my first boot of the day.

Dunno if that is what is causing the problem though!

---

