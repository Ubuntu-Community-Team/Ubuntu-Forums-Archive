---
title: "ccleaner"
date: 2009-12-26
forum: General Help
---

### Post by karmicgaz on 2009-12-26
I used to use ccleaner a lot in windows, is there such a thing for ubuntu 9.1?

---

### Post by The Secret on 2009-12-26
You don't need it on Linux / Ubuntu.

---

### Post by karmicgaz on 2009-12-26
Why not? Surely history, recent docs etc are stored and need purging?

---

### Post by The Secret on 2009-12-26
History for what ? Firefox - there's a menu option for this purpose. Recent documents - there's a menu option to delete them.
Everything you need is already in place and can be cleaned up without installing additional software.

---

### Post by kerry_s on 2009-12-26
very true Linux dosen't keep track of everything you do.

---

### Post by Kevbert on 2009-12-26
For cleaning up there are a number of terminal commands such as
```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```
There's also a command (which escapes me) to get rid of backup files (those that start with a '~').
Wish there was a Linux program like ccleaner as it does an excellent job in Windows.

---

### Post by pricetech on 2009-12-26
> **Kevbert said:**
> 
Wish there was a Linux program like ccleaner as it does an excellent job in Windows.

Precisely.  In winders you can manually delete the stuff, clear out unwanted startup items, etc.  CCleaner just puts it all in one place and makes the task a lot simpler and quicker.

I think that's what the original poster was after.

---

### Post by NFblaze on 2009-12-26
No. I'm surprised at how common this question is. Anyway, Linux is a different OS than Windows so it doesnt really require Ccleaner, as it doesnt have registry that gets cluttered.

Though, if you want to clear out your recent documents/evidence. You can use the Places -> Recent Documents on the menubar, Delete /tmp contents, and use the Kevbert's apt-get methods.

---

### Post by steve161 on 2009-12-26
Bleachbit.  It is in the repos

---

### Post by houseworkshy on 2009-12-26
It's true tha linux doesn't really need such programs, they do however exist.  Bleach, flint and sweeper are three that come to mind.  If you use them be cautious as they will want to run with authority and errors made with them can be serious.  They can be found in the repositories and on debget.net when it's up.

---

### Post by steve161 on 2009-12-26
Agreed.  Linux is good at keeping your computer clean with some built-in maintenance.  Also, it does not come close to windows in creating tmp files and mru's.  However, I've come to like bleachbit for the ability to easily clean up thumbnails, java cache, and a few other places with one click.  It will also, if run as root, clean up all the additional language localization files that most never use.

---

### Post by karmicgaz on 2009-12-26
Thanks guys, noobies need all the help we can get!

---

### Post by scouser73 on 2009-12-26
> **steve161 said:**
> Bleachbit.  It is in the repos

+1 for BleachBit

---

### Post by MaxIBoy on 2009-12-26
BleachBit is pretty cool. I use it to get rid of translations I don't need (no, I don't need everything translated into Hebrew, Korean, Ibo, Welsh, *or* Klingon!)

---

### Post by ram4nd on 2009-12-26
There is a tool for similar thing, but that is as close as you can get to ccleaner. [http://blog.ubuntu-tweak.com/downloads]("http://blog.ubuntu-tweak.com/downloads")

---

