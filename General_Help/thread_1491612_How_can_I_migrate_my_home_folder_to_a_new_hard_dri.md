---
title: "How can I migrate my /home folder to a new hard drive?"
date: 2010-05-23
forum: General Help
---

### Post by jon.reeve on 2010-05-23
I'm running out of space on the hard disk that contains /, and so I want to migrate my /home folder to a new hard disk. Does anyone know any easy way to do this?

---

### Post by sylvester_0 on 2010-05-23
This would easiest be done in recovery mode (select this at boot time.) You obviously can't do it when you're using files in the /home folder (a normal user is logged in etc.)

Format the drive as ext4 (mkfs.ext4), mount it in a temporary location (mkdir /tmpmount&&mount /dev/sdx0 /tmpmount), move the contents of your home folder to your new partition (mv /home/* /tmpmount) then unmount (umount /tmpmount) and make the necessary entry in /etc/fstab pointing /home to the new device/partition.

---

### Post by SoFl W on 2010-05-23
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://ubuntuforums.org/archive/index.php/t-1123750.html](http://ubuntuforums.org/archive/index.php/t-1123750.html)

I had trouble with the psycocats method, what I did was when doing a fresh install of 10.4 I told the install process to create a separate partition for /home

---

### Post by lovinglinux on 2010-05-23
Creating a new partition for home is strongly advised, since it allows you to keep your settings and personal files if you need to install Ubuntu from fresh.

Nevertheless, you can also move for example your music and/or video folder to the new partition and create a symlink to your home. This basically allows you to store the files physically on another driver/partition, but at the same time allowing the system to see them as if they were located under your home. My home folder for example has only configuration files and it has only 8Gb. All my personal files are somewhere else, symlinked to home. So my system sees my video folder under home, but it is not actually there.

Perhaps [this](http://manpages.ubuntu.com/manpages/jaunty/man7/symlink.7.html) will help.

---

