---
title: "Upgrade causes freeze!"
date: 2010-05-26
forum: General Help
---

### Post by OllieGab on 2010-05-26
I upgraded from 9.10 to 10.4 and apart from some minor hitches (that have now been resolved) most things are working as expected.
However, now suddenly the pc freezes up after an hour or so, no warning whatsoever. The mouse and the keyboard don't respond at all. Alt+SysRq+REISUB does not work. Completely non-responsive.
I have to turn it off "forcibly".
Any ideas where I could start looking?:confused:

---

### Post by wilee-nilee on 2010-05-26
> **OllieGab said:**
> I upgraded from 9.10 to 10.4 and apart from some minor hitches (that have now been resolved) most things are working as expected.
However, now suddenly the pc freezes up after an hour or so, no warning whatsoever. The mouse and the keyboard don't respond at all. Alt+SysRq+REISUB does not work. Completely non-responsive.
I have to turn it off "forcibly".
Any ideas where I could start looking?:confused:

Pop a live cd and run it long enough to see if it does this again if not, pull what you need off and do a fresh install. Or load thumb with a persistent setting it will actually run as fast as the hd if you have usb2

---

### Post by OllieGab on 2010-05-26
I looked around the forum (stupidly enough **after** I posted my inital message) and I realised that this problem seems to cause a lot of grief to loads of people.
At the moment I have started my machine up with the second kernel version on the menu list and so far nothing 'has happened'. Let's see if this holds. Otherwise I will try your suggestion. 
I have separate home, boot and root partitions. If I do carry out a clean install will I keep most of the set up I've got now? Ie installed applications and customisations of this that and the other?

---

### Post by -humanaut- on 2010-05-26
I'd recommend a fresh install. Just back up your files also when your partitioning if you want to (this is what I do) create a 10-15 GB fat32 partition that you can back-up your important files to and keep it unmounted so if your system goes down atleast you don't lose import files.

---

### Post by wilee-nilee on 2010-05-26
As the other posts suggest you can set up a home partition, but the fresh install will just be the base install you will have to do the customizing. If you have a apt source list that has extras beyond the regular release you want to save those and the keys, or at least know how to get them back. I'm not sure why the suggestion is a fat type partition I wouldn't do it that way but we all do things differently.

---

### Post by -humanaut- on 2010-05-26
> **wilee-nilee said:**
> As the other posts suggest you can set up a home partition, but the fresh install will just be the base install you will have to do the customizing. If you have a apt source list that has extras beyond the regular release you want to save those and the keys, or at least know how to get them back. I'm not sure why the suggestion is a fat type partition I wouldn't do it that way but we all do things differently.

Sorry maybe I wasn't clear I have a separate / & /home on EXT4 my fat32 isn't mounted and I use it to strictly backup files I try to keep it away from everything else on my system.

(I use fat32 for a backups because its simple to access the files on any rescue c.d. I can get my hands as its pretty much universally accessible from most Linux distro's)

---

### Post by OllieGab on 2010-06-11
Does anyone know if this problem has been sorted yet? It seems as if quite a few of us had this 'freeze problem' when upgrading to 10.4.
I also tried a clean install on a net book, also with the same result. Worked for a while and then total stop! Using an earlier kernel seems to fix some of the problems, at least on my machine!

---

