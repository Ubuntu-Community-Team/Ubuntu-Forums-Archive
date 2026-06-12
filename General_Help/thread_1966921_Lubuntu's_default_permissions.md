---
title: "Lubuntu's default permissions"
date: 2012-04-27
forum: General Help
---

### Post by ofb on 2012-04-27
Lubuntu makes new folders and files as 775 and 664, whereas Ubuntu uses 755 and 644. Anyone happen to know why?

---

### Post by MG&amp;TL on 2012-04-27
My guess would be differences in the file manager-Lubuntu uses PCManFM, whereas Ubuntu uses Nautilus.

---

### Post by ofb on 2012-04-27
Actually, I /think/ that's a function of umask, and is independent of the manager. For instance when I use Dolphin on either machine, it follows suit with what seems to be the OS default.

---

### Post by MG&amp;TL on 2012-04-27
> **ofb said:**
> Actually, I /think/ that's a function of umask, and is independent of the manager. For instance when I use Dolphin on either machine, it follows suit with what seems to be the OS default.

My mistake then, just a hunch. :)

Testing it, you are right. Hm...interesting!

---

### Post by Paddy Landau on 2012-04-27
I wonder if it is to do with the umask. This can be set in the login scripts or, I believe, in /etc/fstab.

Check your fstab. I'm not at my computer right now, but when I am I'll have a look at the login scripts for Ubuntu and Lubuntu to try to spot where it is happening.

---

### Post by Dennis N on 2012-04-27
My older Lubuntu version (11.04) creates permissions 755 (directories) and 644 (files), same as Ubuntu. So apparently a change was made in the defaults since then.

---

### Post by ofb on 2012-04-27
Aha -- it's an all-buntu thing, as of 11.10:

[http://www.mail-archive.com/ubuntu-devel-announce@lists.ubuntu.com/msg00628.html](http://www.mail-archive.com/ubuntu-devel-announce@lists.ubuntu.com/msg00628.html)

Their reason is to make sharing the filesystem easier. Makes sense, but people should be aware of the one downside I can think of -- when you upload to a website you'll need to change to 755/644.


Minor curiosity - when I re-checked 11.10 and 12.04 just now, I noticed the default user folders like Documents, Music, etc are still 755 on both.


Paddy Landau -- sorry I wasn't more clear. I wasn't after "how", but rather "why" this had been changed.


(now I have to remember how to mark a thread as Solved. that'll be a minute.)

---

