---
title: "Simple Backup Suite problem"
date: 2010-12-19
forum: General Help
---

### Post by tc101 on 2010-12-19
I just installed Simple Backup using the instructions here:

[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

I did a test run by selecting "Use recommended backup settings" in the General Tab and then hitting the "Backup Now" button.

I opened File System/var, and the backup folder has an X over it and is empty, although this is where the backup was supposed to go.  

I went to System/Admin/Simple Backup Restore and it shows me that the backup I just did is available and I was able to restore from it.

Why can't I see it under /var/backup ?  Why is the X over /var/backup and why does it show as being empty?  How can I access the backup and move it off sight?

---

### Post by Zill on 2010-12-20
It may be that you have (inadvertently!) changed the default backup target destination.  If you open a terminal you can see the settings with the following code...
```
cat /etc/sbackup.conf
```
If the "target" line does not show /var/backup then you can either edit the sbackup.conf file manually or use the GUI "Simple Backup Config".

Note that sbackup runs as root by default and so the destination directory will also be owned by root.  You may need to open your file manager as root (via sudo) to see or move the full contents.

---

### Post by tc101 on 2010-12-20
Thanks.  I remember something about sudo and root from using ubuntu years ago, but have forgotten the details.  Could anyone suggest a quick tutorial anywhere?

---

### Post by Ghost_Mazal on 2010-12-21
This terminal command will open a Nautilus explorer with root privilages.

```
gksudo nautilus
```

---

### Post by Zill on 2010-12-21
tc101:  As you appear to be using Kubuntu (kde), rather than Ubuntu (gnome), I suggest you open the Dolphin file manager as root with the following code:
```
kdesudo dolphin
```

Further info on the use of sudo is in the [RootSudo]("https://help.ubuntu.com/community/RootSudo") community documentation.

---

### Post by Ghost_Mazal on 2010-12-21
Sorry , I missed that

---

