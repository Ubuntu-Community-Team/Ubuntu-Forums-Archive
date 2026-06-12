---
title: "upgrade from 9 to 10 messed with automount"
date: 2010-05-05
forum: General Help
---

### Post by dd1linux on 2010-05-05
I have a 500GB external usb drive to hold all my music, videos, etc.. it used to mount to /media/Storage, but after I updated the os, it created a new folder called Storage_ and during boot I get an error (something like /dev could not be loaded) and when I try to open up amarok it says it can't access /media/Storage.  What's weird is that drive isnt even listed in my fstab.  what is the best way to fix this problem - maybe even just deleting /media/Storage, but i dont think that will fix the startup error.

---

### Post by nitstorm on 2010-05-05
ubuntuforums.orgubuntuforums.org/newreply.php
Add the external drive (/media/Storage) to the fstab. Look [here]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by dd1linux on 2010-05-05
Ok, but if its not in the fstab, how is it getting auto-mounted?  Would u like to see my fstab?

---

### Post by Peter09 on 2010-05-05
I think Ubuntu mounts all usb devices by default - its just that its not mounting it automatically where you used to mount it when it was in your fstab.

---

### Post by dd1linux on 2010-05-05
I see, so the update basically re-did my fstab

---

### Post by dd1linux on 2010-05-05
Well, I added it to my fstab, but neither problem was resolved.

---

### Post by dd1linux on 2010-05-05
Ok I fixed the amarok problem by removing the old directory, but at boot i still get:  

mount: mounting none on /dev failed: No such device

seems a little redundant, is that a problem in my fstab?

---

