---
title: "Backup/Restore strategy in Ubuntu - advice needed."
date: 2010-08-04
forum: General Help
---

### Post by jlunse on 2010-08-04
Let's say my main disk crashes and I have to replace it. Now I want to restore "**everything**" as it was before the crash.
Also remember, I still have a dual boot with Win XP Media Center Edition (promise, that I rarely or never use it... maybe, no need with the superb Ubuntu 10.04 LTS *Lucid Lynx*:) ...but still want to keep XP stuff for sentimental reasons, or something like that.) 
There are several nice guidelines on how to backup and restore Ubuntu with tar and bz2 but I'm still not sure that it covers my needs, ... me being such a _beginner_ in Linux.
So, I have three questions?
For example:
[LIST]

[*]*They advice me to exclude directories like proc, lost+found, mnt, mnt, sys
***What kind of information will I loose - from a beginners "point of view"?***

[*]*They advice me to restore GRUB when I move the system to another disk.
***Is my dual boot with with WinXP MCE now removed?***
[/LIST]

***Could you think of any backup/restore procedure that safely takes me back to my dual boot system on a newly installed disk?***
*...or should I reconsider my dual boot system and focus on backup/restore only Ubuntu?*

---

### Post by cariboo on 2010-08-04
I've used [Clonezilla]("http://clonezilla.org/"), with great success, it allows you to create images of partitions and/or disks The big draw back is that you have to boot the clonezilla live CD/USB in order to use it.

---

### Post by jlunse on 2010-08-04
[Clonezilla]("http://clonezilla.org") sounds like the perfect solution for me.
But I'm not sure I understand the drawback where you have to boot with it. Could you give more details?

Also which version do you use: [Clonezilla Live]("http://clonezilla.org/download/sourceforge/") (Alternative stable - Ubuntu-based?)

---

### Post by cariboo on 2010-08-04
I personally use grsync, which I can run while I'm doing other things. With Clonezilla, you have to stop what you are doing and reboot the system, then boot the Live CD/USB.

I only back up my home directory, as it takes so little time to do a re-install. I run the development version of Ubuntu, so re-installs are a fact of life. :)

---

### Post by Maverick_Meerkat on 2010-08-04
I have three partitions on my drive.
1. for Ubuntu (my default OS) 
2. for XP Pro (just in case)
3. for my data, docs, music etc. 

I also have two external HDD. I simply boot to XP then drag and drop the contents of Ubuntu partition to the external. To restore I simply drag and drop from the external to the Ubuntu partition.

You could use a similar strategy to copy your Ubuntu folder and wubildr, wubildr.mbr and boot.ini to a separate partition, an external HDD, or even burn it to DVD. Of course, to fit on a DVD your Ubuntu install must be smaller that 4.7 gigs.

This may not be the best or most elegant way of doing things, but it works well for me. I only submit this for your consideration. It is a possibility. Perhaps, it will spark an idea that is perfect for your particular situation/needs.
;)

---

### Post by jlunse on 2010-08-04
Sounds to good to be true for my scenario, or? Consider my initial scenario where my internal (master) disk crashes and I want to do a complete restore of my dual boot with Ubuntu and WinXP on a **_new empty HDD_**.
How do I copy from the external HDD to the newly installed HDD without a OS?

p.s. I had more or less the same configuration as you but where #3 (the external HDD with all my music/data and stuff crashed last week). Really sad but still happy that it wasn't my main (master) HDD.

---

### Post by jlunse on 2010-08-04
cariboo907, I understand that you are a Ubuntu developer and probably don't have a dual boot configuration with XP and backup/restoring your home directory is a simple daily task for you. But, I don't even know where my "home directories" are?
Again, consider my initial scenario where I have a dual boot config and where my main (master) HDD crashes...and where I want to restore everything. I guess it isn't possible, but I just want to know. I have two computers with Ubuntu 10.04, today. My computer and my daughter's and I don't want to end up in a situation where I have to reinstall all programs and hours of tuning in both Ubuntu and XP, again because of a disk crash.
So, I'm not sure if grsync is the best strategy for me.

---

### Post by Maverick_Meerkat on 2010-08-04
> **jlunse said:**
> Sounds to good to be true for my scenario, or? Consider my initial scenario where my internal (master) disk crashes and I want to do a complete restore of my dual boot with Ubuntu and WinXP on a **_new empty HDD_**.
How do I copy from the external HDD to the newly installed HDD without a OS?

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

A hard drive failure is a different situation all together. Unless you are using a Maxtor HDD, it's rare that any physical defect will arise. A physically damaged drive is the only instance that makes data recovery difficult. A typical or simple crash is software related and it's fairly easy to recover the data. With that said...

In the scenario where you need to copy your original to a new hard drive, the easiest solution is to use software that clones the partition, or will image the complete drive. Typically, you can use that software on CD to write a duplicate to a new drive.

However, using my method you must partition & install Windows (what a drag). Then you simply drag and drop the Ubuntu folder to the proper partition then drag and drop the wubildr, wubilr.mbr, and boot.ini to C:\ directory.

Of course, in my case I booted to Ubuntu and copied the XP partition to the external as well. So I can use the same process to restore XP by booting to Ubuntu.

Like I said... "This may not be the best or most elegant way of doing things, but it works well for me." It's just something that might inspire thought about creative alternatives.

---

### Post by bodhi.zazen on 2010-08-04
Moved to general help.

Personally, IMO, OS are easy to install and configure. I keep a /data partition and back up the data. 

Keeping the data separate from the OS has a number of advantages. It is much easier to back up , backups are smaller, and you can reinstall an OS without data loss.

---

### Post by jlunse on 2010-08-06
> **bodhi.zazen said:**
> Moved to general help.

Personally, IMO, OS are easy to install and configure. I keep a /data partition and back up the data. 

Keeping the data separate from the OS has a number of advantages. It is much easier to back up , backups are smaller, and you can reinstall an OS without data loss.

Yes, installation of Ubuntu is easy to re-install and I don't think I will need XP anymore. Data like photos, music files and all downloaded stuff could also be easily backed up, no problem. But I'm a ordinary user (not a developer) of Ubuntu, and with a lot of small user tweaks in GUI, interface settings, program installations (packages). Is there any easy way to back up that stuff?
I don't want to redo all these settings and installations again.

---

### Post by Quackers on 2010-08-06
These backup methods all sound fine when you can boot into the OS. The problems arise when you can't boot - for whatever reason. I would have thought that a cloned image of the drive/partitions with a bootable live cd would be the best option. Unfortunately, as I have found to my cost, most backup images don't work with a raid system and some won't restore in AHCI SATA mode.
Could someone confirm that Clonezilla works in AHCI please? It sounds like the right option for me :-)

---

### Post by bodhi.zazen on 2010-08-06
> **jlunse said:**
> Yes, installation of Ubuntu is easy to re-install and I don't think I will need XP anymore. Data like photos, music files and all downloaded stuff could also be easily backed up, no problem. But I'm a ordinary user (not a developer) of Ubuntu, and with a lot of small user tweaks in GUI, interface settings, program installations (packages). Is there any easy way to back up that stuff?
I don't want to redo all these settings and installations again.

IMO, by far the easiest method is to use a separate /home partition.

---

