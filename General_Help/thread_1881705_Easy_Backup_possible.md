---
title: "Easy Backup possible?"
date: 2011-11-16
forum: General Help
---

### Post by hogfan on 2011-11-16
I'm running an Ubuntu server and have yet to find a good quick tool for backing up a couple of directories to an external hard drive attached to my server.  The FileSystem Backup tool in Webmin is pretty much worthless as I have never been able to get it to work.  Basically, all I'm needing to do is complete one initial backup manually of each folder to the attached external HDD, and after that point have differential backups (when each time the scheduled backup runs, only new or changed files are added/updated in the existing backup).  I do not even require any compression for the backup.  rsync sounds like the best tool, but I don't understand all the options and would prefer not to spend a ton of time messing with a a config file.  Is there a decent WebGUI backup tool out there that I can simply install via apt, and then schedule and manage my backups via a web interface?  I have had this server running for several months with Apache, Subsonic, etc. but have yet to find a user friendly way of scheduling and managing backups.  I don't mind managing some things from a terminal window, but backups is something I'd like to be able to point & click to manage.  Any suggestions are appreciated.

-hogfan

---

### Post by camaron1 on 2011-11-16
Back in Time is what you are looking for (GUI for rsync). It is extremelly easy to use, it does incremental backups on schedul and automatically, you can have different profiles, etc. Don't know about the web interface though.

---

### Post by raja.genupula on 2011-11-16
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

that have many options.

i hope that gonna be  helpful to you.

---

