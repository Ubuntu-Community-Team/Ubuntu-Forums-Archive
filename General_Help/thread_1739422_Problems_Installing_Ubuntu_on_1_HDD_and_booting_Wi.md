---
title: "Problems Installing Ubuntu on 1 HDD and booting Win 7 on Another"
date: 2011-04-25
forum: General Help
---

### Post by Muff Muff on 2011-04-25
I just downloaded Ubuntu no problem, and put it on a DVD just fine.  I have 2 HDD in my computer, a 1.5TB (main drive, in slot SATA 0) and an 80GB (back up, in SATA 1).  I intended on installing Ubuntu on the 80GB drive, and it seemed I did so just fine; I got to the end of the process perfectly.  However, when I restart my computer to boot it up it just gives me a black screen with a white flashing underscore in the top left hand corner, kinda like a DOS screen.  I also tried booting up from my 1.5TB drive, but another black screen said that it didn't exist, along with throwing me a code, which leads me to believe that I deleted my Win7 partition by mistake.

Oh Ubuntu gods, what haz I done wrong? :(

---

### Post by Quackers on 2011-04-25
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Muff Muff on 2011-04-26
I can't do that because it won't connect to the internet for some reason, which it would with Windows.  I did copy down the error code it gives me after the installation finished and I restart it, which is when it goes wrong.  The first is a 3 or 4 digit random number, I can't really tell because it goes off the left side of the screen.
 
random #* end_request: I/O error, dev sr0, sector534624

---

### Post by oldfred on 2011-04-26
You can run the boot script from the live CD.

The error you get is because it ejects the CD and then tries to finalize something from the CD it just ejected. You can ignore that error.

Do you have it plugged in with an Ethernet cable, not wireless. Often it has to download the wireless drivers from the Internet.

---

### Post by Muff Muff on 2011-04-27
it's wireless, I'll try wired as soon as I can, I have a busy week ahead of me.

---

