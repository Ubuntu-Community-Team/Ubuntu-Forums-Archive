---
title: "Touchpad working at login screen but not logged in"
date: 2011-02-24
forum: General Help
---

### Post by Captain Giraffe on 2011-02-24
I have a problem with my T60 touchpad. It works fine at the login screen, but stops working when I login. 
I works again at the login screen when I logout.
Is there a setting I have overlooked? Can't find anything relevant. 
I recently installed disper(not in the default repos) for switching between one and two displays. Not sure at all if that is the culprit. 
Tried "remove (completely)" disper to no avail.

Also tried replacing xorg.conf with the backup.

dmesg doesn't show anything of interest.

I'm om maverick.

Any ideas on how to debug this would be greatly appreciated!

---

### Post by Captain Giraffe on 2011-02-24
```
synclient touchpadoff=0
```
did the trick

---

