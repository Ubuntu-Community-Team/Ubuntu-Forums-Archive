---
title: "Can I recover this ?"
date: 2010-02-18
forum: General Help
---

### Post by CeeVee777 on 2010-02-18
Hi,
I'm going to replace my Western Digital system disk with an SSD.

I've been doing weekly tar backups using the following command, changing the date for each backup

sudo tar cvpzf /media/Backup/Archive/Terminator20100212.tgz --exclude=/media --exclude=/proc --exclude=/mnt --exclude=/sys --exclude=/lost+found /

Can I replace my system disk, boot from a LiveCD, format the SSD system disk, restore my system using 

tar xvpfz /media/Backup/Archive/Terminator20100212.tgz -C /

Update grub as per
[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore)

then just alter the UUID's in fstab to conform to the new values.


OR

because the new drive is different to the old one will I have problems and have to do a fresh install ?

I guess the question I'm really asking is 
What hardware changes will make the tar backup non-useable ?

---

