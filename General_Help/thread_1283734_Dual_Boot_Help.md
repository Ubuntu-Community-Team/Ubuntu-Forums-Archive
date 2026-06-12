---
title: "Dual Boot Help"
date: 2009-10-05
forum: General Help
---

### Post by lcollier93 on 2009-10-05
Right now, I have a dual boot setup with two hard drives. One is a 60GB Samsung that has linux and the other is a 320GB WD that has Windows 7. I wanted to single boot windows 7 for a little bit so that I would have a free IDE spot to plug in another hard drive that I wanted to access. But, whenever I unplug the linux hard drive and try to boot up to the windows 7 one, the screen says GRUB and won't do anything. I guess I need to reinstall the windows loader or something? I don't know but any help would be appreciated. I just want to boot into Windows 7 without the linux hard drive plugged in.

---

### Post by lcollier93 on 2009-10-05
If you could help me to just boot into linux, that would help as well. I just want to boot into one of them so that I have a free ide plug.

---

### Post by mikewhatever on 2009-10-05
It looks like W7 is on the first hdd, and that's where GRUB is installed by default, unless you change it. Reinstalling W7's bootloader should fix it. Frankly, your question has nothing to do with dual booting, and you'll probably get better help with W7 on a W7 forum. Good luck.

---

### Post by lcollier93 on 2009-10-05
OK thanks and sorry I'm new at this. haha.

---

### Post by fluffman86 on 2009-10-05
It's kinda weird the way this works, but here goes:
You overwrote the Master Boot Record of your first hard drive.  This has Windows on it.  Now, for the MBR, Grub is installed, and looking for files on Drive *2*

To start booting with just the windows 7 HDD plugged in, you need to reinstall the Master Boot Record.  You can google for how to do this.

In Windows XP, you would boot from an XP recovery disc, then go to a command line repair console, and type "fixmbr" and that was it.  Instructions for 7 will probably differ.

Once you have 7 booting again, you'll need an Ubuntu CD to reinstall grub on your Linux hard drive.  This time, you'll be able to install grub ONLY on the linux hard drive, so it won't matter if you have 1 or 2 drives plugged in.

---

