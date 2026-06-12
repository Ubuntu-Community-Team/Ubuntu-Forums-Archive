---
title: "Natty. Doesn't detect external monitor"
date: 2011-05-16
forum: General Help
---

### Post by amulet on 2011-05-16
Please help, I am tearing my hair out over this...
I have connected my Samsung tv / monitor to my Toshiba laptop running Natty, and want both the external monitor and the laptop monitor to display either the same image or different parts of my desktop, I really don't mind at this stage.  
However Ubuntu doesn't detect the monitor correctly, only as "Unknown", and won't allow me to enter the correct resolution. The external (Samsung) monitor displays the message "No Signal".

Strangely also the monitor was working fine on a Vista OS, and suddenly and unexpectedly stopped working, showing the same "No Signal" message.  

The monitor is recognised and was working on another Ubuntu Natty OS, on an ancient Dell laptop until that died minutes ago.

It is really not my day! :confused:

Thank you to anyone with some good advice.

---

### Post by samMD on 2011-05-16
Weird I have a HP laptop with intel graphics ubuntu 11.04 when i hooked a external monitor it worked.

dont worry man I had same problem when I switched to ubuntu...The question is did you get a message for "Additional drivers"? click ubuntu icon "menu" and go under administration or preferences and look for "additional driverS" let it find your graphics card. If it finds it enable it (or it will do it for you) and restart.

If you have ATI or Nvidia look for it under preferences or administration (sorry I forgot since Ubuntu 11.04 now has Unity so I just search for it) open the graphics manager and for Nvidia the program should be called x server settings. Go to display configuration click on the monitor that is not activated click configure and for nvidia its "twinview". I dont know about ATI sorry...

---

### Post by amulet on 2011-05-20
Thanks for your advice SamMD, 
I am not new to Ubuntu, but this is still confusing me! 
I have AMD Catalyst Control Center for the ATI graphics card, which detects the Samsung monitor.  However, it is identified as "unknown" in preferences>monitors, so I can't configure it there at all, and the monitor still shows "No Signal".
Like I say, the monitor was working fine on Vista, but stopped working suddenly and mysteriously, and hasn't worked at all on Natty (on this particular laptop).
The same monitor and cables do work on the old Dell laptop, which has Nvidia graphics, although the picture is a little low in quality.

So, the graphics card is detected by the system, and although the ATI CCC recognises that the external monitor is connected, it is not sending the right signal to the monitor?

---

### Post by linuxinstalledfromhdd on 2011-05-20
I really wish I had some advice for this problem. This is why I avoid ATI graphics with Linux systems.

---

### Post by amulet on 2011-05-20
> **linuxinstalledfromhdd said:**
> I really wish I had some advice for this problem. This is why I avoid ATI graphics with Linux systems.

@linuxinstalledfromhdd ...
So, for future reference, i.e. once I have no hair left and have thrown the laptop at the monitor, what graphics cards would you recommend for Linux users?

---

### Post by linuxinstalledfromhdd on 2011-05-20
Nvidia. Or better yet Intel.

---

### Post by ryansinn on 2011-05-31
Ubuntu doesn't work with my NVidia 9600GT and two displays either...  Only thing that seems to work out of the box is Intel based video cards (probably because their drivers are built into the kernel!)

I can have two external displays (with rotation) configured on my X200T ThinkPad... it's the NVidia and ATI cards we use that give us trouble based on their proprietary drivers.

Nvidia drivers worked fine in 10.10 out of the box with a slight bit of xorg.conf tweaking for portrait rotation of one of the displays

In 11.04 -- I can get both screens to operate as independent displays, but I can't drag windows between them regardless of if I set them up with Xinorama or TwinView...

---

