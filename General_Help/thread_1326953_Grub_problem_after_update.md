---
title: "Grub problem after update"
date: 2009-11-14
forum: General Help
---

### Post by PC_load_letter on 2009-11-14
So I installed Karmic 64bit last week on my Vostro 1400 laptop w/ Nvidia 8400GS. Everything was great! I started the update manager, I remember it asked me which Grub version I want, I sticked to the default choice, finished the update & turned the laptop off.

Today, I can't get to the login screen. Right after the bright Ubuntu symbol, I get a message "failed to blah blah, using the 1064x768 version instead". This same message appeared last week as well but the system booted with no problems then. That was both before and after installing  the Nvidia driver.

What happens now is that I don't get to see the brown splash screen, and the screen starts to flicker forever. I turned it off from the on/off switch and using Jaunty now. 

Any idea howto fix this?
Thanks.

---

### Post by PC_load_letter on 2009-11-14
OK, restarted in recovery mode, the error message was:
nvidia driver cannot be found, no screens available. So I edited xorg.conf to use nv instead, rebooted. Then I reinstalled the nvidia driver v185, then rebooted. Now I can't enable desktop effects, what the heck is going on?

??????

---

### Post by upapilot on 2009-11-15
Your graphics driver has probably got corrupted....try reinstalling Ubuntu and then tell me the results...

---

### Post by PC_load_letter on 2009-11-15
Are you serious? Install Ubuntu Karmic from scratch? 
Everything is working except compositing. I installed Compiz (just for testing), and when I typed:```
$ compiz --replace
``` in terminal, here is what I have got: 
```
Checking for Xgl: /usr/bin/compiz: 421: xvinfo: not found
not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: /usr/bin/compiz: 421: xdpyinfo: not found
not present. 
aborting and using fallback: /usr/bin/metacity 
```
Compositing w/ metacity doesn't work either.

If I have to install Karmic from scratch, fine, but how would I guarantee even then that this same problem will not happen again?

---

