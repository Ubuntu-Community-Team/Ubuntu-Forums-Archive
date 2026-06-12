---
title: "Syncing files between windows and ubuntu"
date: 2010-04-01
forum: General Help
---

### Post by [z]er0 HP on 2010-04-01
Hi,

I have a large music collection (80gb or so) Which I would like to sync between my windows hard drive and my ubuntu hard drive.

I primarily use my ubuntu drive but would like to be able to listen to my music on my windows drive when I use that and it would also serve as a backup.

in short:
new music on ubuntu in /home/user/music >> copy to C:\music

(rare occasion)
new music on windows in c:\music >> copy to ubuntu /home/user/music next time I login


Could someone please suggest how I could do this, thanks

---

### Post by WannabeFantasma on 2010-04-01
Is it on the same pc?
If so, you could use a partition with all your music.

If on other pc, I have no idea :D maybe a home network?
might be handy for me too! since I have a pc upstairs and downstairs, and now I have to move my external drive around! :D

---

### Post by cjhabs on 2010-04-01
> **'[z]er0 HP said:**
> Hi,

I have a large music collection (80gb or so) Which I would like to sync between my windows hard drive and my ubuntu hard drive.

I primarily use my ubuntu drive but would like to be able to listen to my music on my windows drive when I use that and it would also serve as a backup.

in short:
new music on ubuntu in /home/user/music >> copy to C:\music

(rare occasion)
new music on windows in c:\music >> copy to ubuntu /home/user/music next time I login


Could someone please suggest how I could do this, thanks

rsync is available for both platforms and can do this.
You can trigger a script at logon in Ubuntu with:
System-> Preferences -> Startup Applications

Not sure how you trigger it in Windows.

---

### Post by [z]er0 HP on 2010-04-01
Both hard drives are in the same computer.

Would you please be able to give me an example of how to use rsync?

---

### Post by SteveHillier on 2010-04-01
You could try this link.

I googled it and there are lots of references to rsync on this forum

```
http://ubuntuforums.org/showthread.php?t=587293
```

Steve

---

### Post by danielcheng on 2010-04-01
i guess you should create a separate partition just for storing music, perhaps using FAT32
it also reduces data redundancy

---

### Post by cjhabs on 2010-04-01
> **'[z]er0 HP said:**
> Both hard drives are in the same computer.

Would you please be able to give me an example of how to use rsync?

Here is a script I use to backup to a mounted partition on the same computer - it happens to be an external drive.

```
#!/bin/sh

# Backup /home/chris to the WD Passport USB drive
LOGFILE="/home/chris/logs/rsync_chris.txt"

rm -rf $LOGFILE

if [ -d "/media/My Passport/Data/my_ubuntu_backup" ]; then
	rsync -au --exclude='.cache' --exclude='.evolution/cache' --log-file=$LOGFILE /home/chris/ "/media/My Passport/Data/my_ubuntu_backup"
	echo "Backup Done"
else
	echo "Skipping backup - media drive is not available"
fi
```

As both folders are on the same drive, I would just share that folder instead.

---

### Post by anantshri on 2010-04-01
didn't understood one simple thing.

if both the harddisk are connected at the same time on a single system then its better to directly mount the windows partition on your linux and use it irectly.

---

### Post by coffeecat on 2010-04-01
> **danielcheng said:**
> i guess you should create a separate partition just for storing music, perhaps using FAT32
it also reduces data redundancy

Agreed, but NTFS would be a better choice, imo. NTFS read-write is reliable in Ubuntu, NTFS is a more robust filesystem than FAT32, and the OP has Windows (and chkdsk) should the NTFS filesystem get damaged.

---

### Post by john newbuntu on 2010-04-01
Like some others suggested, I'd just keep it in one common place and listen on both the OS's.  You may need to keep a backup on another drive just in case your hard disk drive crashes for which you could use rsync or a zillion other software.

---

