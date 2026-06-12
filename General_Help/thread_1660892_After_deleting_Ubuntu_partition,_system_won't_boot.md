---
title: "After deleting Ubuntu partition, system won't boot! Need urgent help!"
date: 2011-01-06
forum: General Help
---

### Post by Appleallie on 2011-01-06
I dual booted Ubuntu and Windows 7 for a while but after doing all schoolwork on windows 7 I decided to delete Ubuntu. A friend had partitioned my harddrive and installed Ubuntu and everything. 
I went into disk (or maybe it was drive) manager and I deleted the partitions for
Ubuntu and reallocated the unallocated space to drive C. 
After restartting it won't boot anymore and I get a "error: no such partition. (next line) grub rescue>"
please please please someone help 
I really don't know much about Linux and computers. Sp
Please describe a step by step process that I can do. 
I currently only have a Windows 7 64bit recovery disk. That's
It.
[it's options are: "startup repair"(tried this, it found mp
Errors) system restore (said there was an error and it
Couldnt do it) system image recovery (I've never made a system image) and I
Can pull up a comman prompt. That's about it.]

I do have a working computer at home that can be used Tp download and
Burn anything else to a disk I might need. 

Please I REALLY need help before I go back to school!
Thank you, I appreciate the help you can give me!

---

### Post by xcorpion on 2011-01-06
hi
i just step in
i m having a problem with my hp compaq cq41-208au
i was using win7 and then i install ubuntu 10.10 via internet.
after installing ubuntu it asks me for update and i accept it buh after it also ask me smthng grub and didnt notice what it says and just click restart
after i got a screen which says 
error : no such device : bed4e5bc-7d2e-486e-a365-14e5de8d236c
grub rescue>

<Note: i have two partitions sda1 sda2 both are HPFS/NTFS
and my win7 is install in sda1 and ubuntu in sda2 and sda1 is boot*

help me out plz i m f**K freakin out with this prob

---

### Post by wilee-nilee on 2011-01-06
> **xcorpion said:**
> hi
i just step in
i m having a problem with my hp compaq cq41-208au
i was using win7 and then i install ubuntu 10.10 via internet.
after installing ubuntu it asks me for update and i accept it buh after it also ask me smthng grub and didnt notice what it says and just click restart
after i got a screen which says 
error : no such device : bed4e5bc-7d2e-486e-a365-14e5de8d236c
grub rescue>

<Note: i have two partitions sda1 sda2 both are HPFS/NTFS
and my win7 is install in sda1 and ubuntu in sda2 and sda1 is boot*

help me out plz i m f**K freakin out with this prob

Please start your own thread.:) Actualy sounds like a wubi install look at this link and solution 1.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by wilee-nilee on 2011-01-06
> **Appleallie said:**
> I dual booted Ubuntu and Windows 7 for a while but after doing all schoolwork on windows 7 I decided to delete Ubuntu. A friend had partitioned my harddrive and installed Ubuntu and everything. 
I went into disk (or maybe it was drive) manager and I deleted the partitions for
Ubuntu and reallocated the unallocated space to drive C. 
After restartting it won't boot anymore and I get a "error: no such partition. (next line) grub rescue>"
please please please someone help 
I really don't know much about Linux and computers. Sp
Please describe a step by step process that I can do. 
I currently only have a Windows 7 64bit recovery disk. That's
It.
[it's options are: "startup repair"(tried this, it found mp
Errors) system restore (said there was an error and it
Couldnt do it) system image recovery (I've never made a system image) and I
Can pull up a comman prompt. That's about it.]

I do have a working computer at home that can be used Tp download and
Burn anything else to a disk I might need. 

Please I REALLY need help before I go back to school!
Thank you, I appreciate the help you can give me!

Do you have a Ubuntu disc if not download one we need to look at your set up with a script, it is in my signature the bootscript.

Edit: I will be online for a a while if you need some guidance or have any questions. There are others as well who can help.
This sort of fix though with errors being thrown a a vague description of the Ubuntu removal eg how exactly makes this a little more difficult. You wouldn't want advise that bricks the W7 if it isn't already.

---

### Post by djjerky on 2011-02-22
Hey, I just fixed the same problem on my pc. Here is a step by step guide that should work for you.

1. Insert and boot from your recovery disk.
2. Set your language options, and then Click on Repair your computer.
3. It should detect your windows 7 installation. Select your installation and click next.
4. Click on the Command Prompt option.
5. Type in "diskpart" to load the windows partition editor.
6. Type in the following commands:

list disk
select disk 0
list partition
select partition 1
active
exit

Here, the command "list disk" will list all of the hard disks attached to your computer. "select disk 0" will tell diskpart what disk to select. You need to substitute 0 with the disk that contains your windows installation. "list partition" will list all the partitions on the selected disk. "select partition 1" will tell diskpart what partition to use. You will need to replace 1 with the 100 mb partition that contains your windows boot loader. "active" will make the selected partition on the selected disk the active boot partition. "exit" will exit diskpart.

7. Back in the command prompt window, type in

bootrec.exe /fixmbr
bootrec.exe /fixboot
bootrec.exe /rebuildbcd

These commands will place the windows boot loader back into the MBR and boot sector of your hard drive. the rebuildbcd switch will re-detect your windows installations, and add the appropriate entries to the windows boot loader. 

8. Remove the windows repair disk and reboot your computer.
9. Enjoy your windows :)

