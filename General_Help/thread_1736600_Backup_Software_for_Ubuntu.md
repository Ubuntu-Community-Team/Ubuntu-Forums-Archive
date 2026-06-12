---
title: "Backup Software for Ubuntu"
date: 2011-04-22
forum: General Help
---

### Post by krumpy on 2011-04-22
I'm a new Ubuntu user switching over from Windows.  I was curious what the best software is to set up a recurring backup to a my network drive?  I googled but didn't really see much consensus.  Thanks.

---

### Post by Rubi1200 on 2011-04-22
Hi and welcome to the forums :-)

Take a look here for some backup options:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by Stray Wolf on 2011-04-22
The fact that there's no consensus may have to do with personal preferences toward different interfaces (gui's) and terminal methods like rsync.  You can look under section 30 of [http://ubuntuguide.org/wiki/Ubuntu:Maverick.]("http://ubuntuguide.org/wiki/Ubuntu:Maverick")

Note:  Make sure you select the guide for your version of Ubuntu.

Also, in the software center there are several you can install.  I use backintime for the most part.  Some people like clonezilla but with backintime it pretty easy to get a fresh install re-configured to your personal flavor too.

---

### Post by BigBaka on 2011-06-20
I've been on Ubuntu for a couple of years now but have not been particualarly happy with any backup programs so far. I was recently using Deja dup as it was able to automatically backup over a network, but I discovered that it kept increasing the space it took up on my backup hard drive and eventually my hard drive became full, and I deleted all the backup folders, and a week later the hard disk crashed and I lost everything! Murphy's law! 

Also it saved all the files in a compressed format under a duplicity system, but actually I would prefer to simply have the files themselves in the backup rather than a compression of all the files. 

If anyone had better software recommendations, or ways to tweak deja dup to overcome these problems I'd love to hear as well.

Regards,
BB

---

### Post by Sidney232 on 2011-09-17
Stray Wolf - are there any guides to help you reconfigure a fresh install using snapshots taken from another machine?

---

### Post by CrusaderAD on 2011-09-17
Keep is awesome.

---

### Post by rewyllys on 2011-09-17
I've been using Lucky Backup for almost a year, with completely satisfactory performance.  It's available via the Synaptic Package Manager; the package name is **luckybackup**.

---

