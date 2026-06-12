---
title: "nvidia resolution problem"
date: 2009-11-02
forum: General Help
---

### Post by xcitergr on 2009-11-02
I have recently updated to 9.10. Everything is ok except this,** I can not set my resolution to 1280*1024**. I have the latest nvidia drivers and when I try to do this from X nvidia settings the 1280*1024 resolution is not available, **also my display is listed as crt and it is an lcd display!** any way that i can fix this problem?

graphics card: nvidia 9400
display: eizo s1701 flexscan
 

be very detailed i am not that good as a user.

thanks in advance :p

---

### Post by lokutus25 on 2009-11-03
Which nvidia drivers do you have? Seems there are many.

---

### Post by realzippy on 2009-11-03
delete your current xorg.conf,if exists, (backup maybe better),open terminal:

**sudo nvidia-xconfig**

what creates a new one.Restart X (Log out/in),terminal again:

**gksudo nvidia-settings**

make changes,hit "apply",hit"save to X configuration file"

---

### Post by legolas_w on 2009-11-13
Thank you, it solved my problem.

---

### Post by igmorais on 2009-11-20
> **xcitergr said:**
> I have recently updated to 9.10. Everything is ok except this,** I can not set my resolution to 1280*1024**. I have the latest nvidia drivers and when I try to do this from X nvidia settings the 1280*1024 resolution is not available, **also my display is listed as crt and it is an lcd display!** any way that i can fix this problem?

graphics card: nvidia 9400
display: eizo s1701 flexscan
 

be very detailed i am not that good as a user.

thanks in advance :p

Same problem. Not solve. the only resolution available is 600x480. I use nvidia fx5500.

---

### Post by verytired on 2009-12-28
Hi I am also struggeling with this issue!  Tried installing the 190.4 Nvidia drivers the hard way.  It did not do anything.  This is realy irritating.

---

