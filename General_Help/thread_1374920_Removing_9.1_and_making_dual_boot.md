---
title: "Removing 9.1 and making dual boot"
date: 2010-01-07
forum: General Help
---

### Post by johnhdsi on 2010-01-07
Hi everyone,
I have my pc setup with 2 hard disks, my main HD is running Win XP and the second HD is loaded with 9.1, the disk I loaded 9.1 on is a 40 gig HD, I wanted to try out 9.1 as a clean install before mucking around with dual boot. I really like 9.1 and now I want to change the way I am setup so I can run a dual boot. Right now the way it is I go through GRUB to choose either linux or win, it defaults to Linux, I removed the disk the 40 gig drive the other day and when I do I can't boot up, I get an error message telling me something like Grub not found (Duh right I took the HD out) I want to reset my comp so the 40 gig drive is visible to win and do the dual boot with 9.1 inside of windows. 

My questions are this.
1. How would change the current boot config. so that windows loads and I don't have to use GRUB to choose my O/S.

2. How would I go about removing 9.1 from the 40 gig drive and leaving it blank so I can utilize it for windows.

my main concern here is getting the pc set back up so I can boot into windows without using the GRUB menu, I'm on my work pc and getting some greif from my boss on this. I'm worried that if I just remove 9.1 from the 40 gig drive that I won't be able to load windows, like when I physically removed the HD from the pc.

Any ideas or walk throughs would be most appreciated.

Thanks in advance!!!
John

---

### Post by synapsys on 2010-01-07
You can restore the win xp boot loader by booting the xp cd and choose to repair current installation. Then at command prompt run```
fixmbr
```Then you can plug the 2nd hard drive back in and format it from inside windows.

---

### Post by pedro_orange on 2010-01-07
You can actually alter the GRUB to have a different default; so if you wanted it to boot Windows by default then you could just change it in the GRUB config.

However; if you really want to wipe the second drive. You could probably do this in Windows in Disk manager. Or you could use GParted or something.

You may need to restore your Windows boot loader (from your recovery disk I imagine) if you want to get rid of the GRUB.

---

### Post by johnhdsi on 2010-01-07
Here's the only problem I have, my comp never came with a recovery disk. It uses a partition on the main drive as recovery. How would I edit GRUB to change the boot order? 

I can't see the second drive from win, so I can't use any windows utilities to modify the drive. If I was to completly remove 9.1 from the 40 gig drive would GRUB still be there in the boot menu?

---

### Post by johnhdsi on 2010-01-07
Ok, I found a thread to edit the GRUB Menu so windows boots as default. At this point I would like to dump 9.1 from the 40 gig drive and use it as a windows drive, then re-install 9.1 as dual boot. So how would I go about removing 9.1 from the 40 gig drive and making it a windows drive without using a boot disk ( I don't have one )

---

### Post by pedro_orange on 2010-01-08
Just use something like GParted to format it. 

Or you could just boot into Windows (You might need to install an Ext3/4 driver depending on the file system) and format it through Disk Manager.

---

### Post by johnhdsi on 2010-01-08
How do I boot up gparted? I tried sudo gparted in terminal but got nothing and I don't see it in any of the drop down menus. I'm sorry to keep bugging with this stuff I'm just a noob with partitions and disk managment stuff. Once I format through Gparted the disk will be blank yes? At that point when I boot into windows I shouldn't have any grub loader and I can format the disk as a win volume right? My final end goal here is to wipe the 40 gig drive and have it as a 2nd drive for windows, then re-install 9.1 as a dual boot. I just ran out of space to quickly on the 40 gig drive. 

Thanks for putting up with me
John

---

### Post by pedro_orange on 2010-01-11
Hi sorry for the lateness in the reply.

GParted is a separate piece of software. You can download it from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

You download the ISO, burn it to a disk and then boot your machine into it (so restart the machine with the CD-ROM in the drive; and select the CD-ROM to be your boot device)
You can do loads with GParted including managing your partitions or wiping them etc. The UI is very simple and just a light version of GNOME with only GParted links.

---

### Post by johnhdsi on 2010-01-11
Awesome thank you so very much for the help. I'll give it a go and see what happens. Thanks again!!


John

---

