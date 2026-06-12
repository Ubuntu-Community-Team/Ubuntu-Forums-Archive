---
title: "Need a backup program that supports incrementals"
date: 2010-11-20
forum: General Help
---

### Post by dorlow on 2010-11-20
I've been searching the web all day and looking at many forums.  It is absolutely amazing to me that no one has created an easy to use program that creates full and incremental backups.  Everything I find only creates full backups.  When my backups are on the average of 300 GB, I don't want to perform a full backup every night.  Does anyone have an easy-to-use Ubuntu backup program that's gui that does that?

---

### Post by aeronutt on 2010-11-20
I use an rsync script; rsync does incremental.  I believer there's a gui for rsync....grsync or other, but I haven't tried the GUI.

---

### Post by 73ckn797 on 2010-11-20
I use grsync, available in Synaptic, to back up critical data. It does incremental.

---

### Post by dorlow on 2010-11-20
I'm looking at it now.  How do I setup incrementals?

---

### Post by dorlow on 2010-11-20
I see an option that says "keep partially transferred files"

---

### Post by dorlow on 2010-11-20
Forget it, I gave up on gui.  I'm just using tar.  I figured out this...

sudo tar -z --create \
           --file=/media/Backup/$(date +%y%m%d)_$(date +%H%M%S)_Pictures.tgz \
           --listed-incremental=/var/log/usr.snar \
           /media/0A2E27592E273D57/Pictures/

So then I just need to do this for every folder I want to backup and after a week, I need a scheduled task to delete the user. snar file so it creates a new full backup.

---

### Post by dcstar on 2010-11-20
> **dorlow said:**
> I've been searching the web all day and looking at many forums.  It is absolutely amazing to me that no one has created an easy to use program that creates full and incremental backups.  Everything I find only creates full backups.  When my backups are on the average of 300 GB, I don't want to perform a full backup every night.  Does anyone have an easy-to-use Ubuntu backup program that's gui that does that?

[http://www.granneman.com/techinfo/security/backup/unisonbackup.htm#TOC](http://www.granneman.com/techinfo/security/backup/unisonbackup.htm#TOC)

---

