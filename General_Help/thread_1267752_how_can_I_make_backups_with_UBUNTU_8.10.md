---
title: "how can I make backups with UBUNTU 8.10?"
date: 2009-09-16
forum: General Help
---

### Post by yanvolking on 2009-09-16
Hello Community,
 
I have recently changed from windows to UBUNTU on all my computers. It's a question of philosophy.  I use a 1TB external HDD to store all my data : personal admin, photos, movies, music etc.  I cannot allow myself to lose this data so I have 2 backup HDDs (that way there is at least one that is safely stored away when I am doing the back-up operation).  Until now I used **window's backup function** which creates a *.bkf file.
 
Does Ubuntu have a clone of Windows' BACKUP function or at least something similar with such options as incremental backups (so you dont have to re-backup the whole thing when you've just added a couple of files to the main HDD)?

---

### Post by shel-hall on 2009-09-16
The 'rsync' program will keep two (or more) disks syncronized, which seems to be what you want to do.  It's a command-line program, but many GUI front-ends exist for it.  Google "ubuntu gui rsync" and see what appeals to you.

'rsync' can work locally or over a network; I use it to back up my laptop to a server thousands of miles away, but it will work just as well with locally attached drives.  It's fast because it only sends the changes: it will send new files, or just new parts of files.

-Shel

---

### Post by yanvolking on 2009-09-16
Thanks very much.  I'll down load the package and give it a try.  Will let you know how it went in the next few days.

---

### Post by louieb on 2009-09-16
Along with rsync there is tar,  partimage and rdiff. 

To get an idea of whats out there search the **tutorial and tips** section for **backup** in the** title**.   You'll find quite a few scripts written for tar and rsync.

Another place to search is Synaptic you'll find programs such as **backula, sbackup** and **grsync**.

---

### Post by scouser73 on 2009-09-16
For backing up I use [[COLOR="Red"]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html"), the tutorial shows you how to use it and in my opinion I think it's an excellent program for backing up data.

---

### Post by Darkwing-Duck on 2009-09-22
A very good tool that was mentioned is rsync. Here is a good tutorial on setting up and using rsync. 

[http://gwos.org/udsf/doku.php/software:backup:rsync](http://gwos.org/udsf/doku.php/software:backup:rsync)

Hope this helps you out!

---

### Post by stinger30au on 2009-09-22
install wine

[http://www.winehq.org/](http://www.winehq.org/)

and use 

syncbackfreeware

[http://www.2brightsparks.com/downloads.html](http://www.2brightsparks.com/downloads.html)

works just fine for me for this, has done for years

---

