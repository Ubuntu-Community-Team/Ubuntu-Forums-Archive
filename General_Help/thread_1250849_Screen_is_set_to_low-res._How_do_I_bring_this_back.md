---
title: "Screen is set to low-res. How do I bring this back up?"
date: 2009-08-27
forum: General Help
---

### Post by anthony62490 on 2009-08-27
After running a (pretty awesome) demo, my screen has been set to an obscenely low resolution. It's at the point where I can use my mouse to scroll around the desktop. I know I can fix this by resetting the computer, but how do I reset the resolution without turning the box off?

BTW, if you want to see the demo go [HERE]("http://www.scene.org/file.php?file=/parties/2001/assembly01/demo/mfx_d2.tgz"). Click the link that says "mfx_d2.tgz"
(It's pretty awesome, but there's a bit of swearing, so you may want to herd the kids out of the room. Or use headphones.)

---

### Post by beastrace91 on 2009-08-27
Check under System->Preferences->Nvidia Settings (I'm assuming you have the drivers installed for your 6200) 

Or if you do not have the nvidia drivers installed (and are just using the NV ones) it is also under System->Preferences->Display

~Jeff

---

### Post by aljoriz on 2009-08-27
enter this command at the terminal: 

gksu nvidia-settings

then edit the resolution to your taste and press save to xconfig. 
This way when you reboot you would have the resolution that you wanted and not the lowest which is 800x600

---

### Post by beastrace91 on 2009-08-27
> **aljoriz said:**
> gksu nvidia-settings

No need to really run it as super user as when the demo crashed it did not edit his default res in the xorg anyways (and I find it is better to only run programs as super user when you have to)

~Jeff

---

