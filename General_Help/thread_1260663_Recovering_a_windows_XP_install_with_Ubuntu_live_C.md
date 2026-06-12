---
title: "Recovering a windows XP install with Ubuntu live CD - Conflicting programs on startup"
date: 2009-09-07
forum: General Help
---

### Post by themusicalduck on 2009-09-07
Sorry if this isn't completely Ubuntu related, but I hope someone can help me here.

I've been working on a laptop for somebody, just cleaning it up and removing unnecessary things for them. I decided to install Avast, Ad-aware and spybot all with the intention of doing scans and cleaning things up. After installing all three, the laptop now crashes on startup, suggesting that Avast and ad-aware (or something) are conflicting on startup (I guess cause apparently ad-aware has a startup daemon now..)

I've been posting on a windows forum and they've suggested logging in as an admin, which I can't because it logs into the user account automatically. They also suggested using ERDcommander, which is like a live Windows OS for recovery. It looked promising, but it locks up every time after about 30 seconds of use. I managed to get it to check for system restore points on the XP install, but apparently there are none anyway.

The only thing I can get it to do of course, is boot into an Ubuntu live session..

Does anyone have any ideas what could be done to remedy it? I'm beginning to think I'm going to have to re-install windows and wipe this guys drive.

One thing for sure is I'm never offering to fix someone's computer again.

---

### Post by fluffman86 on 2009-09-07
Most of the time, after a bad virus infection, an OS install is usually the way to go.  Of course, I usually recommend another OS, like Ubuntu. :)

That said, can you get to Safe Mode? That usually lets you log in as the official Administrator account.

Also, I recommend Bart PE as a windows recovery/repair environment.  It's great, but a little difficult to build right the first time.

---

### Post by bumanie on 2009-09-07
Booting into an ubuntu live cd should give you access to the windows hard drive, but you will have to make yourself root to be able to remove anything. It is possible to type sudo -i and be root for the live cd session, as far as I remember. If you don't mind command line, Trinity Rescue Kit could be worth looking at. It is designed specifically for the purpose of fixing windows machines. Also if you have an external hard drive large enough to copy the guys partition/hdd on to, you could do that with dd commands (or copy the partition with gparted) and attempt the recovery knowing you have a bit for bit copy that can be put back on the computer if things don't work out. The other thing you could try would be to copy any important files and reinstall windows anyway - as said by the above post, once windows has a bad virus infestation, re-installation is usually the best thing and it never hurts starting off with a fresh windows' registry as well.

---

### Post by themusicalduck on 2009-09-08
> That said, can you get to Safe Mode? That usually lets you log in as the official Administrator account.

I tried it before, safe mode blue screens after a few seconds of booting up :/

The original plan was actually to re-install, but I don't have a copy of XP home (professional, but not home) and there is no recovery partition. I might ask if he has a recovery CD, but you know people aren't great at holding onto those.

I'll have a look at trinity.

EDIT: Changing the names of folders for any ant-virus related software in program files fixed it in the end and didn't seem to cause any problems.

---

