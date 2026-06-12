---
title: "Please! Partition Table messed up!!"
date: 2011-01-17
forum: General Help
---

### Post by LuisAugusto on 2011-01-17
Here's the thing: I can't boot, I just got a grub rescue screen, which is completely useless.

From my Ubuntu LiveUSB I can perfectly access my NTFS partition (this is yhe only one I care for), so all my data is there, I used testdisk which discovered perfectly my partition setup, and I wrote it to the MRB, however, I still can't boot (maybe my ext4 is death, but I don't are), the biggest problem is I can't use gparted (it doesn't detect the partitions) so I can't re-install Ubuntu to get Windows 7 back using the GRUB.

Is not that I am more of a Windows user, but this is my mom's laptop, and she uses mostly windows and has all her info there.

I'm desesperated, all help will be welcomed

---

### Post by paddyS on 2011-01-17
Try using the windows rescue tool.  Scared the **** out of me using it the first time but I managed to totally rebuild my MBR having first booted from an XP CD.  I imagine the newer versions are the same.

---

### Post by LuisAugusto on 2011-01-17
This is the output from fdisk

```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf56e2efe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       25252   202624328+   7  HPFS/NTFS
/dev/sda3           25252       28163    23384064   83  Linux
/dev/sda4           28163       30402    17990154    f  W95 Ext'd (LBA)
/dev/sda5           28163       28295     1057784   82  Linux swap / Solaris
/dev/sda6           28295       30402    16924672    7  HPFS/NTFS

Disk /dev/sdb: 2099 MB, 2099249152 bytes
65 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 4030 * 512 = 2063360 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aaf85

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1017     2049224    b  W95 FAT32

```

The W95 Ext'd (LBA) and the Linux partition on top are probably lost, don't, again, I just want to be able to boot to Windows 7! 

May I ask what "windows rescue tool" are you speaking of? Thanks in advance.

From parted:
```
GNU Parted 2.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Error: Can't have a partition outside the disk!                           
(parted)    
```

---

### Post by LuisAugusto on 2011-01-17
Oh, I already see part of (hpoefully the whole) the problem (but I don't know how to fix it), two of my partitions there end on cylinder +1 the end of the physical hard drive, I guess if I could adjust them, I should be able to read disks with gparted, and format all but /dev/sda2 (where Windows 7 is), so I should be able to install Ubuntu, and select Windows 7 from the grub menu.

Could somebody tell if my assumptions are correct? And if such, could somebody tell how to do it?

---

### Post by Quackers on 2011-01-17
That's definitely the problem. Sda4 is an extended partition and it ends on cylinder 30402 (and so does sda6, which is a logical partition within that extended partition), but your disk only has 30401 cylinders.
Sadly, I too don't know how to fix it :-(
I'll do some searching!

---

### Post by LuisAugusto on 2011-01-17
Thank you so much!!

However, I already solved it, since I didn't care about the partitions on the extended one (because they were quite fresh, every bit of important information was on the Windows 7 partitions, thankfully), what I did was simple enough, I got rid of them using fdisk XD:

```
fdisk /dev/sda
```

Then I used the "d" option to delete a partition, and selected "4", so all the problems poofed away with it, then I could normally install UBuntu, and I'm writing this from Windows, man, for a moment I really got scared!

Again, thank you for helping me out =)

---

### Post by Quackers on 2011-01-17
Excellent! :-)
I'm surprised that fdisk could just delete it, but happy :-)

---

### Post by LuisAugusto on 2011-01-18
> **Quackers said:**
> Excellent! :-)
I'm surprised that fdisk could just delete it, but happy :-)

