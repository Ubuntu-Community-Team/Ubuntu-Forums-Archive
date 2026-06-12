---
title: "Installing on an NTFS partition not used by Windows"
date: 2009-07-17
forum: General Help
---

### Post by futuroimperfetto on 2009-07-17
Hello,

 I would like to install Ubuntu on a 2005 Sharp laptop that comes with Win XP and no installation disk for it. There is a hidden partition that allows one to reinstall Windows from inside the hard drive.

The current setup is: 5GB hidden partiton (FAT32), 30GB for C: and 30GB for D: (both NTFS formatted). D: is really empty. It's a second partition where one can put stuff.

I would like to know if it is doable to format D as 29GB ext3 and 1GB swap. I would guess that Windows will stop seeing D:, but this laptop will get a dual boot with 30GB dedicated to Ubuntu.

NOTICE: I have no WinXP installation disk and I prefer not to kill XP altogether on this machine. Moreover, we tried Wubi which works, but makes the machine become incredibly slow with time (both on Ubuntu and on XP).

Does anyone have a better idea on how to make this machine into a dual boot? Am I doing something dangerous/wrong by re-formatting NTFS into ext3? I have some doubts that, if this plan won't work out, the hidden partition will not know how to restart altogether when it sees an ext3 partition.

Thanks!

---

### Post by cholericfun on 2009-07-17
Youre right - windows is ignorant of ext3,
but that jsut means that after installing ubuntu, windows won't know theres a D partition.
so no problems there... apart from wanting to see data from windows from your ext3 partition, if that is important i "think" there is some program out there to explain to windows what ext3 is...

---

### Post by coffeecat on 2009-07-17
What you suggest seems eminently reasonable to me, with a couple of caveats.

> **futuroimperfetto said:**
> The current setup is: 5GB hidden partiton (FAT32), 30GB for C: and 30GB for D: (both NTFS formatted). D: is really empty. It's a second partition where one can put stuff.

This probably means that you have three primary partitions as follows:

#1 - 5GB hidden
#2 - Windows C:
#3 - Windows D:

... which, to Linux, would appear as sda1, sda2, sda3.

So, because you cannot have more than 4 primary partitions, I would suggest you do the following.

Boot up with the Ubuntu live CD and go to System > Administration > Partition Editor (Gparted). Make sure it shows the partition layout (more or less) as I have described. If it doesn't, post back. If it does, use Gparted to delete Windows D:/sda3. Now create an extended partition in the space left by the deleted D:. In the extended partition, create your two Linux partitions - ext3 for the root partition and also the swap partition.

Now, when you are ready to install, choose 'manual' at the partitioning stage and point the installer at your new ext3 partition for the root (/) partition. It will pick up the swap one automatically.

The reason I suggest this is that it gives you some flexibilty for the future, which four primary partitions would not. Note that, unlike Windows, Linux can quite happily boot from a logical partition.

> **futuroimperfetto said:**
> I would guess that Windows will stop seeing D:, but this laptop will get a dual boot with 30GB dedicated to Ubuntu.

Well - the 30GB will no longer be "D:" (drive letters are a Windows-only convention), and you would have to install a Windows ext2/3 driver for it to read/write your Ubuntu root partition - although, personally, I would not do this. And, yes, you'll get a perfectly good dual-boot.

> **futuroimperfetto said:**
>  NOTICE: I have no WinXP installation disk and I prefer not to kill XP altogether on this machine.

In which case, may I recommend the following proprietary, but free, software?

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

It's really very good indeed. You can save an image of your C: drive to an external drive and use that to restore Windows if your C: drive becomes corrupted. It's as good as other paid-for imaging software. **EDIT:** ... and with Macrium, you create a...

> Linux based Rescue CD with Network access and full GUI.                        Only 6.5MB in size!

...for restoring Windows! What a wonderful irony. :) Linux to the rescue, yet again. 

> **futuroimperfetto said:**
> I have some doubts that, if this plan won't work out, the hidden partition will not know how to restart altogether when it sees an ext3 partition.

I would hope that the hidden partition would simply restore Windows to its factory state in the C: partition. I doubt whether the presence of an ext3 partition would confuse it. At worst, it would probably see it as a broken partition (since it wouldn't recognise the filesystem) and reformat it for you - possibly without asking first! :(

Happy Ubuntu-ing!

---

### Post by futuroimperfetto on 2009-07-17
Dear cholericfun and coffeecat,

 Thank you for your very detailed answers! Unfortunately, I will not be able to play it over the weekend, but I actually wanted to know more about it.

> **coffeecat said:**
>  This probably means that you have three primary partitions as follows:

#1 - 5GB hidden
#2 - Windows C:
#3 - Windows D:

... which, to Linux, would appear as sda1, sda2, sda3.

So, because you cannot have more than 4 primary partitions, I would suggest you do the following.

Wow. This explains a lot! I have been tinkering with the Ubuntu partitioner, precisely deleting D and replacing it with a swap partition, then / and then /home and it wouldn't let me, because you cannot have more than 4 primary partitions!

Creating both / and /home is a thing a friend of mine suggested to me some time ago and it makes sense on another machine I have, but not here.

So, like you suggested, I will have Gparted remove D and format it into ext3 and a swap area.

> **coffeecat said:**
> 
Linux can quite happily boot from a logical partition.

Ahem, I never tried putting logical. What does that mean? Sorry for the trivial question.

OK, I will work on this thing as soon as I can (hopefully, Monday) and post back what happens. It's good to know there is free software to take snapshots of the Windows hard drive.

Thanks again for this description!

Cheers

---

### Post by coffeecat on 2009-07-17
> **futuroimperfetto said:**
> Ahem, I never tried putting logical. What does that mean? Sorry for the trivial question.

No problem. Instead of one of your primary partitions you can have one (but one only per hard drive) extended partition. This is simply a container for a number of logical partitions. It's a way of getting round the 4 primary partition limitation - which dates back to MS-DOS days. I can't remember the limit for the number of logical partitions you can make, but it's much more than you're ever likely to need - dozens rather than a handful.

Anyway - in Gparted, first create an extended partition to fill all the free space you create by deleting the old D: partition. Then highlight the extended partition, click on 'new', adjust the size to what you want, make sure you've got the right filesystem selected (it defaults to ext2, which you don't want) and you should be able to make your first logical partition. Simply repeat for the other partition(s).

