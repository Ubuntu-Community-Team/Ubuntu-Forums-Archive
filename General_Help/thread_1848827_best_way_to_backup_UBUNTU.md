---
title: "best way to backup UBUNTU"
date: 2011-09-23
forum: General Help
---

### Post by liquidmonkey on 2011-09-23
am using 11.04 and have installed quite a few programs for research i'm doing.

how can i easily backup an entire copy of UBUNTU that of course includes any special programs or settings i have made.
i'm not concerned with files in folders (ie download or documents) as i use UBUNTU ONE to backup / sync those.


i've searched and seen the official ubuntu backup page but to be honest, that page looks out of date.



any suggestions?

---

### Post by haqking on 2011-09-23
> **liquidmonkey said:**
> am using 11.04 and have installed quite a few programs for research i'm doing.

how can i easily backup an entire copy of UBUNTU that of course includes any special programs or settings i have made.
i'm not concerned with files in folders (ie download or documents) as i use UBUNTU ONE to backup / sync those.


i've searched and seen the official ubuntu backup page but to be honest, that page looks out of date.



any suggestions?

make a tarball using .tar

clonezilla to take a complete clone of your system

simple backup (in the repos)

dd (man dd)

remastersys

lots of options

---

### Post by seawolf167 on 2011-09-23
I'm a big fan of Clonezilla for full images every couple of months, then rsync for critical data daily, though as posted above you have lots of [backup options]("https://help.ubuntu.com/community/BackupYourSystem"):

[LIST]
[*][Clonezilla]("http://www.clonezilla.org")
[*][Rsync]("https://help.ubuntu.com/community/rsync")
[*][Tar]("https://help.ubuntu.com/community/BackupYourSystem/TAR")
[*][dd]("http://ubuntuguide.net/backup-and-restore-entire-hard-disk-with-dd-command")
[*][Sbackup ]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite")(software)
[*]+more
[/LIST]

---

### Post by polardude1983 on 2011-09-23
Currently I rsync my /home folder, /etc/apt/sources.list, /etc/apt/sources.d.list, and then I also create a backup of my installed programs using dpkg. But you can also backup installed programs from synaptic too.

There are quite a few ways to do it. No way is wrong.

---

### Post by seawolf167 on 2011-09-23
> **polardude1983 said:**
> No way is wrong.

The only "wrong" way is to make backups then never check their integrity. The worst feeling in the world is opening a backup for something critical only to find that it is corrupted and unusable :(

---

### Post by SecretCode on 2011-09-23
I think Clonezilla and Remastersys are the most appropriate for what you ask for.

And I second the importance of testing your backups can be restored!

Not just once; CD and DVD backups can degrade, and HDD backups can be overwritten or fail. Any backup you hope to use more than a year later you should test, and possibly re-write.

---

### Post by sammiev on 2011-09-23
+1 for Clonezilla, I use it every 2nd week to backup all my OS at the same time. :)

---

### Post by CharlesA on 2011-09-23
> **SecretCode said:**
> I think Clonezilla and Remastersys are the most appropriate for what you ask for.

And I second the importance of testing your backups can be restored!

Not just once; CD and DVD backups can degrade, and HDD backups can be overwritten or fail. Any backup you hope to use more than a year later you should test, and possibly re-write.
+1. If you are just doing data backups, rsync can't really be beat imo.

Mmm rsync over ssh... ;)

---

### Post by HermanAB on 2011-09-23
I just backup data with rsync and I keep a tarball copy of /etc.  Backing up anything more than that is not much use, since Linux is very easy and quick to re-install.

---

### Post by Bobhuber on 2011-09-23
Fsarchiver. I use it daily. Advantage - You can back up your entire partition while it is  mounted without the need to boot from a live CD and has the ability to restore to any size partition as long as there is room on the partition. It can be found in the package manager.

[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

---

### Post by liquidmonkey on 2011-09-26
thanks for all the replies, will give your suggestions a try for sure!
and yeah, linux is extremely easy to re-install as someone mentioned BUT all the extra stuff i have setup is not hence why i want a good backup solution which encompasses all the extras i put in and setup.

THANKS!

---

### Post by mastablasta on 2011-09-26
i use mintbackup. they developed it as they use reinstall as preferred method of up&#353;grade unlike Ubuntu's upgrade method.
 
anyway it's easy to use with 2 buttons for backup (one for system and one for home folder files) and 2 buttons for recall of backup.

---