Thanks you, I'm happy too. I guess fdisk could delete it because it only actually deletes it from the MBR, the partition is left untouched (I'm just guessing). Actually, I thought about what my mom had there (and there wasn't anything important) because I thought about the possibility of writing down the exact parameters of the partitions, and then just using the last partition of all (/dev/sda6) and then playing with testdisk, or maybe even foremost to recover my whole original Ubuntu installation, or data from it.

I'm just so happy everything went right, my mom had extremely important information there (work documents, clients archives, etc).

---

### Post by srs5694 on 2011-01-18
FWIW, [this Web page of mine](http://www.rodsbooks.com/missing-parts/index.html) describes how to fix the problem of the too-big extended partition without deleting all your partitions. TestDisk (or at least some versions of it) seems to have a bug that causes it to create this problem. I'm reluctant to recommend it any more because of this bug.

Are you now able to boot Windows? If so, you might mark the thread as solved. If not, then this is basically a Windows-only computer now, so you might want to post a query in a Windows forum; the people there are more likely to know their way around Windows recovery tools.

---

### Post by Dvilef on 2011-01-18
i have a question I have a toshiba Satellite l355-s7902

250GB (5400 RPM) Serial ATA hard disk drive.


i trying to install 10.10 , i have a live cd, problem that i have is the installer is not reckonizing the harddrive,  

when i try to install it tells me that i have , 2.8 gb of space, that  must be the ram, i checked the hard drive , it is secure in place, i  tried to also install other versions , nothing, same thing with all,  installers can find harddrive, is thier anything i can do to fix this  problem , with live cd, not sure how to get 10.10 to find my hard drive,  i research a little, some thing about the kernel, needing something, or  i could flash bios , or may be it's the harddrive, in some of the other  live cd i have tried 8.10 i get a black screen with a list of commands ,  im not sure what command would work , can somebody help

i also went in to bios using the f2 key and change for achi to compatitlity, it didn't help 

my desktop is 2 years old it reads the ram but not the harddrive

sorry to reply to this thread not sure how to make my own

---

### Post by LuisAugusto on 2011-01-19
> **srs5694 said:**
> FWIW, [this Web page of mine](http://www.rodsbooks.com/missing-parts/index.html) describes how to fix the problem of the too-big extended partition without deleting all your partitions. TestDisk (or at least some versions of it) seems to have a bug that causes it to create this problem. I'm reluctant to recommend it any more because of this bug.

Are you now able to boot Windows? If so, you might mark the thread as solved. If not, then this is basically a Windows-only computer now, so you might want to post a query in a Windows forum; the people there are more likely to know their way around Windows recovery tools.

Thank you very much for your help, yes, I'm able to boot Windows perfectly, I just installed Ubuntu in space of the old extended partition and then grub did the trick(I could've just install the grub, but I'm really into Linux, I been using it almost exclusively for years now, around 7-8 years, in fact, my own computer only has Ubuntu, in the past, I was more of an OpenSUSE user, but as time passed I felt better with this distro, specially, because of the huge amazing community, from help in the forums to ppa and tutorials).

Once again, thanks for the help, and I will bookmark your web for future reference!


> **Dvilef said:**
> i have a question I have a toshiba Satellite l355-s7902

250GB (5400 RPM) Serial ATA hard disk drive.


i trying to install 10.10 , i have a live cd, problem that i have is the installer is not reckonizing the harddrive,  

when i try to install it tells me that i have , 2.8 gb of space, that  must be the ram, i checked the hard drive , it is secure in place, i  tried to also install other versions , nothing, same thing with all,  installers can find harddrive, is thier anything i can do to fix this  problem , with live cd, not sure how to get 10.10 to find my hard drive,  i research a little, some thing about the kernel, needing something, or  i could flash bios , or may be it's the harddrive, in some of the other  live cd i have tried 8.10 i get a black screen with a list of commands ,  im not sure what command would work , can somebody help

i also went in to bios using the f2 key and change for achi to compatitlity, it didn't help 

my desktop is 2 years old it reads the ram but not the harddrive

sorry to reply to this thread not sure how to make my own

That's a weird problem. Maybe you could run the live CD and run GParted and tell us what you see, also, you could put the output of the following command:

```
sudo fdisk -l
```

---

### Post by Quackers on 2011-01-19
> **Dvilef said:**
> i have a question I have a toshiba Satellite l355-s7902

250GB (5400 RPM) Serial ATA hard disk drive.


i trying to install 10.10 , i have a live cd, problem that i have is the installer is not reckonizing the harddrive,  

when i try to install it tells me that i have , 2.8 gb of space, that  must be the ram, i checked the hard drive , it is secure in place, i  tried to also install other versions , nothing, same thing with all,  installers can find harddrive, is thier anything i can do to fix this  problem , with live cd, not sure how to get 10.10 to find my hard drive,  i research a little, some thing about the kernel, needing something, or  i could flash bios , or may be it's the harddrive, in some of the other  live cd i have tried 8.10 i get a black screen with a list of commands ,  im not sure what command would work , can somebody help

i also went in to bios using the f2 key and change for achi to compatitlity, it didn't help 

my desktop is 2 years old it reads the ram but not the harddrive

sorry to reply to this thread not sure how to make my own

You will get a better response if you start your own thread.
Near the top left of the main forum page is a brownish tab with white writing that says "new thread". If you click on that you can type away :-)
It would help if you could include the output of the boot script in your thread, as described below.
From the live cd/usb desktop, if necessary, please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