In Linux, you can tell which is a logical partition from its device number. Primary and extended partitions are numbered sda1 through sda4. Logical partitions are numbered sda5 and upwards. (Or sdb1, sdb5, etc in the case of a second hard drive, sdc for a third, and so on.) So, in your case, the hidden and Windows C: partitions are probably sda1 and sda2. When you create the extended partition, that will become sda3, and the two logicals will be sda5 and sda6. Or they will be if there are only three partitions. If there's another hidden one tucked in there (Dell are notorious for odd hidden partitions), then the numbering may be different.

As far as a separate /home is concerned, you might want to consider this. Some people find this useful, although I don't bother. You simply create three logical partitions in the extended partition.

---

### Post by ronaldprettyman on 2009-07-17
> **futuroimperfetto said:**
> Hello,

 I would like to install Ubuntu on a 2005 Sharp laptop that comes with Win XP and no installation disk for it. There is a hidden partition that allows one to reinstall Windows from inside the hard drive.

The current setup is: 5GB hidden partiton (FAT32), 30GB for C: and 30GB for D: (both NTFS formatted). D: is really empty. It's a second partition where one can put stuff.

I would like to know if it is doable to format D as 29GB ext3 and 1GB swap. I would guess that Windows will stop seeing D:, but this laptop will get a dual boot with 30GB dedicated to Ubuntu.

NOTICE: I have no WinXP installation disk and I prefer not to kill XP altogether on this machine. Moreover, we tried Wubi which works, but makes the machine become incredibly slow with time (both on Ubuntu and on XP).

Does anyone have a better idea on how to make this machine into a dual boot? Am I doing something dangerous/wrong by re-formatting NTFS into ext3? I have some doubts that, if this plan won't work out, the hidden partition will not know how to restart altogether when it sees an ext3 partition.

Thanks!
NTFS is not in the kernel, there is a hack to do this, but your better off installing to Ext3 and installing the Ext2 drivers for windows if you want to access your linux files from windows. Rather then install linux to ntfs. Though this one project that does this and runs very stable Topologilinux might be worth a shot as you don't have to repartition to run it and its fairly stable. At least it was the last time I ran it back in 2005 or so. It installs  to an image on an ntfs file system and is based on slackware and but might a be little more intimating then ubuntu. And your have a heck of a time viewing your files in windows natively. The best options is probably just ext drivers for xp. Google it.

---

### Post by futuroimperfetto on 2009-07-23
Hi all,

 I've done it. I've changed D into an ext3 (root /) + swap area and placed Ubuntu side by side with Windows. It looks like everything went well, except for one thing.

I did not touch the hidden partition as I wanted to keep it in case I wanted to reinstall Windows. Now I cannot use it as GRUB starts immediately after the BIOS and I have no access to it. GRUB only allows me to boot into WinXP or Ubuntu.

It used to be that it asked me if I wanted to start it right after the BIOS startup (by pressing an F-key, can't remember which now).

From the LiveCD I can see that the hidden partition is still there, but I cannot use it. Any idea on how I can get it back to work? Can I edit GRUB somehow?

Thanks!

---

### Post by coffeecat on 2009-07-24
> **futuroimperfetto said:**
> From the LiveCD I can see that the hidden partition is still there, but I cannot use it. Any idea on how I can get it back to work? Can I edit GRUB somehow?

Yes, this should be possible. If you add an entry to grub's menu.lst similar to the Windows stanza (but with a different root line and title), that should work. I say "should" because that works for the hidden partitions I've experience of, but Sharp may just have done something differently.

Anyway, to see what needs to be done, boot into Ubuntu, open a terminal and post the output of:

```
sudo fdisk -l
```You can copy and paste from the terminal (but use shift+ctrl+C for copy), but please put the output into [noparse]```
  
```[/noparse] tags otherwise it's difficult to read.

Also, post the contents of your /boot/grub/menu.lst file. With those I can give you the extra entry for menu.lst.

> **futuroimperfetto said:**
> It looks like everything went well, except for one thing.

I did not touch the hidden partition as I wanted to keep it in case I wanted to reinstall Windows. Now I cannot use it as GRUB starts immediately after the BIOS and I have no access to it. GRUB only allows me to boot into WinXP or Ubuntu.

It used to be that it asked me if I wanted to start it right after the BIOS startup (by pressing an F-key, can't remember which now).

That's curious. The mbr must have been passing control to whatever bit of code was prompting you for the hidden partition rather than straight to the Windows NTLDR, which is usually the case. Grub stage 1 replaces the mbr, you see. Anyway, it might be an idea to double-check the laptop documentation for the F-key combination, so you can use that as a fallback in case the grub edit doesn't work for whatever reason. If you've mislaid the user manual, or never had one in the first place, you might be able to download a pdf from the Sharp website - if their customer support is any good, that is.

---

