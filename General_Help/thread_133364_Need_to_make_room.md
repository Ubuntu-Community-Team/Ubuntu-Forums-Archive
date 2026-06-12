---
title: "Need to make room"
date: 2006-02-20
forum: General Help
---

### Post by Fred Doolie on 2006-02-20
Hello, all. I'm a noobee here so be patient please.
While looking though my new Ubuntu system I found massive files in /var/cache/apr/archives.  They look like all the updates I did. Aren't those files just wasting space now? Can I safely delete them?

---

### Post by Sutekh on 2006-02-20
For sure.  

The only reason I'd keep them, was if you planned to move them across to a fresh install and wanted to install without downloading them again.

If you were interested in backing them up, you should look at this link
[Ubuntu Wiki - Apt Move Howto]("https://wiki.ubuntu.com/AptMoveHowto")

 - It will make a CD repository that you can use to backup all those packages if you wish

---

### Post by benplaut on 2006-02-20
sudo apt-get clean


^^that'll do the trick.  a bit more safe is:

sudo apt-get autoclean

---

### Post by Fred Doolie on 2006-02-20
Well, THAT was a fast anwer. Thank you.

---

