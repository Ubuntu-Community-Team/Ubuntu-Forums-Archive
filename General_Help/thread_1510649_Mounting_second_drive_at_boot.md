---
title: "Mounting second drive at boot"
date: 2010-06-15
forum: General Help
---

### Post by zappadragon on 2010-06-15
I have two hard drives in my computer, both 250GB. /dev/sda1 is my main drive with Ubuntu installed and then I have the second drive /dev/sdb1 which is my Backup Volume. I run all my backups and dump the data to this drive. Every time I boot the computer I have to mount the Backup Volume. Is there an easy way to get it to mount at startup?

Thanks and I hope I have given you enough information.

---

### Post by plucky on 2010-06-17
> **zappadragon said:**
> I have two hard drives in my computer, both 250GB. /dev/sda1 is my main drive with Ubuntu installed and then I have the second drive /dev/sdb1 which is my Backup Volume. I run all my backups and dump the data to this drive. Every time I boot the computer I have to mount the Backup Volume. Is there an easy way to get it to mount at startup?

Thanks and I hope I have given you enough information.

You have to add a line in **/etc/fstab**

See [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) for a Howto mount a Linux partition.

Good Luck

---

### Post by Palanthas on 2010-06-17
I was pointed towards this site a while back and it has always helped me with fstab.

[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

I have two HDDs that I have to set up in fstab any time I reinstall Ubuntu. This should do what you need, and if it doesn't work, post back and somebody will be sure to help!

EDIT: I was just looking through that link I posted and I don't think it says this but when choosing the mount point I choose the "/mnt/" location in /
This keep the icon for the HDD from showing up on your desktop.

---

