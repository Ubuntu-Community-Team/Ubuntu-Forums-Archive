---
title: "Help recovering files from ext4 volume formatted to fat"
date: 2011-10-19
forum: General Help
---

### Post by SnatchAttack on 2011-10-19
So I was trying to build a liveusb to try out the new kubuntu 11.10 and in the create startup disk program i accidently chose my ext4 formatted external hard drive instead of the flash drive. it quick formatted the hdd to fat and i haven't written anything to the drive since. Is there any way i can recover my files from the disk?

---

### Post by oldfred on 2011-10-19
Welcome to the forums.

You first should do an image backup as anything we try may make it worse and having a backup at least offers a way to go back.

You can use dd to copy exact image or possibly these:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)


If not sda use sdb, or sdc 
Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

This just changes partition table which may be all that is required. But e2fsck may be required if the file structure is still there.
change sdb7 to type 83
sudo sfdisk --change-id /dev/sdb 7 83

---

