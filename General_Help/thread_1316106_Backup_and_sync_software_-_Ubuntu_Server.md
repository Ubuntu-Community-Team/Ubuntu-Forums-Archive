---
title: "Backup and sync software - Ubuntu Server"
date: 2009-11-05
forum: General Help
---

### Post by mocka on 2009-11-05
I am having two computers I want to backup/synchronize with a folder on a Ubuntu Server 9.04. If I have edited the same file on one of the computers, I want the latter file to replace the earlier version of the file.

Also, it would be nice to have a software that comes with a Web GUI.

I have looked a little on Amanda (though it does not have WebGUI, thats for Zmanda), Backuppc and iFolder.

What should I pick (can be software that I haven't mentioned)?

---

### Post by Giblet5 on 2009-11-05
You want rsync.

No gui, but a gui would be a waste of time. Just enter the command and be done with it.

```
rsync -aurzpt /folderIwantsynced/ remotehost:/folderIwantsynced
```

That won't handle deleted files on the source. Add the -d option to do that.

You'll need to install openssh-server on the remote system (slave).


There is a gui interface to rsync, but it's an easy command to learn.

```
sudo apt-get install grsync
```

---

### Post by jimcuk on 2009-11-05
nice how would I go about scheduling grysnc, or would I have to look into cron jobs for rsync

regards
Jim

---

### Post by Giblet5 on 2009-11-06
> **jimcuk said:**
> nice how would I go about scheduling grysnc, or would I have to look into cron jobs for rsync

regards
Jim

You'll want to use cron jobs for rsync.


Windows is a GUI environment that provides rudimentary command-line interfaces; You can do a few things and it's easy.

To accomplish anything beyond rudimentary operations in Windows, one must learn a programming language. There is an advantage that comes with this: others *expect* to have to pay something to use your creations.


Linux is a command-line environment that provides some rudimentary GUI interfaces; You can do almost anything without learning a programming language, although it's a bit overwhelming.

To accomplish anything beyond rudimentary operations in Linux, one must resign oneself to learning to use the command line. There is an advantage that comes with this: your ability to perform complicated tasks is unbounded by interface constraints.


Advantages and disadvantages. Everything's a balancing act.

---

### Post by rollback on 2009-11-06
You can use a free cloud storage service like Ubuntu One, or Dropbox.

---

### Post by MatthewMetzger on 2009-11-16
backuppc can use rsync as it's transfer mechanism. Works great. Slightly complicated to set up, but wonderful once you understand it.

---

### Post by cscj01 on 2009-12-30
Here is my environment:


[LIST=1]
[*]a Karmic PC with two internal hard drives and one USB hard drive;
[*]an XP PC with two internal hard drives and one USB hard drive;
[*]the two PCs on a home network with file and print sharing.
[/LIST]

Here is what I would like to do;

[LIST=1]
[*]sync (including deletes) my data hard drive on my Karmic PC with the USB drive on the XP PC;
[*]use the USB hard drive on the Karmic PC for selected backups of other data on either of the PCs.
[/LIST]

Would backuppc using rsync be good software to do this?

---

### Post by cscj01 on 2009-12-30
bump

---

### Post by kjohri on 2009-12-31
You can try using Unison for synchronizing files between different machines. Unison works on Linux as well as Windows. 

[http://www.softprayog.in/tutorials/synchronize-files-primer.shtml]("http://www.softprayog.in/tutorials/synchronize-files-primer.shtml")
[http://www.softprayog.in/tutorials/synchronize-files-advanced.shtml]("http://www.softprayog.in/tutorials/synchronize-files-advanced.shtml")

---

### Post by stinkeye on 2009-12-31
Have a look at 
[_[COLOR="DarkRed"]**luckyBackup**[/COLOR]_]("http://luckybackup.sourceforge.net/")
A Gui which uses rsync and can be scheduled.
Any questions go here: [_[COLOR="DarkRed"]http://www.kde-apps.org/content/show.php/luckyBackup?content=94391[/COLOR]_]("http://www.kde-apps.org/content/show.php/luckyBackup?content=94391")

---

### Post by cscj01 on 2010-01-15
I tried Unison, but either it was overkill, or I was too simple-minded to set it up. Then I tried luckyBackup, and everything is working as I had hoped.  I really like luckyBackup.

---

