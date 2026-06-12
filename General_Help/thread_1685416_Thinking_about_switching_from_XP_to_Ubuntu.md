---
title: "Thinking about switching from XP to Ubuntu"
date: 2011-02-10
forum: General Help
---

### Post by cblnchat on 2011-02-10
Right now i have Ubuntu on a pretty small partition of my hard drive.  And im using it WAY more that XP so memory is running a bit low.  And i wanna switch from Windows to ubuntu permanently.  Is there a way i can have ubuntu use all my hard drive and take out windows XP without uninstalling ubuntu and reinstalling it?  If possible id like no to uninstall it.  

Thanks

---

### Post by 3Miro on 2011-02-10
You can boot form a LiveCD, remove/resize the windows partition and then resize/expand the Ubuntu partition. This is somwhat dependent on your partitioning scheme since you can only "merge" neighboring partitions. 

WARNING: BACKUP ALL IMPORTANT INFORMATION FIRST AS ANYTHING GOING WRONG CAN LEAD TO COMPLETE LOSS OF DATA.

---

### Post by cblnchat on 2011-02-10
> **3Miro said:**
> You can boot form a LiveCD, remove/resize the windows partition and then resize/expand the Ubuntu partition. This is somwhat dependent on your partitioning scheme since you can only "merge" neighboring partitions. 

WARNING: BACKUP ALL IMPORTANT INFORMATION FIRST AS ANYTHING GOING WRONG CAN LEAD TO COMPLETE LOSS OF DATA.

How do i do that?  Sorry i didnt say it in my original post, but im still pretty new to ubuntu.

---

### Post by 3Miro on 2011-02-10
> **cblnchat said:**
> How do i do that?  Sorry i didnt say it in my original post, but im still pretty new to ubuntu.

Do you have an Ubuntu CD. If not, download one and burn it (or you can use a USB drive). 

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Then use gparted. You want to move/resize/delete partitions.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

If you are new to those things, make sure to double-backup everything important.

---

### Post by oldfred on 2011-02-10
You should be backing all your data from either windows and Linux. I tend not to back up the full system as I will just reinstall, but I have installed multiple times and that is easier for me than trying to get a backup working.

Do you burn all your files to CD/DVD on a regular basis? Copy to external flash drives/USB hard drive even more frequently?

If backing up /home be sure to include hidden files & folders as that is where your user configurations and data are.

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[http://www.rsnapshot.org/](http://www.rsnapshot.org/)
[http://backintime.le-web.org/](http://backintime.le-web.org/)

Fulll system to backup:
[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

Post this:

sudo fdisk -lu

Click on windows partition in places, computer, left pane to mount it, then this will show all mounted partitions:
sudo df -H

---

### Post by Mad dog on 2011-02-10
I want to add my 2 cents. I'm sort of new so tell me if I'm wrong.

All you have to do is backup your HOME folder (The entire thing) then reinstall Ubuntu, then import your backed up HOME folder.

Isn't this the easiest/cleanest/most efficient way to do it?

:guitar:

---

### Post by oldfred on 2011-02-10
I pretty much agree with Mad Dog.

But I also backup any system file in /etc that I manually edit. I just put into /home a copy (but do not reinstall, but review settings). I also run a list of installed apps, since I have installed a lot of things and it is a lot easier to reinstall from a list. And I include a copy of bootinfoscript as that has a lot of drive & configuration info that may be useful in recovering data.

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

---

