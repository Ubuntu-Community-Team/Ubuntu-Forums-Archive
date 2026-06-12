---
title: "Back up downloaded updates"
date: 2006-03-24
forum: General Help
---

### Post by Shampyon on 2006-03-24
Is there any way to back up the updates I've gotten through apt-get, the update manager and Synaptic to a cd? I may have to reinstall Ubuntu after messing with some stuff, but I don't want to use more bandwidth downloading all those updates again. I don't want to just back up the whole system, because I've made some changes that'll screw up the new install.

Also, I read in another thread about being able to download images of the repositories. Is this too new for me to be able to get it from an online store, saving my bandwidth? Or perhaps any plans for Canonical to realease cheap copies of the discs for users?

---

### Post by Sutekh on 2006-03-24
Easiest ways

[Ubuntu Wiki - Apt Move Howto]("https://wiki.ubuntu.com/AptMoveHowto")

and

[Ubuntu Wiki - Apt Move Howto (Simple)]("https://wiki.ubuntu.com/AptMoveHowto/simple")


[Ubuntu Starter Guide - Backup and Restore apt-get cache]("http://www.ubuntuguide.org/#backuprestoredownloadedrepositoriescache")


You could also create a local repository, on say another partition that won't be formatted when you re-install Ubuntu.  You can add that to your sources.list and "download" your packages from there.

---

### Post by Shampyon on 2006-03-24
The first link timed out, the third link went to a Microsoft page (accident, or them being sneaky buggers?)

That middle link, though, looks pretty darn easy. Thanks heaps, I'll get on that right away! :-D

---

### Post by Sutekh on 2006-03-24
Accident / my fault

I made a typo,  if a url is **http://http://**  it goes to microsoft.com

Anyway the first link is just a more involved version of the middle one.  Good luck!

---

