---
title: "&quot;Uninstalling&quot; LiveCD Ubuntu from Win7"
date: 2012-01-31
forum: General Help
---

### Post by NewWorldInOrder on 2012-01-31
I recently installed Ubuntu via LiveCD on my laptop. On my PC, I use Ubuntu so I wanted to install linux on my laptop for fun. Long story short, I really want to "uninstall" Ubuntu from my laptop. I remember Wubi had an uninstall button, but I can't do much on dual boot Ubuntu + Win 7.

I've gone through several Google searches, but I'm kinda confused. Also, most of them were for Windows XP and Windows Vista. I am a Windows 7 Home Premium User, fyi. 

I tried searching the forums but I think it's either I didnt dig deep enough or I just couldn't find it.

TLDR; Please help me remove Ubuntu from my laptop without damaging my Windows files. Also, can someone please inform me how to reallocate the Ubuntu partition back to Windows?

---

### Post by bcbc on 2012-01-31
To remove a dual boot, you need to reinstall the windows bootloader, and after that remove the partitions created when you installed.

Step 1
======
So, if you don't already have one, create a Windows repair CD from your current Windows install. Then boot from it to a repair prompt and run:
```
bootrec /fixmbr
```
This replaces the grub2 bootloader.

Step 2
======
From now on your computer must boot directly to Windows (with no grub menu) before you can proceed to remove the linux partitions.

Step 3
======
Hit the Windows key, type in "Disk Management". This will show "Create and format hard disk partitions" above. Select that. You'll see a couple of unknown partitions (one corresponding to the size of the Ubuntu partition - and the other the size of the swap partition). You can delete these and then merge the free space back into your windows partition. You'll also have to delete the extended partition in order to merge it back (if one was created during the install). You could also just create a separate new NTFS partition in the space and keep the extended.

---

