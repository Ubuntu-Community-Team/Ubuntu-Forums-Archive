---
title: "Hard drive move"
date: 2010-10-28
forum: General Help
---

### Post by kooldino on 2010-10-28
I recently installed a new hard drive.  I booted off of a live CD and copied the contents of my old hard drive to my new hard drive.

I want to keep both disks in the system, however, I want the new hard drive to become the boot drive, so the OS and such runs off of it.  How do I accomplish this?

---

### Post by papibe on 2010-10-28
You have several options (I assume both are internal hard disks):
[INDENT][LIST=1]
[*]Swap the disk and do a clean install on the new one (do not format the old one). After you boot, copy manually all your files from the "old" /home/user to the "new" /home/users.
[*]Use clonzilla. Install your new hard drive (but keeping the old one where it is). Clone your old disk and then restore it back to the new one. After that swap the disks.
[*]Use gparted. Similar at the previous one. Boot using the Ubuntu installation CD, but select "try live" instead of install. Then look for gparted on the menus. You can read how to copy/move partitions [here]("http://gparted.sourceforge.net/larry/move/move.htm"). After that swap the disks.
[/LIST][/INDENT]

These are very general instruction, depending on which option you choose, you'll probably need to read and learn a little bit more.

But first of all: **[COLOR="Red"]remember to backup your files![/COLOR]**

---

### Post by kooldino on 2010-10-28
Well, as I mentioned, the data has already been copied from the old disk to the new disk (yes, they are both internal hard drives).

So by "swap disks", do you mean to simply swap the SATA cable, so it reads sda as sdc and vice versa?

---

### Post by papibe on 2010-10-28
> Well, as I mentioned, the data has already been copied from the old disk to the new disk (yes, they are both internal hard drives).
How did you copy the data? In order for the new disk to boot, a simple copy (like copy/paste on the gui, or cp on command line) won't work. But if you used a tool like gparted to copy the whole partition, you're ready to go.

> So by "swap disks", do you mean to simply swap the SATA cable, so it reads sda as sdc and vice versa? 
You have to options here. If you swap the disks**, next time you boot, you'll be booting using the new one. Another, is to go to the BIOS, and change the main device in which the system boots.

Did this help?
Regards.

** the cables.

---

### Post by kooldino on 2010-10-29
> **papibe said:**
> How did you copy the data? 

sudo cp -rp

> In order for the new disk to boot, a simple copy (like copy/paste on the gui, or cp on command line) won't work. But if you used a tool like gparted to copy the whole partition, you're ready to go.

Ah.  I was unaware that gparted could copy an entire partition.

> You have to options here. If you swap the disks**, next time you boot, you'll be booting using the new one. Another, is to go to the BIOS, and change the main device in which the system boots.

Changing the boot priority in the BIOS is no problem, but I didn't know if it would screw with the system if it's used to booting on sda1 and is now booting on sdc1.

---

### Post by kooldino on 2010-10-29
The plot thickens.

I did as you said and copied my 9.04 partition via gparted, then reset the boot order in the BOIS. It still booted to the old disk.  Then I realized something - The old disk has an older partition on it from an even older version of kubuntu (8.04).  It looks like it's actually booting LILO (or whatever the boot manager is) from that 8.04 partition.

So I guess I need to install a boot manager to the 9.04 cloned partition on my new hard drive.  Is that the best way to go?  If so, how do I do that?

---

### Post by papibe on 2010-10-29
Maybe I should have asked this before but... Do you have a separate /home partition on your old disk?

---

### Post by kooldino on 2010-10-30
> **papibe said:**
> Maybe I should have asked this before but... Do you have a separate /home partition on your old disk?

I don't, but I plan on doing a separate /home partition the next time I do a clean installation so it will make the installations easier in the future.

---

### Post by papibe on 2010-10-30
If you want to take the first option I gave you (number 1, I think is the easy one), I wrote more details in another thread. It may clear things up a little bit. Take a look:

[http://ubuntuforums.org/showthread.php?t=1609557]("http://ubuntuforums.org/showthread.php?t=1609557")

Regards.

---

### Post by kooldino on 2010-10-31
I checked it out, but why bother doing a complete reinstall and losing all of my programs and such when all I need is a boot manager to point to that partition, or to run one off of that partition?

---

### Post by kooldino on 2010-11-02
Bump

---

### Post by kooldino on 2010-11-04
I know someone out there can help me...

---

### Post by kooldino on 2010-11-09
Or not...

---

### Post by alphaamanitin on 2010-11-09
The easiest solution to me seems to be cloning your old drive to the new drive again.  I personally prefer the dd command.  It will make an exact copy of the original drive to the new drive if done properly.  I am not quite sure what you would like to do with the old drive after that.  If you want the old drive to simply be space than use gparted to reformat the drive.  

AlphaA

---

