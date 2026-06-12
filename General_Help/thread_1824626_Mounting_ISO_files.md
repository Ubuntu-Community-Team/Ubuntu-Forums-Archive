---
title: "Mounting ISO files"
date: 2011-08-14
forum: General Help
---

### Post by Jo.Buntu on 2011-08-14
I have the French ISO files for rosetta stone and to install them I need them to be mounted as a CD so the actual program will find them and extract them. I attempted using Furius to shove them in a loop and that didn't seem to work.

Any suggestions?

---

### Post by Sazhen86 on 2011-08-14
Hi

This might help...

[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

Cheers

---

### Post by Jo.Buntu on 2011-08-14
It didn't actually. I've tried Scripts, terminal Commands, Archive Mounter, Furius, etc.

My only idea is that rosetta stone, being in WINE, won't recognize the ISO because, if mounted anywhere out of the "drive_c" file structure, the file is in "Ubuntu Land" so-to-speak.

---

### Post by Sazhen86 on 2011-08-14
It's been a while since I used WINE, and I don't have it installed at the moment, but I seem to recall a configuration option in WINE where you can tell it which folder to use as the CDROM drive.

---

### Post by Jo.Buntu on 2011-08-14
I'll take a look through winecfg again. I'll edit this post and update after I take a look.

Alright and thanks for the tip, I was able to get it working.

For anyone that may find this thread whilst having the same issue as me here is how I did it.

Using Furius Mount the ISO in [s]loop[/s]. Not sure why I did that, just using FUSE works fine and you don't have to constantly enter your password, so do that instead. The default Mount point is your desktop and that will work just fine.

In Terminal type: winecfg

Open "drives"
click "add"
click "show advanced"
click "browse"
direct yourself to the ISO
i.e. "home/[user]/Desktop/[filename].iso"
Click "Apply"

Then go to Rosetta stone and follow the prompts for add a language.

Repeat these steps for each language "CD"
:D

---

