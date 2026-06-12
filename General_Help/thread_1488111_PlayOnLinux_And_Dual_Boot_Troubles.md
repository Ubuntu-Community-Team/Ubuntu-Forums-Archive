---
title: "PlayOnLinux And Dual Boot Troubles"
date: 2010-05-19
forum: General Help
---

### Post by Laraso on 2010-05-19
Hey, just got Ubuntu today and I have to say I am quite impressed.

Everything is fine and cool, installation when without a hitch, but I am having problems with dual booting.

I was originally going to have a dual boot with Ubuntu and Vista, I  did everything I was supposed to, but after installing Ubuntu it only  allows me to boot into XP, which is not installed onto my HD.

I need to know if there is any way I can add Vista to the boot loader,  please, any advice at all would be much appreciated.

Also, I am trying to install Supreme Commander, and when it asks me for the location of my CD-Mount, I hit a dead end. I bought the game online via [www.direct2drive.com]("http://www.direct2drive.com"), so I don't have a CD. Is there a way to tell it this so I can begin playing?

---

### Post by Laraso on 2010-05-19
bump

Sorry...

---

### Post by marshmallow1304 on 2010-05-19
PlayOnLinux is just some scripts and configurations for using Wine.  Try running the installer with Wine (right-click, open with Wine).

For booting Windows, try opening a terminal (Applications->Accessories->Terminal) and running
```
sudo update-grub
```


Also, it is recommended that you wait 24 hours before bumping.

---

### Post by Laraso on 2010-05-19
Sorry about that.

OK, I typed sudo update-grub into the terminal, it told me it was generating some sort of configuration file and it said it found stuff.

After it completed, I rebooted my computer and all it did was add Ubuntu to the boot loader twice.

Any way to add Windows Vista Home Premium to the boot loader? Still real new to Ubuntu.

---

