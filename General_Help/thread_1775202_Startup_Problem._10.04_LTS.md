---
title: "Startup Problem. 10.04 LTS"
date: 2011-06-04
forum: General Help
---

### Post by Ethangar on 2011-06-04
Due to work I haven't booted into Ubuntu in ages. Now that the job is wrapped up, I decided to bounce into Linux.... Grub comes up same as normal and I let it go while I go and get a coffee. All that is on the screen when I come back is a black screen with an unblinking cursor. I gave it a good 5 min in case it was doing something but nothing past that went on. No HDD activity so I had to hit the power button. This time I watched it. The splash screen flashes on and disappears, up comes the cursor. There is a flicker with a line of text but its to quick to read and back to the cursor. It does that about 3 times in 20 seconds and then just sits there. I tried one of the older version kernels but they don't work either. XP (obviously) boots fine. I can't check but I'm pretty sure that its v10.04 LTS that is installed. Recovery seems to work OK but not having done anything in there previously I don't know what to do or what its doing. It leaves me with a dos looking menu for update grub, clean space etc and defaults to Boot normally. Selecting that presents the login/password and leaves me in a console screen.

In the time since the last bootup I have swapped out an ancient nvidia 8600 for a GTX460. Could that have anything to do with the non start? In windows it still uses the same driver as my old card so I'm unsure if this would effect it. I also likely rearranged my usb devices when plugging them back in Other than that its the same machine that has run like a top. 

Any ideas on where to even start looking?

---

### Post by Joe- on 2011-06-04
Fresh Install?

---

### Post by Ethangar on 2011-06-04
No. Its an existing one. I upgraded to 10.04 from 9.10(?) It was working fine about a month ago when I was last into Ubuntu. The only changes to the system since then was the gfx card (Needed cuda) and the (likely) rearranging of what USB ports my devices are plugged into. All of them worked fine before and no new ones have been added.

Oh and 32 bit linux if that matters.

---

### Post by Rubi1200 on 2011-06-04
Try using nomodeset at boot time:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by pksadiq on 2011-06-04
I hope that you got X working before
and now at least you get the tty login ( if not from grub boot to recovery mode)
login to tty

and type:
```
sudo service gdm stop
``` 

then :
```
sudo Xorg -configure
```

then test it and if it works copy the new xorg.conf file to /etc/X11/
(don't forget to backup the old)

---

### Post by Ethangar on 2011-06-04
> **Rubi1200 said:**
> Try using nomodeset at boot time:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

Just tried this.. Same result. I'm beginning to think that its something hardware. I tried rebooting with my external HDD (usb) still attached and that makes my (usb) keyboard stop working so I can't arrow down any. Unplug it and the keyboard works as normal. I tried to boot off of a USB stick that I have linux installed on (10.10) but as soon as I plug it into the usb, again I can't use my keyboard.. This is getting weirder all the time since all this worked a few months ago.

---

### Post by Rubi1200 on 2011-06-05
Have a look in BIOS, perhaps a setting related to the keyboard and mouse was inadvertently changed?

---

