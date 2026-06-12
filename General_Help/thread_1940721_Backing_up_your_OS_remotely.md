---
title: "Backing up your OS remotely"
date: 2012-03-14
forum: General Help
---

### Post by ptmuldoon on 2012-03-14
Is there a way to make a backup of your OS via a lan connection?  

My home server running Ubuntu Server edition is of course connected to my home LAN.  Can I use another PC on the network to make a backup of the OS without having to shut it down?

---

### Post by raja.genupula on 2012-03-14
[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite#Backup_Destination_on_Remote_Machine](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite#Backup_Destination_on_Remote_Machine)

yup! you can take backup from your server and then place it remote machine .

---

### Post by CharlesA on 2012-03-14
> **ptmuldoon said:**
> Is there a way to make a backup of your OS via a lan connection?  

My home server running Ubuntu Server edition is of course connected to my home LAN.  Can I use another PC on the network to make a backup of the OS without having to shut it down?
You can use tar and ssh to do that as well.

I think Lars posted a command to do that, but I cannot recall what it is.

---

### Post by ptmuldoon on 2012-03-14
Thanks for the tips and links guys, but is sbackup doing what I'm trying to do?  I'm trying to back up the Operating System itself, so that if I have a hard disk crash or similar, I could take the backup iso file to burn to an disk and restore.

---

### Post by raja.genupula on 2012-03-14
i think you gonna like this 
[http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)

---

### Post by ptmuldoon on 2012-03-15
raja,

Thanks for the tips and links.   I just tried remastersys but learned it doesn't fully support a Ubuntu Server that does not a GUI installed.  I'll need to read back through the initial tutorial as well if it that method will make a backup without having a GUI or not.

Also does anyone else also have any suggestions for backing up an OS like Ubuntu Server that does not include a GUI?

---

### Post by CharlesA on 2012-03-15
Clonezilla - image the OS drive and keep the image on an external drive.

---

