---
title: "RSYNC error - backup failed"
date: 2011-01-29
forum: General Help
---

### Post by sisterdorothy on 2011-01-29
Our backup script was working fine (ssh to the server, back up /home to a second hard drive on my computer). Then right after an ubuntu update, it quit working.  I investigated and found that "something" had changed the label on the backup hdd to what looked like gibberish to me. But the script identified the backup hdd by its uuid, which didn't change.  Yet, here is the error I get when the backup fails:

receiving file list ... done [took about 5 seconds]
rsync: mkdir "/media/14D9-3B1F/server-backup" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(594) [receiver=3.0.6]

Note that the backup hdd IS mounted, uuid is correct, and the folder 'server-backup' DOES exist.

Does anyone have a clue for me?  I'm moderately experienced in Linux and ubuntu.  Our server runs centos 5.  And as stated, the backup ran fine for several weeks.  I think there was a new linux kernel on that update, but at this point a while later I don't know which one.  Current kernel is .2.6.31-22-generic.

thanks for any help...
Sr. Dorothy

---

### Post by sisterdorothy on 2011-01-29
Hmm, solved by myself, a "moderately experienced" linux user/administrator...whose memory ain't what it used to be.  Apparently I originally identified my backup disk in the backup script by the disk label.  Then when "something" relabeled my backup disk during an ubuntu update, I decided to use the uuid to designate it.  When I just now changed it back to the (new) label, it backed up my files.  I'm blushing...

---

