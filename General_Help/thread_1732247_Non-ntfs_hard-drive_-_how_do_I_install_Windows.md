---
title: "Non-ntfs hard-drive - how do I install Windows?"
date: 2011-04-18
forum: General Help
---

### Post by demonboy on 2011-04-18
Hi,

Some time ago I reformatted my hard drive to just run Ubuntu. Now I need to install Windows XP but when I put in the install disk it says it can't find a hard drive. I'm guessing this is because the hard drive is formatted to a Linux-specific ext4/extended/linux-swap set-up. 

The ext4 partition is 71GB and only uses 13GB. I have 57GB free. I can see all this in Gparted but how do I now split that ext4 up and free some space for ntfs partition for Windows? Indeed is this what I should be doing? Obviously I can't unmount the ext4 bit whilst in Ubuntu.

Ultimately I want to do a complete reformat of the hard disk and just install Windows XP for the time being (I'm handing the laptop in for a hardware service).

My current set-up is:

```

Partition       File System  Mount Point     Size          Used          Unused         Flags
/dev/sda1    ext4             /                    71.60GiB   13.82GiB    57.79GiB      Boot
/dev/sda2    extended                            2.93GiB        -                 -          
/dev/sda5    linux-swap                          2.93GiB        -                 - 

```

Can anyone offer some pointers?

---

### Post by ububeginner on 2011-04-18
You should be able to reformat and do anything you want to the drive from a Ubuntu Live cd
However, if you reformat the entire drive to NTFS and still fail to install Windows, you won't have a working PC

---

### Post by Mark Phelps on 2011-04-18
You'll need to boot, either from an Ubuntu LiveCD, or from a GParted LiveCD, in order to shrink the Linux partitions to make room for installing XP.

Why a CD? Because you have to mount the Linux partition containing the OS in order to run it and you can't do partitioning work on a mounted partition.

---

### Post by demonboy on 2011-04-19
I used the Gparted Live CD (on a USB) to reformat the hard drive. I have tried every single possible combination and type of hard drive format yet the Windows CD refuses to see any hard drive at all. I've tried NTFS, FAT16 (except that's a max 4GB so useless), FAT32, EXT4. I tried partitioninig it so I had both NTFS and EXT4 and I tried the whole drive as NTFS. I tried flagging the drive as 'boot' too, yet every time the CD refused to see the hard drive. I know the CD is not at fault.

I have tried doing a search on this subject and it seems quite a few other people have had problems getting their Windows installation CD to see the hard drive yet I can't find a solution.

---

### Post by ububeginner on 2011-04-19
Do you have a SATA harddrive?
If so, XP doesn't have built in drivers for your drive.
Maybe this link can help you
[http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/](http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/)

---

### Post by ububeginner on 2011-04-19
Reading through the comments in in the link in my previous post i found some possible simpler solutions. (if you do have a SATA  drive that is)
check out what wil and Nicolas Stears have to say 
[http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/#comment-23733](http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/#comment-23733)

---

### Post by dragonfly41 on 2011-04-19
I agree ububeginner .. I had the same problem trying to install XP on Dell Inspiron 1720 and I went into Bios (F2) to make the simpler change .. I have a SATA drive.

> A more simple solution. Go into your bios and change your SATA Device Operation to ATA instead of AHCI.

---

### Post by demonboy on 2011-04-19
OK, progress has been made. I wasn't able to change my SATA to ATA but I could change it to IDE (it's quite an old, cheap Acer) and that has done the trick.

Thank you to everyone who replied. I will now mark this topic 'solved'. Cheers.

---

