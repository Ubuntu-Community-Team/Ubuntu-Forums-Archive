---
title: "Vice C64 Emulator"
date: 2010-01-03
forum: General Help
---

### Post by lewisforlife on 2010-01-03
I installed Vice, the Commodore 64 Emulator with sudo apt-get install vice.  I cannot figure out how to run this package, has anyone ever used it?  I have looked in the menus and there is no menu item.  I have also tried running 'vice' from shell.  How can I tell where this was installed to?

---

### Post by lewisforlife on 2010-01-14
Anybody?

---

### Post by junapp on 2010-01-14
If you go into synaptic, search for 'vice', right click on it, select properties, and look for the installed files in /usr/bin, they will likely be what you need to type to get the program to run. 

also from the notes for vice:
> 
This package does not contain the various ROM images needed to
actually use the emulators; they are available separately from other
locations (see the README.ROMs file).  A corporation in the
Netherlands called Tulip holds the copyrights to the ROM images, and
redistribution is not permitted, but VICE itself is unencumbered.
did you take a look at the README.ROM file?

---

### Post by lewisforlife on 2010-01-14
Vice is not even showing up in the graphical package manager.  I have "All available applications" selected, but the c64 emulator does not show up when performing the search.  Is there a way I can find this info out from the shell?  I can do:

```
dpkg --get-selections | grep vice
vice         install
```

So I know it is installed.

---

### Post by junapp on 2010-01-15
could try
dpkg -p vice
dpkg -c vice

see:[http://www.cyberciti.biz/howto/question/linux/dpkg-cheat-sheet.php](http://www.cyberciti.biz/howto/question/linux/dpkg-cheat-sheet.php)

---

### Post by cronos on 2010-01-15
I don't know why it is not working for you.  When I installed Vice via Ubuntu Software Centre, the files were found in the 'other menu'.

To run vice from the terminal, type: x64

Vice files are located in: /usr/bin/x64

Unfortunately, Vice does not come with ROMS due to copyright reasons.  So, you will need to find the ROMS and copy all the ROMS into <user>/.vice/C64 (case sensitive)

Alternatively, you could download the Vice source file and compile it to avoid hassle of searching for ROM files.

---

### Post by yazmonium on 2010-02-17
ok, so one has looked at this thread in a month, but maybe I can resurrect the discussion.

I found the roms at [http://www.zimmers.net/anonftp/pub/cbm/crossplatform/emulators/VICE/old/index.html](http://www.zimmers.net/anonftp/pub/cbm/crossplatform/emulators/VICE/old/index.html)

I put them in ~/.vice/xx and in /usr/lib/vice/xx, where xx is C64, VIC20, etc, but I still have the same error.  Does anyone know where vice is looking for them?

---

### Post by arkor on 2010-02-28
Hi, I am also trying to run Vice on Xubuntu 9.10 Karmic Koala. I found this link.
[http://thejungleonline.wordpress.com/2009/08/10/playing-commodore-64-games-on-vice-versatile-commodore-emulator/](http://thejungleonline.wordpress.com/2009/08/10/playing-commodore-64-games-on-vice-versatile-commodore-emulator/)

At the above link it mentions.
&quot;You also need to copy the ROM files from the C64 into the ~/.vice/C64 folder. Once completed this folder should contain four files and these are basic, chargen, kernal and 1541.&quot;


I put the ROMS into the ~/.vice/C64 folder
Still at the command prompt when typing x64 it give the error 
&quot;Couldn't load kernal ROM 'kernal' Machine initialization failed

Like yazmonium said. Where to to put the files?

Oh the day I get this emulator working will be a fine day indeed. Until then, more searching, & inquiring, I guess.

---

### Post by mocha on 2010-04-01
I don't think you guys realized, the "kernal" file in that archive you downloaded was named "kernel" thus the error message about not finding it.....

---

### Post by Grishka on 2010-04-05
[32-bit VICE 2.1](http://www.mediafire.com/?senc0ndjfxm).
[64-bit VICE 2.1](http://www.mediafire.com/?myxnmcsy2ch).

I didn't have time to package VICE 2.2 yet, will do when possible.

---

### Post by arborinfelix on 2010-05-15
hi guys...
i got it working.
you will need 4 rom files. 

kernal
basic
chargen
c1541

the roms should have no extensions like ".rom" ONLY FILE NAMES NO EXTENSION NAMES (case sensitive)
the roms should be in the folder <name>/.vice/C64  (case sensitive)

---

### Post by parovelb on 2010-06-26
Where do I get these roms?

---