---

### Post by Quackers on 2011-02-22
The /fixmbr instruction should work, but the diskpart instructions will make partition 1 on the first hard drive the active partition. This is fine if Windows boot files are on that partition, but not so good if they're not there!

---

### Post by azonirunner on 2012-03-09
> **djjerky said:**
> Hey, I just fixed the same problem on my pc. Here is a step by step guide that should work for you.

1. Insert and boot from your recovery disk.
2. Set your language options, and then Click on Repair your computer.
3. It should detect your windows 7 installation. Select your installation and click next.
4. Click on the Command Prompt option.
5. Type in "diskpart" to load the windows partition editor.
6. Type in the following commands:

list disk
select disk 0
list partition
select partition 1
active
exit

Here, the command "list disk" will list all of the hard disks attached to your computer. "select disk 0" will tell diskpart what disk to select. You need to substitute 0 with the disk that contains your windows installation. "list partition" will list all the partitions on the selected disk. "select partition 1" will tell diskpart what partition to use. You will need to replace 1 with the 100 mb partition that contains your windows boot loader. "active" will make the selected partition on the selected disk the active boot partition. "exit" will exit diskpart.

7. Back in the command prompt window, type in

bootrec.exe /fixmbr
bootrec.exe /fixboot
bootrec.exe /rebuildbcd

These commands will place the windows boot loader back into the MBR and boot sector of your hard drive. the rebuildbcd switch will re-detect your windows installations, and add the appropriate entries to the windows boot loader. 

8. Remove the windows repair disk and reboot your computer.
9. Enjoy your windows :)

Thank you for the instructions.  This just saved me a few hours of reinstallation.  :)

---

### Post by CaseyC on 2012-03-09
Had this issue a long time ago, although I think I followed similar steps above but what I ended up doing is running a Windows 7 repair from the W7 disk and that fixed the issue. 

That was just an fyi for everyone :)

---

### Post by efalzon on 2013-02-11
Still works in 2013! Thanks DJ!!

> **djjerky said:**
> Hey, I just fixed the same problem on my pc. Here is a step by step guide that should work for you.

1. Insert and boot from your recovery disk.
2. Set your language options, and then Click on Repair your computer.
3. It should detect your windows 7 installation. Select your installation and click next.
4. Click on the Command Prompt option.
5. Type in "diskpart" to load the windows partition editor.
6. Type in the following commands:

list disk
select disk 0
list partition
select partition 1
active
exit

Here, the command "list disk" will list all of the hard disks attached to your computer. "select disk 0" will tell diskpart what disk to select. You need to substitute 0 with the disk that contains your windows installation. "list partition" will list all the partitions on the selected disk. "select partition 1" will tell diskpart what partition to use. You will need to replace 1 with the 100 mb partition that contains your windows boot loader. "active" will make the selected partition on the selected disk the active boot partition. "exit" will exit diskpart.

7. Back in the command prompt window, type in

bootrec.exe /fixmbr
bootrec.exe /fixboot
bootrec.exe /rebuildbcd

These commands will place the windows boot loader back into the MBR and boot sector of your hard drive. the rebuildbcd switch will re-detect your windows installations, and add the appropriate entries to the windows boot loader. 

8. Remove the windows repair disk and reboot your computer.
9. Enjoy your windows :)

---

### Post by wildmanne39 on 2013-02-11
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

