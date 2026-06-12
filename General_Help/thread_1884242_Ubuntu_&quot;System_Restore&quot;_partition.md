---
title: "Ubuntu &quot;System Restore&quot; partition"
date: 2011-11-20
forum: General Help
---

### Post by Kelvari on 2011-11-20
I'm sure that this is possible, but how would someone go about having a computer with a "System Restore" partition in Ubuntu?

Would you have to use something like the Boot Disc Creator and point it at an extra partition on the hard drive?

---

### Post by dniMretsaM on 2011-11-20
As in a partition that stores all your data in case of a crash (local backup)? You can use GParted to make a partition and a cron-scheduled script to transfer the files. There are probably other ways to do this, but I don't know what they are.

---

### Post by Kelvari on 2011-11-20
I mean like a "Factory Restore" partition - one you can boot into to do a fresh install of Ubuntu (or whichever variant you use). Kind of like how most OEMs have a System Restore partition to reinstall Windows.

---

### Post by oldfred on 2011-11-20
I do not believe in the full image backups, but some do. I saved these links for those.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

[http://www.rsnapshot.org/](http://www.rsnapshot.org/)
[http://backintime.le-web.org/](http://backintime.le-web.org/)
[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)
[http://flyback-project.org/](http://flyback-project.org/)

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

I just plan on reinstalling from a liveCD (actually USB or harddrive booted ISO for me) and restoring data that I backup a bit more regularly than the full image that I might create.

I like rsync to backup those things I consider most important on a  more often basis and the most vital data I copy to DVDs on about a quarterly basis. If I was a business I would be doing full backups daily or even more frequently depending.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by tordeu on 2011-11-21
I don't really understand what you are trying to do. When you are talking about "Factory Restore", how would that differ from using an Ubuntu CD to do a fresh install?

---

### Post by dcstar on 2011-11-21
> **tordeu said:**
> I don't really understand what you are trying to do. When you are talking about "Factory Restore", how would that differ from using an Ubuntu CD to do a fresh install?

Some people just want the install media on their hard disk and bootable, like:

[http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html](http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html)

Another option may be to create a Live USB and then put the image of that onto the hard disk and see if it boots?:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Kelvari on 2011-11-21
> **dcstar said:**
> Some people just want the install media on their hard disk and bootable, like:

[http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html](http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html)

Another option may be to create a Live USB and then put the image of that onto the hard disk and see if it boots?:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

This is what I was hoping to achieve. I have to admit, I tend to put Linux (primarily Ubuntu for ease of use) on older computers and give them to people that need a computer, and have been trying to come up with a better solution than having to give out CD after CD or flash drive after flash drive.

Would using UNetbootin actually work for this, or is there something else that I would have to do?

---

### Post by tordeu on 2011-11-21
Ok, I just wasn't sure, because when it said "System Restore", I thought more of a backup solution (system+userdata), while "Factory Restore" sounds more like "Install CD on disk".

Anyway, I don't know if that is of any use for you, but if you want to backup the system after it is installed (so that you don't need to go through the install process again), the things oldfred posted might be worth a look. Also, there is something else I could think of, although I am not sure if they are of any use for your case):

Install two Linux systems on the disk. One "main" system and one "rescue" system. After both are installed, boot into the rescue system and backup the main system to the rescue partition (with tar, rsync, dd, any special backup tool, ...). This way, you have a rescue system where you can easily install additional software to and which you could also use to make additional backups of the main system, which has the advantage that the main system is not running while making a backup, thus preventing consistency errors.

---

### Post by majedaly on 2011-11-21
I reached this solution totally by chance! I needed to upgrade my laptop's hard drive, so, I bought a new drive, and used gparted to copy the partitions from the old drive to the new drive. When I finished, I used the old drive as an external USB disk. did not erase any data, because I wanted to verify that everything was in place on the new drive.
connecting the old drive using the USB port on ANY computer would boot up ubuntu with the exact same settings I had on my old machine. Tried it on many platforms, seems it gets everything to work!
Now, I carry this drive with me, and whenever I need to access my files, i just connect it to any PC, and just boot it from the USB drive, and voila !

---

### Post by tordeu on 2011-11-21
Great to hear. That's one of the very nice things about Linux: The ability to boot an installation on a different PC.

---

