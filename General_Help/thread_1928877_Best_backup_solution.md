---
title: "Best backup solution?"
date: 2012-02-20
forum: General Help
---

### Post by blackbird3216 on 2012-02-20
Hi All. I think it is time for me to setup a backup system for my files. I have lost my files once, and I don't want it to happen again. 

My main HD is a 320gb seagate. I installed a backup HD with 120gb, which should be sufficient to simply hold my personal files. 

The HD is currently formatted as fat3d, and does not mount upon login. I really don't like how it always appears on my desktop when I do mount it. I think there should be a way to disable that popup. 

I've been looking at backup solutions, and I think that the best program would be Grsync. Other programs, like Back in Time, Flyback, etc seem poorly maintained and may not hold up. Since I only need to backup /home, I don't think it should be that much of a problem. 

I wanted something that uses symlinks, as to reduce the amount of copying needed. 

Is there a solution similar to "time machine" for Mac-OS? I think that the Ubuntu Foundation should consider including a backup utility in the fresh install, as to emphasize the importance of backing up.

---

### Post by hwttdz on 2012-02-21
>Hi All. I think it is time for me to setup a backup system for my files. I have lost my files once, and I don't want it to happen again.

Regular backups are a great idea, and they can make a lot of things easier, even outside the world of hardware failures.  Imagine you want to upgrade via fresh install, or switch distros.  No need to back up your data, just unplug your backup drive, wipe the other one and start fresh. Once you have the install up and humming, bring your data back in.

>My main HD is a 320gb seagate. I installed a backup HD with 120gb, which should be sufficient to simply hold my personal files.
Sounds pretty reasonable.  

>The HD is currently formatted as fat3d, and does not mount upon login. I really don't like how it always appears on my desktop when I do mount it. I think there should be a way to disable that popup.
Are you using gnome?  I think you need to look in gconf-editor and search for a key named "volumes visible" or somesuch, just searching for volumes should bring it up.  Uncheck the box.  Drive no longer shows on desktop.

>I've been looking at backup solutions, and I think that the best program would be Grsync. Other programs, like Back in Time, Flyback, etc seem poorly maintained and may not hold up. Since I only need to backup /home, I don't think it should be that much of a problem.
grsync appears to be just a frontend for rsync.  You should look into how rsync works, because in some configurations it will delete files in the backup when they are deleted from the source.  I keep independent .tar.gz archives of my home directory, so files can appear in one and not in another.  

>I wanted something that uses symlinks, as to reduce the amount of copying needed.
A symlink does reduce copying, but the copying is exactly what you need for backup purposes.  Imagine you have books, and instead of having two copies of the same book in two different libraries, you have a slip of paper in one library that says, please find this book in the other library.  Now one library burns down.  That slip of paper isn't going to do you much good.  This is why you want two full copies of any data you want to keep on two different drives (two different machines in two different physical locations is even better).

>Is there a solution similar to "time machine" for Mac-OS? I think that the Ubuntu Foundation should consider including a backup utility in the fresh install, as to emphasize the importance of backing up. 
The default backup application is Deja Dup, which is a frontend to duplicity.  In general there is a default application for any functionality, but you should decide if that application is the best suited to your personal needs.

---

### Post by blackbird3216 on 2012-02-21
Hi. Thanks for replying. I tried Grsync, and that works pretty well. I might have to try Deja-dup too. 

The problem I am having now is that I can't automount my drive. I want to keep auto-popup for things like flash drives/media players, but I don't want my backup HD to consistently pop-up like that. 

One "solution" that did not work was to create a folder at /mnt/Backup, and force the system to mount at that point. That never worked. 

Here's the failed "solution":
sudo mkdir /mnt/Backup
sudo gedit /etc/fstab

Here's the Fstab file: 
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=64d80785-1447-4104-bad2-0d324a968be3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c54e0a03-255b-402c-9b72-5ef62a505525 none            swap    sw              0       0
# Backup Drive
/dev/sdb1  /mnt/Backup   ext3  none

Every time I bootup, it does not find /dev/sdb1. I also tried it with the UUID, but that didn't work either. 

Actually, this is not what I want. I want the 120gb drive to show up as a drive (when I go to "Computer"), not as a folder. Is there a way to do this?

---

