---
title: "windows install help"
date: 2011-02-05
forum: General Help
---

### Post by skrizzy on 2011-02-05
i have UNR installed on my netbook but would like to install windows 7 over UNR, not a dual boot. i have what i need but i cant install it to usb because i cant run .exe files in ubuntu and wine is not working for me. please help me. i think i bit off more than i can chew with installing over windows and would like to go back.

---

### Post by doogie256 on 2011-02-05
i'm pretty new here too, but would it be easy to just use a USB cd/dvd drive to boot the install disk off of?

---

### Post by efranor on 2011-02-05
i had a few problems with that myself when i started and i came to the conclusion that if i install windows first the linux grub overrides the windows booter, also that just lets you select the kernel you wish to use for that session. Installing linux should be enough for you to go for some coffee or something like that, just use sudo apt-get install and just list all things you want to have on it. It should take you some 10 minutes and all of it should work... hope i helped.

---

### Post by skrizzy on 2011-02-05
@efranor im not sure you understand my meaning. i already have ubuntu installed but i would like to completely install windows 7 over ubuntu.

im not sure how to use a usb installer tool for ubuntu because everyone i come across is for use with windows and i cant get wine to run correctly. is there some code i can put into the terminal or a script i can run or anything?

---

### Post by Chizzleface on 2011-02-05
If you're booting from a disk, you need to make sure your BIOS is set to run from D: before C: so that it will auto-detect the installation disk. That's how all OS software is installed.

---

### Post by Chizzleface on 2011-02-05
Apologies, didn't realise you were on a netbook - use this program [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) it should allow you to run Windows 7 installation from usb key.

---

