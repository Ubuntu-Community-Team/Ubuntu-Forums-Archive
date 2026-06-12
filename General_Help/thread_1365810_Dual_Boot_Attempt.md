---
title: "Dual Boot Attempt"
date: 2009-12-27
forum: General Help
---

### Post by lotusalive on 2009-12-27
Hi there all...  I am finally after a year of looking at Ubuntu Software in Synaptics Pkg Mgr, and playing with it all, feeling up to attempting a Dual Boot, only because I've not upgraded my Intel945 GC to something more wonderful, and would like to use it for W's.  

I went through the process of 'Installing GRUB to MBR instead of Root Partition' with Live-CD last night, but at instruction #6) Type "root (hd0,__), I got confused whether to do it as strictly "root (hd0,7)" or "root (hd0)."  I tried it both ways, and it succeeded in both, and left it in status "root (hd0)." 

I have created an 30 GiB NTFS Partition, prior to Swap and all other Linux Partitions, and it is mounted on /windows.  Then all Linux partitions follow it encased in an 'extended' partition.  I've installed all the NTFS software and MBR software, and planning to follow the Community Documentation for 'Installing Windows After Ubuntu.' The NTFS partition shows full File System Support.  But when I follow the command to Backup to boot sector, I get this reply: 

```
 dd if=/dev/hda of=/mbr.bin bs=512 count=1
dd: opening `/dev/hda': No such file or directory 
```
 
When I first installed Ubuntu last year, it completely wiped my Windows XP install, and we did not really understand why, but I just decided to go with it, since I like it so much ! :)  But now, I'm wondering if we'll ever be able to really make W's work again...

(There has been a Dual Boot with V-word on this Dell T5088 once before, but with V installed first, and someone drove Ubuntu, and even Red Hat, into it for 
me !)

All help greatly appreciated !

---

### Post by Zoot7 on 2009-12-27
I'm confused, did you install Ubuntu after windows or just start with no OS?

[QUOTE=lotusalive]I have created an 30 GiB NTFS Partition, prior to Swap and all other Linux Partitions, and it is mounted on /windows.  Then all Linux partitions follow it encased in an 'extended' partition.  I've installed all the NTFS software and MBR software, and planning to follow the Community Documentation for 'Installing Windows After Ubuntu.' The NTFS partition shows full File System Support.  But when I follow the command to Backup to boot sector, I get this reply: 

```
 dd if=/dev/hda of=/mbr.bin bs=512 count=1
dd: opening `/dev/hda': No such file or directory 
```[/QUOTE]
Try changing it to /dev/sda, you shouldn't really need to back up the MBR though.
Dual boots are normally easy, it's just a case of installing Windows on it's own partition while leaving room for Ubuntu, then installing Ubuntu and using Grub to dual boot the two.

---

### Post by David Delony on 2009-12-27
When you want to install a dual-boot Windows/Ubuntu machine, it's usually easier to install Windows first, then install Ubuntu. 

My only experience with dual-booting is installing Linux on a computer where Windows was already installed. I haven't run a Windows installation in a long time, but I think it might see the partition you want to install Windows on. Windows installs its own bootloader, and the Ubuntu partition might be unavailable. The Ubuntu CD does have tools to rebuild the MBR. 

This [wiki page]("https://wiki.ubuntu.com/IrcGuidelines") has more info. Before you proceed you should **back up your important files**.

---

### Post by lotusalive on 2009-12-28
I seem to be experiencing trouble with my Jaunty/Main repo not being installed currently, so that may be the reason I get this reply:
```
grub> find /boot/grub/stage1
 (hd0,6)

grub> root (hd0,6)

grub> setup /dev/sda

Error 11: Unrecognized device string

grub>

grub> setup (hd0,6)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,6)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,6)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,6) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

grub> 

```

But thanks for the info, and I can always try another time, when my install is working properly.

---

### Post by john newbuntu on 2009-12-28
Remember that should you need to restore the MBR from that file, use 446 as the block size and not 512 unless you want to overwrite the partition table.  Wont make a difference either way if partitions stay the same.

---

### Post by lotusalive on 2009-12-28
Thanks for that, John.  Apologize, since I can't visualize it, really.  Gave it try, to no avail, but at least it's here to refer to for future ref, when it will work, eventually I hope.
```
lightening@lightening-desktop:~$ dd if=/dev/hda of=/mbr.bin bs=446 count=1
dd: opening `/dev/hda': No such file or directory

```

---

### Post by john newbuntu on 2009-12-28
like zoot7 suggested, use sda instead on hda

---

### Post by lotusalive on 2009-12-28
Well, this is what I got...  Is this success in that Grub will now show up on my F10 Boot Menu ? ?  Is that what I'm aiming for to install W's ? ?

```
lightening@lightening-desktop:~$ sudo -i
[sudo] password for lightening: 
root@lightening-desktop:~# dd if=/dev/sda of=/mbr.bin bs=446 count=1
1+0 records in
1+0 records out
446 bytes (446 B) copied, 6.6064e-05 s, 6.8 MB/s
root@lightening-desktop:~# 
```

---

### Post by lavinog on 2009-12-28
> **lotusalive said:**
> Well, this is what I got...  Is this success in that Grub will now show up on my F10 Boot Menu ? ?  Is that what I'm aiming for to install W's ? ?

```
lightening@lightening-desktop:~$ sudo -i
[sudo] password for lightening: 
root@lightening-desktop:~# dd if=/dev/sda of=/mbr.bin bs=446 count=1
1+0 records in
1+0 records out
446 bytes (446 B) copied, 6.6064e-05 s, 6.8 MB/s
root@lightening-desktop:~# 
```

That command makes a backup of the master boot record of your master hard drive (sda) to a file /mbr.bin

It wont change grub.
Grub is needed for dual booting.
I have installed windows after installing Ubuntu...it is not a simple task if you don't understand partition tables.  What windows install disk do you have? Is it a software recovery disk that the computer manufacture supplied, or is it an actual windows installation disk that you purchased separately?
Recovery disks will usually wipe your ubuntu install.

---

### Post by lotusalive on 2009-12-29
Thanks lavinog.  It's not a recovery disk, wxpProSP1, purchased separately, as Dell T5088 came with v-word, and mfr emach, would not give me a recovery disk, after I told them I'd installed Linux...  (what else is new...)  And you're right, in that I probably don't understand the partition tables well enough to do it this way, w after ubu...  That's why I'm here begging the questions and asking :)

grub does not yet show up in the F10 Boot Choices, and as I recall, when we did have a Dual Boot, that is where it appeared.

---

### Post by lotusalive on 2010-01-08
Trying to do a bas-ackwards dual boot, tried to load xp including driver folder into an Archive in File System, but it said I don't have the right permissions to do this...  I have made a copy on my desktop of the emachine Drivers for this T5088 model, but I have no restore disk for the NTFS Partition.

Do I need to load xp into Ubu File System ?  If I do need to do that, can someone tell me HOW with Terminal ?  How do I get NTFS to SEE xp from disk ?

Sorry to be such a pain in the ****...  Thanks in advance for suggestions, knowledge, insights. :)

---

