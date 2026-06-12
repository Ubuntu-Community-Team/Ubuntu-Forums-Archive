---
title: "Log In Sound on Ubuntu 12.04"
date: 2012-04-26
forum: General Help
---

### Post by craig10x on 2012-04-26
I just re-installed ubuntu 12.04....on my beta2 install, it listed the gnome start up sound in the menu which was unchecked...when i checked it i got the "jungle drum sound"...

On my re-install, gnome start up sound is not listed on the start up applications drop down...if i wanted to add it to my start up application drop down (so that i can check the box and make the sound come on) what should i enter into that start up window (using the "add" button)...?

Thanks... :)

---

### Post by grahammechanical on 2012-04-26
Try browsing to /usr/share/gnome/autostart/GNOMELoginsound

Regards.

---

### Post by craig10x on 2012-04-26
thanks but still not sure what to do...can someone explain the easiest way to get it going? 

I was also wondering why it appeared on the beta2 but does not appear on the final release (the start up sound is no longer listed in the start up menu)...

---

### Post by craig10x on 2012-04-26
By the way, i have my "alert sounds" on from the sound menu (not muted) and i raised the volume up on it more then 80% of the way up...
where do i find this item since it doesn't appear in the start up menu on the final release install?

---

### Post by baltisalty on 2012-07-22
Try adding this command (copy/paste) into a new entry on start up apps...


/usr/bin/canberra-gtk-play --id="desktop-login"

---

