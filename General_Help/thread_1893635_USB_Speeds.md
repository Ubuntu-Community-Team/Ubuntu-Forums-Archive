---
title: "USB Speeds"
date: 2011-12-10
forum: General Help
---

### Post by paddy100 on 2011-12-10
The one thing that gets me about Ubuntu is the speed it moves/copies files between USB disks. It has been covered in depth in the past - and I am surprised the developers have not found "fix" for it yet, but with a theoretical highest speed of 480Mb/s for USB2 I am copying at 5.7Mb/s in Ubuntu.
It is faster for me to boot to Windows - copy/move the files, and boot back to Ubuntu than it is for me to do it in Ubuntu.

Ive tried the BIOS settings/updates, I have 2GB ram, starting with the disks attached/ not attached ..... etc. Yet I am down to almost 1% of the maximum transfer speed. This is a major factor why I cannot get rid of Windows.

Is there ever going to be a fix there for this issue?

---

### Post by bluexrider on 2011-12-10
> **paddy100 said:**
> The one thing that gets me about Ubuntu is the speed it moves/copies files between USB disks. It has been covered in depth in the past - and I am surprised the developers have not found "fix" for it yet, but with a theoretical highest speed of 480Mb/s for USB2 I am copying at 5.7Mb/s in Ubuntu.
It is faster for me to boot to Windows - copy/move the files, and boot back to Ubuntu than it is for me to do it in Ubuntu.
Ive tried the BIOS settings/updates, I have 2GB ram, starting with the disks attached/ not attached ..... etc. Yet I am down to almost 1% of the maximum transfer speed. This is a major factor why I cannot get rid of Windows.
Is there ever going to be a fix there for this issue?

Using NTFS formatted thumb drive would be slower than EXT4 because NTFS is not native to the kernel - its part of ntfs-fuse which is magnitudes slower than native MS NTFS.

I expect it is a performance issues with NTFS.   Is the USB disk partition you're working off NTFS formatted? 

What  does your CPU look like while your copying these files? 

If it is I would recommend not using NTFS on the USB disk unless you have to.

If you have to there is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/392204")  with NTFS-3G, though it doesn't list 11.04 as impacted. 

There is a  comment that someone has confirmed it on 11.04, but anyway some people  have had luck with an [unofficial PPA]("https://launchpad.net/%7Ex3lectric/+archive/team-iquik-releases/+packages") though they have on packages for 11.04 yet.  
  
Another fix may exist, if indeed this bug applies.

---

### Post by BC59 on 2011-12-10
More details about workarounds for the slow speed:

[http://superuser.com/questions/203538/how-do-i-get-better-usb-transfer-speeds-in-xubuntu](http://superuser.com/questions/203538/how-do-i-get-better-usb-transfer-speeds-in-xubuntu)

---

