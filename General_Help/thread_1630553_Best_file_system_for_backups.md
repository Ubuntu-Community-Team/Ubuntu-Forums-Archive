---
title: "Best file system for backups"
date: 2010-11-25
forum: General Help
---

### Post by youngfool on 2010-11-25
Hi people,
I'm having some trouble to find a file system that allows me to backup my data to an external HD, and then access this data in other Linux (and sometimes windows and mac) machines.
The file system that I'm looking for must:
- have no user permissions: anyone can do anything with the data;
- have support to large files: I've used FAT for a while but it just sucks;
- maybe support access in windows and or mac with additional drivers;
- have journaling (or something of the sorts) to reduce the risk of data loss.
Any ideas?
Thanks and sorry for my engrish :)

---

### Post by a-user on 2010-11-25
use ext3 and change permission on the backup to all read/write etc. this can be done automatically  when copying (see man-page for cp or tar).

you cann access ext2/3 with free tools from windows.

alternativly you can use ntfs. ubuntu supports ntfs write and read. but it is the worse filesystem. though i still use it on usb-sticks exactly for the "useable everywhere" reason.
but the journaling of ntfs when used from linux does not work or at least not very well if i remember right. it isn't a good one anyway.

i guess there are tools for ext3//4 for apple too.

---

### Post by youngfool on 2010-11-25
OK, that's good, but is there a way to change the options of the file system inside the hd, so if I make backups or copy files from multiple computers, I don't need to change the permissions every time?

---

### Post by bodhi.zazen on 2010-11-25
IMO the Windows tools to access ext2 or ext3 are not great.

If you are using multiple platforms I would use ntfs or fat (not sure if mac can read/write to ntfs, if so use ntfs, otherwise fat).

If you are not using cross platform go for ex2. If you are using it for backup only there is no need for the over head of journaling, IMHO.

---

### Post by aeiah on 2010-11-25
i like to use exactly the same filesystem that the original data used, but i guess it depends what you're backing up and why.

if you use ext3 / ext4 you'll be able to take advantage of linux hard linking. NTFS can do hard linking too, but i dont know how well this works with linux. hard linking will allow you to easily create incremental backups that only take up as much hard drive space as the sum of any changes (+ the size of the first backup).

how often are you likely to need to access this data? if it's only when things go very wrong, then it doesn't matter if you can't access it in windows - just pop a livecd or liveusb in there and copy the bits you need using linux.

if you want everyone on the network to be able to get at them at any time then i suppose you'll have to go with NTFS or FAT. FAT's filesize limit of 2GB can be a real pain in the ***, though.

---

### Post by youngfool on 2010-11-25
and what about exFAT? I heard that it's being supported in Linux, but in embryonic stages still.
right now I'm using NTFS, but I just don't like to use non Open Source tools.
I do backups once every 3~4 months, erase all my old data from the external HD and copy all my files again. So I have the backup just in case I delete something by accident, but since in the backups have pictures, movies, songs etc, sometimes I use the HD to copy this stuff to friends' computers.
Guess I'll have to stay with NTFS though...

---

### Post by bodhi.zazen on 2010-11-25
> **youngfool said:**
> and what about exFAT? I heard that it's being supported in Linux, but in embryonic stages still.

I would not use any "embryonic" file system for backups. IMO what you want for backups is reliability.

---

### Post by youngfool on 2010-11-25
Sorry, I didn't explain myself properly.
I don't mean that exFAT would be good to use right now, but linux could have a file system like this for removable devices, no?
We can say many bad things about Microsoft, but at least they got the idea that FAT was outdated and upgraded it to use in all of these pen drives, mp3 players etc. We could have something like this, no?
ps: I know that FAT and removable devices are one of the worst virus spreading tools these days, but this is more because of faulty OSs, isn't it?
ps2: I also know that right now most of windows users don't have support for exFAT themselves, I just like the simplicity of the file system.

---

### Post by bodhi.zazen on 2010-11-25
> **youngfool said:**
> Sorry, I didn't explain myself properly.
I don't mean that exFAT would be good to use right now, but linux could have a file system like this for removable devices, no?
We can say many bad things about Microsoft, but at least they got the idea that FAT was outdated and upgraded it to use in all of these pen drives, mp3 players etc. We could have something like this, no?
ps: I know that FAT and removable devices are one of the worst virus spreading tools these days, but this is more because of faulty OSs, isn't it?
ps2: I also know that right now most of windows users don't have support for exFAT themselves, I just like the simplicity of the file system.

Not sure I am following what you are asking. 

There are many options for file systems available to Linux. I like ext4 and btrfs, but data recovery on these two file systems can at times be problematic.

There are two reasons I would cite for most removable devices to use FAT/NTFS:

1. Most people use Windows.

2. These two file systems are usable by all major OS.

---

