---
title: "Distributing Image of HD to Two Separate HDs"
date: 2011-11-28
forum: General Help
---

### Post by mobius129a on 2011-11-28
How can I copy an image - perhaps using ```
dd
``` - of my 160gb SATA hard drive to two separate iSCSI hard drives each of which is 80gb? Cheers.

---

### Post by searchfgold6789 on 2011-11-28
Raid.

---

### Post by oldfred on 2011-11-28
dd is only intended to copy from same size to same size. 

I am not sure dd is what you want. What is it that you really want to do.

Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

# backupscript.txt
discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by mobius129a on 2011-11-29
@oldffred
At the moment, I am doing two types of backup:
(1) a full, semi-automated (I have a cron script that alerts me every other week to connect backup media and then backs-up if it finds one) backup of my home and opt dirs.
(2) a full, manual backup involving me booting with live cd and dd'ing my /dev/sda (160gb) partition to an external hard drive. 

What I want to do is (2) but using some spare iSCSI 80gb drives I have. I haven't had to time to check but I assume I can use an old rack server to mount the iSCSI drives as external and copy an image to these. I'd prefer my backup method for (2) to be an image so there's minimal fuss should I have to restore. However, out of the 160gb, only about 40gb is currently used - 30gb for home and 10gb for /.

---

### Post by oldfred on 2011-11-29
That is part of the disadvantage of dd. It also copies the empty or zero bits also.

I do not use tar, but I would think that would be a lot better for you.
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)
HowTo: Full backup with tar (older but tar has not changed)
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

I have just a home system so exact recovery is not a requirement. I just back up /home, some of /etc, a list of installed apps and some other stuff and then just plan on a reinstall. I always do clean installs so I am familiar with that way. So I use rsync and some copies to DVDs of the most important or changing info.

---

### Post by mobius129a on 2011-11-29
Ok, thanks. I think the full backup with tar should do the trick.

---

