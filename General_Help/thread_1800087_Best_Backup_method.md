---
title: "Best Backup method?"
date: 2011-07-08
forum: General Help
---

### Post by JayWalker256 on 2011-07-08
Hello. I just got a 2TB drive with the intention of backing up multiple Ubuntu machines to it. What would be the best way to do this, keeping ease of restoration in mind? Should I just copy each drive image to the BU drive, or use a utility like Back in Time? What do you use/your suggestions? Thanks!

---

### Post by lmarmisa on 2011-07-08
I recommend to use Clonezilla Live:

[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by dFlyer on 2011-07-08
If you just want to backup your data, photos and such, just use deja dup. It what I use and works great.

---

### Post by e79 on 2011-07-08
To backup (clone) the full installations, go as suggested by **lmarmisa** and use** [CloneZilla]("http://clonezilla.org/").**
 
To only backiup files (home folders and such), there is many apps that can do it :
 
[**LuckyBackup**]("http://luckybackup.sourceforge.net/")
 
[**BackInTime**]("http://backintime.le-web.org/")
 
[**DejaDup**]("http://live.gnome.org/DejaDup") (as proposed by **dFlyer)**
 
..to only name a few....check in the Ubuntu Software Center and try/decide which one is best for you
 
**Hope this helps**

---

### Post by IWantFroyo on 2011-07-08
I personally wouldn't back up the entire system (I'm a reinstall person), but that's up to you.

I just use something like DropBox to keep my documents on the net, and BackInTime is a good on-system backup.

---

### Post by lmarmisa on 2011-07-08
If you plan to use Clonezilla for the complete backups of several computers I recommend to create a folder for each computer in the root directory of the external 2TB hard drive (computer1, server2, etc). Clonezilla allows to select this folder during the backup and recovery procedures. Clonezilla will add a second directory level for each specific backup according the date and time when the backup was made.

A last comment: clonezilla works fine not only with Ubuntu/Linux systems but also with Windows systems (maybe Mac OS is also supported but I am not sure).

---

### Post by psusi on 2011-07-08
I don't like image backup for several reasons:

[LIST=1]
[*]You can not restore to an even slightly smaller disk, even if the original was nowhere near full
[*]You have to boot from a cd to make the backup
[*]Any fragmentation present in the original is preserved when restored
[*]Wastes time and space backing up the OS, which can easily be reinstalled from the original media
[*]You can't restore individual files from the image, with most of the available tools ( Norton Ghost can )
[/LIST]

---

### Post by nmaster on 2011-07-08
it depends somewhat on the machines and the type of data you want to restore.  for example, if the machines have a vanilla install but a lot of personal data, then you really don't care about the OS and so 'Back In Time' (or some other rsync tool) for the home partition is probably best.

that's just one example, but you get the point.  different people need different backup methods and utilities.

---

### Post by Erik1984 on 2011-07-08
What I do myself, but I have only one machine, is rsyncing my /home/user to an external drive (and some important files over ssh to a server). The advantage of [rsync]("https://help.ubuntu.com/community/rsync") is that all files are on the target in a readable format. With a reinstall of Ubuntu I don't rely on specific software then. I can just copy back the files I want from the external drive.

---

### Post by bpb_21 on 2011-09-12
> **Euroman said:**
> What I do myself, but I have only one machine, is rsyncing my /home/user to an external drive (and some important files over ssh to a server). The advantage of [rsync]("https://help.ubuntu.com/community/rsync") is that all files are on the target in a readable format. With a reinstall of Ubuntu I don't rely on specific software then. I can just copy back the files I want from the external drive.

That's my preferred strategy.  I'd rather have the individual files accessible from any given backup as I work on various OSes and don't like the idea of having to restore to an identical setup (i.e. as from an image).

---

