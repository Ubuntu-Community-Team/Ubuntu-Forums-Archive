---
title: "Backups for mere mortals"
date: 2011-04-30
forum: General Help
---

### Post by edpatterson on 2011-04-30
I am looking for a SIMPLE point and click backup solution for Ubuntu.

At work I manage a rather large Net Backup installation so I am not a complete idiot. Just very graphically dependent. I knew it was bound to happed as soon as the mouse came out...

I installed backuppc. Read the docs/how-to's/tutorials for 90 minutes and have come to the conclusion that it simply is not worth the time effort or energy. I could not even figure out how to use backuppc to backup my Documents directory to a USB attached HDD. Now that is sad.

I currently use rsync over a network to backup up my Ubuntu laptop to a share on Server 2003. That is when it does not error out due to the difference in time stamps. Basically, I get a point in time backup, incrementals don't work.

Thanks for any help
Ed

---

### Post by Irony on 2011-04-30
It is very easy to backup from terminal. Here is the command I do for a full backup of Ubuntu;

```
sudo cp -ax /. /media/backup/.
```

This copies my entire install to an external drive into a folder which here is named backup.

If my install gets corrupted I format my drive and copy the back up back back using a similar command...

---

### Post by edpatterson on 2011-04-30
I was hoping for a graphical interface so I could check various directories/files and a destination with full/incremental/differential options. I guess I'll just mount an external drive and drag and drop.

Being paranoid. I have a new drive for the 11.04 install but wanted to make double dog sure I didn't lose anyting. 

I still have my old 8.04 and 9.04 drives too :-)

---

### Post by Lateralis on 2011-04-30
You may want to check out rsync (command line program; I think installed by default) with the Grsync GUI (which is not).

---

