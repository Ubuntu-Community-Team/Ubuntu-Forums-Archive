---
title: "Install over OS?"
date: 2010-05-14
forum: General Help
---

### Post by mclizardman24 on 2010-05-14
Hi.
I just requested a CD for the newest Ubuntu and was wondering if it was like the Wubi CD that you get when you download the image off the website. Also if doing a full install would affect another operating system that you are also using (I am running windows 7). Would you need a partition in the hard drive? How do I create a partition? Would I choose which os I wanted a boot up? Also, I was wondering if the CD you get when you request one is 32 or 64 bit. Thanks!

---

### Post by Dayofswords on 2010-05-14
well, the cd you request is really the same as the ISO image you download, just burned onto a cd already and comes in a nice sleeve

it comes with wubi and the full installing thingy too.(every iso aswell can do full install ind wubi)

if you doing a full install, yes, you need to partition it. the cd can help you do that when you go to install(there is a side-by-side option, a biggest continuous space, full wipe, and manual, if you dont know how to partition at all, dont choose manual) and by default it will install GRUB which allows you to choose which to boot, windows or Ubuntu, it will by default have the cursor over ubuntu's latest kernel

hoped that help

---

### Post by BoneKracker on 2010-05-14
Yes, you would need a partition (or better yet, a separate disk).

The installer will create a partition for you in free space.  The problem is that you have to create that free space yourself.  If your Windows install takes up the whole disk, and you only have one disk, then you may have to do one of the following:

a) add another disk (easy enough on a desktop system)

b) reinstall windows such that it only uses half the disk or so

c) use windows-based partitioning tools to shrink the size of your ntfs filesystem and partition

As far as I know, the installer cannot shrink down the Windows partition all by itself (although I haven't used Ubuntu for years, and don't know what the installer's capabilities are).  That would be nice, but as far as I know, it's not possible.  Somebody correct me if I'm wrong.

The best of these options is to use an additional disk.  That way, you can install the linux bootloader into the master boot record of the second disk and simply change the settings in your bios to use the second disk as the "boot disk".  The linux bootloader will let you choose whether you want to boot up linux or windows.

If you don't use a second disk, then the linux bootloader gets installed onto the master boot record of the disk that Windows is on.  It will still let you choose whether to boot linux or windows, but if you later decide you don't want to use linux, you've now written over (destroyed) your Windows master boot record and will have to stick in your windows install cd and run an obscure program to repair it.  (Whereas if you used the second disk, you simply switch your bios back to using the first disk as the "boot disk" and it's like you never installed linux at all.)

If you're on a laptop or a second disk is out of the question, then you might use option (c), but that's not for the faint of heart, and most windows-based partitioning software costs money.  In that case, probably the best option is to back up your personal files from windows to an external drive, reinstall windows, using the options that let you partition the disk (leaving space free for linux).  Then install linux.

The CD is either 32-bit or 64-bit depending on what you requested.  If you don't specifically remember requesting a disc for a 64-bit system, then you probably got a 32-bit disk.  You can get disks for 64-bit systems too.

---

