---
title: "How important is backing up?"
date: 2012-05-12
forum: General Help
---

### Post by davidftechman on 2012-05-12
I have been using linux for a little while now dual botting using wubi and im running xubuntu
and xubuntu does not have a backup program to use even though this is a freshly installed xubuntu and was wondering how important is it for me to back up and what back up applications are good to use?

---

### Post by billyseth on 2012-05-12
I threw together a pretty simple script that just copies over my important folders (photos, documents) to an external HD whenever it is plugged in. I looked into some actual back applications but they all seemed a little overkill for what I felt I needed.

I think the first time you lose a bunch of stuff on your computer because of a botched upgrade, or some sort of hardware failure you realize you should back stuff up.

---

### Post by sudodus on 2012-05-12
Tough guys don't back up their data, they do the job twice instead ;-)

So, are you a tough guy, or are you looking for a backup tool? In that case, what do you want, a GUI tool or a command line tool (and make a home-made script), a full backup (image) of everything or a selective backup of your private data or something in between?

---

### Post by Mopar1973Man on 2012-05-12
(Fly on the wall)

I'm really curious of the backup software out there for Linux. As for windows I've always create a full drive image backup to reduce the downtime to a few hours. As for linux I'm not sure how to backup yet as a full image so I'll hang out in the thread also and learn! ;)

---

### Post by marsdend on 2012-05-12
Nothing is 100% safe, I use Ubuntu One for my documents and pictures and a network HD plugged into my home router to backup the rest, downloads, music etc once a day. Works for me!

Well worth backing up though, can be a disaster if you loose everything! :)

---

### Post by Peripheral Visionary on 2012-05-12
*My* Xubuntu came with the great backup utility called **Xfburn**! All my music, pictures, documents, wallpapers, etc can be backed up to CDs in a matter of minutes.

---

### Post by whatthefunk on 2012-05-12
Backing up is very important!
Some things that I do to make sure my stuff is safe:
-I have /home on a seperate partition.  If the OS goes bananas and I have to do a clean install, I can keep /home intact.
-I do routine backups to a different hard drive using Back in Time.  It takes a quick snapshot of selected directories and files.
-About once a month and before I do anything major (upgrade, mess around with important system files, install program that might screw things up etc) I burn all my important stuff to a CD-RW so that if everything goes completely wrong and the computer is destroyed, I still have my data.

Ive been through several mess ups, clean installs, crashes, and virtual train wrecks and have never lost all my data.

---

### Post by wilee-nilee on 2012-05-12
> **davidftechman said:**
> I have been using linux for a little while now dual botting using wubi and im running xubuntu
and xubuntu does not have a backup program to use even though this is a freshly installed xubuntu and was wondering how important is it for me to back up and what back up applications are good to use?

You can at the least with a wubi use a backup to save your home, personally I use grsync to a external. I have partition installs so I also clone the OS.

As far as a backup to reload a wubi, I have never heard of one, but that does not mean it is not possible. A wubi is a file in Windows and a little different.

Personally I would do a partitioned install, and you can actualy transfer that wubi to a partition, there is a thread on the forums just for that, and now a wubi wiki, linked from that thread.

Really as far as backups go you have to think how you would feel if the install was not recoverable.

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by bodhi.zazen on 2012-05-13
> **Mopar1973Man said:**
> (Fly on the wall)

I'm really curious of the backup software out there for Linux. As for windows I've always create a full drive image backup to reduce the downtime to a few hours. As for linux I'm not sure how to backup yet as a full image so I'll hang out in the thread also and learn! ;)

Backing up is only as important as your data. 

There are many back up options, most are covered here:

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Personally I only back up my data ($HOME) and any system file I need to edit. IMO the vast majority of system files are available via a fresh install and apt-get.

---

### Post by lightning slinger on 2012-05-13
> **Mopar1973Man said:**
> (Fly on the wall)

I'm really curious of the backup software out there for Linux. As for windows I've always create a full drive image backup to reduce the downtime to a few hours. As for linux I'm not sure how to backup yet as a full image so I'll hang out in the thread also and learn! ;)

Closest imaging backup to a Windows package like Norton Ghost for linux is Redo Backup and Recovery at 

[http://redobackup.org/](http://redobackup.org/)

It will create and restore a full disc image and therefore can be used to retrieve a completely trashed system. It runs from a live CD based on Ubuntu and can create the image onto another HDD whether external or internal or USB Flash Drive but as it runs from a live CD not onto a CD/DVD directly!

---

### Post by mbott on 2012-05-13
I have 2 12.04 installations and SWMBO has an XP system.  For me, a weekly back-up of each using using Clonezilla is more than sufficient.  Anything thats *really* important gets more attention.  My version of the KISS principal.

-- 
Mike

---

