---
title: "Boot hangs on timidity alsa emulation"
date: 2011-10-25
forum: General Help
---

### Post by Leed on 2011-10-25
I got a nasty problem bothering me. 

After my Upgrade to Oneiric I decided to give the restricted ATI Drivers another chance. Just like in Natty the restricted drivers where pretty laggy, so I decided to remove them again. 

That's where problems started. First of all, the Unity launcher was gone, upon boot all I got was my desktop and nautilus. After searching the forums I found a solution for this. But the second problem was and still is, that I have to boot several times and pray that I'll reach the desktop every time. 

Normally I just get a message, that timidity alsa emulation is being started (followed by an [ok]) and the boot process hangs. I can still alt+f2 into a console and startx ... but then all my unity settings are gone. So all I can really do is reboot 2-3 times until I eventually reach the desktop. Can anyone figure what the problem could be? It is annoying and I'm really not in the mood to reinstall from scratch.

---

### Post by Leed on 2011-10-28
Am I the only unlucky one suffering this problem?

---

### Post by kraylus on 2011-10-29
i updated today to 11.10 from 11.04 and now at boot it hangs when starting timidity as well. no way past it and im not savvy enough these days to root around in safe mode.

just now downloaded a fresh 11.10 and am gonna try a clean install. if i dont come back, then it worked.

---

### Post by jaredscribe on 2011-12-07
I've been using Oneiric for over a month.  Recently I installed GNU Solfege (great app, btw) , which due to my machine's sound setup, required me to get Timidity and use it as the ALSA emulator - but I made that setting from within the GNU Solfege GUI.  Now, I can't reboot - I'm hanging on the same point.

Even if I make it into recovery mode, I'm not sure how to change the setting, or do anything about this, short of removing timidity.  

To the guy above - you could always 
```

sudo apt-get remove timidity

```

I'm going to do that now.  Will let you know how it goes.
Hope this info can help someone debug this issue

---

### Post by jaredscribe on 2011-12-08
I wasn't savvy enough with recovery mode either to remove a program - didn't have write access to the the FS.  So after booting and hanging, ALT-F2 into another TTY console, I started X as root - sudo startx - and removed timidity. Now I can boot.  Now I don't have GNU Solfege though.

---

