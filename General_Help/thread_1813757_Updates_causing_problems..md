---
title: "Updates causing problems."
date: 2011-07-28
forum: General Help
---

### Post by mleeeee on 2011-07-28
I've had the update manager bugging me for days to update so I eventually did yesterday. I came back afterwards and tried turning it on. I couldn't get to the login screen and had to force shut down. I tried several times, alternating between blank purple or black screens. I managed to get there by using a previous version of linux from the boot menu (which I can only get from forcing a shut down).

So how do I undo/uninstall updates in 11.04? 

Thanks to anyone who can help.

---

### Post by marin123 on 2011-07-28
so you can boot other kernels, but newest fails? is that correct?

you can try booting your newest kernel into single user mode and do update with newest version. just answer my question and i will be able to tell you more :)

---

### Post by mleeeee on 2011-07-28
I can only boot from the option on the previous versions boot menu: "Ubuntu, with Linux 2.6.35-27-generic".
The newest (2.6.38-10) fails and so does the first older one on the previous versions menu (2.6.38-8 ). I also can't get the recovery mode of the newest.

---

### Post by marin123 on 2011-07-28
[http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

try this, choose recovery (or something like that) and if you get to the desktop, try updating again.

just in step 8), instead of b, press ctrl+x to boot that kernel.

---

### Post by mleeeee on 2011-07-28
I followed exactly what that guide said but just got a blank screen. I tried using "s", "S", "single" and "Single" but it still wouldn't come up with the final step of entering the root password.

---

### Post by marin123 on 2011-07-28
did you erase words 'quiet' and 'splash' at the end of the line?

---

### Post by mleeeee on 2011-07-28
Oops, I didn't realise I had to do that. It works now.


Thanks very much for all your help! :D

---

### Post by marin123 on 2011-07-29
did you fix your problems? you know that you cant work in single mode all the time?
i mean, you can, but you would be root all the time and you can make damage to your system.

---

