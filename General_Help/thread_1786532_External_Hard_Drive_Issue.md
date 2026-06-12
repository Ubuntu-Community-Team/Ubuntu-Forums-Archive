---
title: "External Hard Drive Issue"
date: 2011-06-19
forum: General Help
---

### Post by Quinn Cussaine on 2011-06-19
I recently moved to Ubuntu, after hearing much about it-Im very pleased-but also in a bit of a quandary- I am trying to use my WD Terra-byte external hard-drive, and for the life of me, Im lost with the "fstab",and etc. Could anyone help me out with a step by step? It would be much appreciated!

---

### Post by dabl on 2011-06-19
Yep.

If that external hard drive is a USB drive, then the first advice is DO NOT try to set it up in /etc/fstab.  Unless you intend to have it connected at every boot, and leave it connected 100% of the time.

What happens if you simply plug in your external drive, when your Ubuntu system is running?

Also, FYI, all USB ports are not created equal -- some have enough power on the power pin, and some do not.  Try all your connectors.

---

### Post by Quinn Cussaine on 2011-06-19
Once its connected, I get an Icon on my desktop for it. Normally, in the days that I begrudgingly used windows, it would simply ask me for my password to access the drive, and it used a program call "WD Smartware", now,when connected, I get this:

Archive:  /media/WD SmartWare/Unlock.exe
[/media/WD SmartWare/Unlock.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/WD SmartWare/Unlock.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/WD SmartWare/Unlock.exe or
          /media/WD SmartWare/Unlock.exe.zip, and cannot find /media/WD SmartWare/Unlock.exe.ZIP, period.


the icon on my desktop displays the contents, such as Unlock EXE., the Virtual CD, etc, however-I get this everytime I attempt to open one. I thought I was a decent geek until i got stumped on this lol

---

