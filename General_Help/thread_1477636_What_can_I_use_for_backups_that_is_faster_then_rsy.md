---
title: "What can I use for backups that is faster then rsync?"
date: 2010-05-09
forum: General Help
---

### Post by darkshadow on 2010-05-09
I am currently backing up my data but find that it takes way to long to do a rsync, it takes forever to just find the differences and transfer them.

Out of 3 separate rsyncs the main one that is slow is my [www.skins.be](www.skins.be) mirror directory which is 41GB and has 392,200 files, sorted into multiple directories. Which grows by around 100 every couple days.

I think that something that would be able to track changes by inotify time on directories will speed it up since Picasa sure finds the changes fast when I open it and it is tracking over 26,200 pictures. I just don't know of a backup solution that does that.


The target is a external hard drive.

---

### Post by LoneWolfJack on 2010-05-09
Your problem most likely isn't rsync but the USB (I assume) connection to your external harddrive. rsync will try to compare each and every single file with the file on your external drive and I suspect that you're hitting the ~25 MB/s limitation of the USB2 implementation.

you may see massive performance improvements when using eSATA.

Other than that, and from my own experience the only real solution is to let your software write an update log and then do the copying yourself through a small bash script.

---

### Post by darkshadow on 2010-05-09
No it is not a speed issue since I when rsync copies data I only get a third of the speed that a "cp" gives

---

### Post by LoneWolfJack on 2010-05-09
that's because of the protocol overhead of USB.

---

### Post by iponeverything on 2010-05-09
The reason it takes so long to find the differences is.. drum roll please...

> 392,200 files

wow.. that's a serious filesystem. I have put together servers using maildir for a couple of hundred clients that didn't have that many files. 

Your best bet for speeding up backups is using SSD, using a filesystem better suited your type of I/O, having the right hardware -- fast drives, bus, etc.. and as mentioned by @LoneWolfJack, not going through USB. 

Looking at rsync as the weak link in the chain is not going to get you very far in speeding up your backups.

---

