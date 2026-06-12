---
title: "Ran fsck on my live ext4 System"
date: 2009-09-26
forum: General Help
---

### Post by phoenix910 on 2009-09-26
Hey everyone - guess what I did? Well, in a very tired state, I cd'd to a mountpoint (/media/drive), and without thinking, ran fsck -y in that directory, thinking "oh yeah, it'll autodetect that drive" - obviously, it didn't - it ran it on my live filesystem instead (and ext4 FS running Ubuntu 9.04). Now, by the time I realised what was happening, my system had started jumping etc :P So, rebooted, got meself a Grub 2 error. Rebooted again, stuck in a live distro, and ran fsck.ext4 /dev/sdb2 - says it found some errors, corrected them, and then it states it's clean. Now though, if I go to mount it:
mount -t ext4 /dev/sdb2 /media/mountpoint
It complains thus:
> root@stephen-usb:/home/stephen# mount -t ext4 /dev/sdb2 /media/temp/
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

So I give dmesg a look:
> root@stephen-usb:/home/stephen# dmesg | tail
[ 1772.262120] ext4: No journal on filesystem on sdb2

So looks like I've lost me journal. I've just made an image of the partition with dd, and am going to try to see if I can get "extundelete" to work on it - however, by the looks of it, that probably won't work. Because this is fairly important to me to get this data back as quickly as possible, I thought I'd post here first to see if I can get some responses coming in :) I've never mucked around much with file/data recovery/journal rebuilds on Linux, however, I am reasonably experienced with general Linux usage, so I shouldn't be too much of a pain to work with (I hope). Thanks everyone :)


-------------------------------------------------------------


EDIT: Seems that the live fsck turned it (or at least tried to recognise it) as an ext2 system (thought this happened before, just confirmed) - I was hoping that an fsck.ext4 would've corrected it but obviously not. I dd'd the disk to an image, and then:
> root@stephen-usb:~# file /media/ISO/Recovery/image.bck 
/media/ISO/Recovery/image.bck: Linux rev 1.0 ext2 filesystem data, UUID=d1524d6a-58cf-4920-9a40-6c61c6ecaad2 (extents) (large files) (huge files)


-------------------------------------------------------------


EDIT: Also seems, as expected, that extundelete doesn't work without a journal:
> root@stephen-usb:/media/ISO/Recovery# extundelete --restore-all image.bck 
ERROR: The specified device does not have a journal file.  This program only undeletes files from file systems with journals.
Also tried it on a loop device, which I setup with losetup, just to be sure:
> root@stephen-usb:/media/ISO/Recovery# extundelete --restore-all /dev/loop0
ERROR: The specified device does not have a journal file.  This program only undeletes files from file systems with journals.
So, short of recreating a blank filesystem, what can I do :S Testdisk doesn't work with ext4 from what I know.

---

