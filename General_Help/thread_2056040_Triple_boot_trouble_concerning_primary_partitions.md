---
title: "Triple boot trouble concerning primary partitions"
date: 2012-09-10
forum: General Help
---

### Post by jamesisin on 2012-09-10
I currently have a lappy with Win7 and Ubu10.04.  This represents four primary partitions (Win7 requires two and Ubu has one for / and another for swap).  The trouble is that I can only have four primary partitions on a single drive.

What I'm trying to sort out is how might I arrange some extended partitions to make this triple boot possible?

Currently the partitions are thus: Win7 Sys | Win7 OS | [lots of empty space] | Ubu OS | Ubu extended with swap.

Suggestions?

---

### Post by jamesisin on 2012-09-10
Oh, and can 10.04 and 12.04 share the same swap space?

---

### Post by oldfred on 2012-09-10
Attach screenshot of gparted with the paperclip icon in the edit message panel above message.

You can share swap if you do not hibernate nor have encryption. You should be able to convert swap to a logical partition. If you delete swap and recreate, you will have to edit fstab with the new UUID.

You may be able to use this to convert a primary to a logical, but you have to follow all the rules on extended & logical partitions.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by jamesisin on 2012-09-11
Attached you will find a GParted screen from that machine (made using the live 12.04 CD).

Would I be able to put both swaps into the same extended?  Thereby allowing for hybernation?

Thanks for helping.

---

### Post by opensshd on 2012-09-11
Swap doesn't need its own partition, in fact, you don't need any swap at all - this will affect performance more or less depending on how much RAM you have installed.

You should be able to change swap partitions to a swap file on the same partition as the OS. 

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by oldfred on 2012-09-11
You are going to have to move sda3 all the way left, then move the start of the extended partition left to include all of the unallocated. Then you can create new logical partitions inside the extended partition. 

You can have as many swaps as you want. But Ubuntu boots pretty fast, and I do not find hibernation saves much boot time. Some do have issues with hibernation depending on what hardware you have.

---

### Post by jamesisin on 2012-09-11
Thanks, opensshd.  That will be useful moving forward.

OldFred - I'm moving the Ubu10 partition to the left now.  I'll expand the extended partition next.

Will the Ubu12 installer recognize that it can created its necessary partitions within the extended or is there another step prior to running the installer?

(I'm hoping when I install 12 & Grub that will fix all the moving/resizing issues as to partition locations.)

---

### Post by oldfred on 2012-09-11
If you are just moving partitions it still should boot. UUID should not change. Windows will not boot after a move until repaired. :)

I have not installed using any of the auto installs nor from CD for ages. I always partition in advance and have used USB flash or now use different hard drive to boot ISO.

But just to see what installer does I let it auto install. It found 40GB unallocated in the extended partition in sdc and just installed. I had a smaller unallocated also and would have preferred that it would choose that, but it worked. But I prefer the manual install so I can control partition sizes, locations, and boot drive. But I have several drives, so it is a bit more complex.


You may want a smaller system partition and create shared data partition(s). I have two shared data, one NTFS from when I still booted XP and another Linux formated.

---

### Post by jamesisin on 2012-09-11
It's all up and running now.  There were a couple of hiccups which I will lay out here for those who follow.

The installer did not offer to install into the empty space I had created by broadening the extended partition.  I had to create the necessary partitions manually and then explicitly point the installer to / and swap locations.

I thought that with the installation of 12.04 I would be using the Grub associated therewith for this system.  This turns out not to be the case; I am still running the Grub associated with 10.04.  I suspect this relates to the fact that 12 is wrapped inside that extended partition.  No real big thing; I'll just have to remain diligent about clearing out old kernels (from 10).

In the end my partitions look something like this:

```
Primary (WinSys) | Primary (Win7) | Primary (Ubu10) | Extended (Ubu12 | Swap10 | Swap12)
```

Thanks to you both for your assistance.

---

### Post by oldfred on 2012-09-11
Glad it worked out.

When you did manual install it should have given you a choice on where to install grub2's boot loader. If you did not install to MBR of drive then the old boot loader remained in the MBR.

If you want 12.04's grub to be in charge you just have to install it to the MBR. Its really just one line from terminal:

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
[COLOR=DarkRed]sudo grub-install /dev/sda[/COLOR]
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by jamesisin on 2012-09-12
Yep, that did it.  Not sure why that wasn't managed at installation but great to have it sorted.  Thanks.

---

