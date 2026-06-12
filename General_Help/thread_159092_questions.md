---
title: "questions"
date: 2006-04-12
forum: General Help
---

### Post by thunderfox933 on 2006-04-12
hello i have sevral questions

1. i am thinking about going back to ubuntu but last time i tryed to install it i couldnt boot into windows xp home edition because grub didnt detect it how could i make it detect it.

2. i have a 120gb harddisk how much space should i allocate to ubuntu.

3. What is a better file system ext3 or fat32. Are they resisten to fragments.

4. I might be getting a new computer. if i move the hdd to the new computer would ubuntu detect the hardware or will it malfucntion and i will have to reinstall windows and ubuntu.

5. last is this enough to run ubuntu

intel pentuim 3 933mhz 
512mb sd ram

---

### Post by Ubuntuud on 2006-04-12
That's a large HD for a P3. Ubuntu will run on it, but I don't think like a Breeze, but since XP probably wouldn't do so either... You should use ext3, I don't know anything about the fragmentation, but it is standard and there might be a reason for that.

---

### Post by Sef on 2006-04-12
> 1. i am thinking about going back to ubuntu but last time i tryed to install it i couldnt boot into windows xp home edition because grub didnt detect it how could i make it detect it.

It should detect it automatically.  If not, you'll need to set it up.

> 2. i have a 120gb harddisk how much space should i allocate to ubuntu.

How much do you want? (If the P3 can handle it.)

> 3. What is a better file system ext3 or fat32. Are they resisten to fragments.

FAT32 is for sharing with windows.   As for Linux either ext3 or reiser is fine.  No real worries about fragmentation with reiser; with ext 3 a small one if your writing a disertation where you keep on expanding the file.

> 4. I might be getting a new computer. if i move the hdd to the new computer would ubuntu detect the hardware or will it malfucntion and i will have to reinstall windows and ubuntu.

Yes, it should pick it up, May need to do some tweaking though.

> 5. last is this enough to run ubuntu

intel pentuim 3 933mhz
512mb sd ram

Yes, though if you find  it a bit slow, maybe xubuntu would be better.

---

### Post by intangir1999 on 2006-04-12
Thunder, the installation wizard should detect the partitions that are available on your computer.  Like most Linux Distros, the application detects available partitions and you are able to figure out whethere you want to use the current one (if you only have one partition this WILL replace any current OS on your system, so be sure when you install Ubuntu to have at least one or two EXTRA partitions).  

Basically what this brings us to is even before installing Ubuntu, you may already want to partition your hard drive into a different amount.  You said 120G, so try something like 80G and 40G, the 40G being the new partition.  If you want it split 60/60, you can do that too, but be sure to use a reliable partition software, Partition Magic is good (although I'm not sure where you'd get it, I think you can find it at Best Buy or Circuit City, places like that), the alternative to software like that is letting the Ubuntu installation wizard partition it for you, however you are not guaranteed to lose any sytem files when the virtual memory split occurs.  It's kind of like drawing a line in the middle of a room with no light, it may be right in the middle of the room, however who knows if you have stuff on both sides of the line that should only be on one side, Partition Magic exists because it will let you partition and not lose any system files.

Of course the dire and Linux savvy alternative is to just format your system, do the partition there.  I definitely warn against this unless you've done this before.  Make backups of everything on to CD or DVD.  Then once you've formatted the harddrive, run the Ubuntu installation CD, partition as needed, make sure you partition the drives to FAT32 file type.  Once the partition is made, get out of the installation, boot with your recovery disk, and make sure the installation occurs on the drive you want to use (usually always C:).  Please research this method, it will work if you have the actual Windows XP OS installation cd, but I'm not 100% sure about recovery disks since they may look for certain disk sizes, although I'd try it out anyway incase I am sure I have all the software on the recovery disks, or can do with out it.

Anyway, look up your options, best bet would be just to make backups of all your data, run defrag on your system, the run disk check (or chkdsk from DOS mode), then try running the install CD for ubuntu.  

Safest bet would just be to get another hard drive, maybe a cheap 30 or 40 gigger, and install ubuntu on that second one, if you really want to avoid partition in the first place.  Dual boot is the least of your problems when it comes to doing the least possible work on a system that has stuff you don't really want to mess with.

---

