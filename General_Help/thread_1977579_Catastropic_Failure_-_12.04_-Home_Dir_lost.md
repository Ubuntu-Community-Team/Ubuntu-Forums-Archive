---
title: "Catastropic Failure - 12.04 -Home Dir lost"
date: 2012-05-10
forum: General Help
---

### Post by makitso on 2012-05-10
Clean install 12.04, Gnome3 shell, Cairo dock.  Have backup disk mounted as /home/backup which contains copy of /home.  Inserted thumb drive and deleted some files which showed up in Cairo trash.  Middle clicked on Cairo trash and deleted files.  After about two minutes nothing happened so I ejected the drive and rebooted.  Upon reboot, the entire /home/me directory is gone completely and so is the backup on the attached drive!!!  Nautilus shows my home folder with 456K files.  Gparted shows 6GB used.  Same for backup.  

Help, I don't know how to recover the lost directories and files

---

### Post by TBABill on 2012-05-10
Do you have a trash bin on the flash drive? Could those files be located there? Just wondering which trash can  you clicked to empty....the flash drive or the computer's.

---

### Post by makitso on 2012-05-10
I clicked on the trask can on the Cairo dock.  It should have deleted the .trash content on the thumb drive.  

When I rebooted the system there is now a standard file system on /home for my user id.  Its all the default stuff, all the prior folders and files are gone.  

I can't believe it took out my backup drive as well!!  

SO, I believe the file system was destroyed and Ubuntu created a new one?  Any idea how to recover?

The thumb drive was only 256MB whereas my mounted home folder was 6GB

---

### Post by lukeiamyourfather on 2012-05-10
Are you sure the disk is mounted where you think it is? Use this command to list the current mounts and their space.

```
df -h
```

---

### Post by makitso on 2012-05-10
Yes, /dev/sdb2 is mounted as /home/me.  If I look at the directory and the sub-directories under it they are all the standard directories with Ubuntu and they have todays date.  None of the older folders are shown either on the primary /home device or the /dev/sda2 backup device.

---

### Post by flemur13013 on 2012-05-10
This may have been answered already (via "df -h") but I've had surprises when I think I'm backing up to a USB drive at /backup/whatever and the drive isn't mounted there, so the backup is going to the / partition in /backup/allyourstuff directories. (This might be because I didn't create the /backup directory specifically as a mount point, rather than as a normal directory).  So anyway, your files might be on your / partition...?

---

### Post by lukeiamyourfather on 2012-05-10
> **flemur13013 said:**
> This may have been answered already (via "df -h") but I've had surprises when I think I'm backing up to a USB drive at /backup/whatever and the drive isn't mounted there, so the backup is going to the / partition in /backup/allyourstuff directories. (This might be because I didn't create the /backup directory specifically as a mount point, rather than as a normal directory).  So anyway, your files might be on your / partition...?

That's a good point. Maybe try booting without the extra disk or just unmount it. The files might be in the folder that you're mounting the extra to.

---

### Post by makitso on 2012-05-10
Gosh, I wish that were the case, but no go.  Two years worth of data lost.  I thought I was save by having two disks and doing backups from one to the other.  Both the primary and the backup have new file systems that were created at the time of the failure.  The files are there just no file systems.  I can probably recover some specific files, e.g. jpg files but others are lost and my mail as well.  I just don't know how this could have happened and why the cairo dock trash delete took out two mounted file systems??????

[lukeiamyourfather]("http://ubuntuforums.org/member.php?u=774656"):  I have booted the linux rescue disk and tried mounting things but no help.  The file system is intact but all my directories and files were deleted.  At this point I do not know if its a Cairo Dock issue or a Ubuntu issue.

---

