---
title: "Replacement for Simple Backup in 11.04"
date: 2011-05-04
forum: General Help
---

### Post by uaebuntu on 2011-05-04
I use Simple Backup to backup all my machines across my home network. 

I have just upgraded my test system to 11.04 with a clean install and want to restore all mt stuff from my backup, however, looking in the software centre Simple Backup no longer exists......

How do I restore my 10.10 data?

---

### Post by r-senior on 2011-05-04
It is in the repositories for 11.04:
```
sudo apt-cache search sbackup
sbackup - Simple Backup Suite for desktop use (core functionality)
sbackup-gtk - Simple Backup Suite GTK+ graphical user interface
sbackup-plugins-fuse - Simple Backup Suite FUSE plugins
```

Search for 'sbackup' in Software Centre, Synaptic, etc.

It's certainly not coming up as a search for "Simple Backup" in Software Centre, which you may want to report as a bug?

---

### Post by Rasa1111 on 2011-05-04
Deja Dup may also be an option.
i use it often and it works great.

---

### Post by uaebuntu on 2011-05-04
Thanks to both of you for your replies.

Simple Backup now installed and operating OK, however it has just raised another question of what to restore which I'll do as another post.

Thanks again

---

### Post by elewis on 2011-05-04
There is an sbackup application in 11.04, however it is not the same sbackup found in 10.04. Unfortunately, the 11.04 version lacks a restore functionality which may be due to a bug. Launching sbackup-restore brings up a backup dialogue, not a restore backup.
I could not find any GUI utility that would pick up the backups I have made with my 10.04 work stations. The lack of GUI restore was fatal to my use of 11.04. I reinstalled 10.04. This brought back full sbackup functionality and I am again on the air. A reliable backup and restore routine is mission critical.
More techno users will need to use straight tar and gzip/gunzip to handle backups made under 10.04 in 11.04. That, however is not tenable for my organizations.

---

### Post by uaebuntu on 2011-05-05
I installed sbackup and sbackup-gtk, the latter gave the GUI interface and allowed me to restore.

because of the significant differences between 11.04 and 10.10 a complete restore could damage the system, I have another thread in upgrades and installation forum looking at what to restore.

Basically I did a clean install of 11.04 and will bring the applications back manually, but some of the directories that have configuration files in them could be dangerous so as yet I have NOT restored 

/etc
/local/usr
/var

and only intend to bring data over from /home when I have restored the user profiles.

---

