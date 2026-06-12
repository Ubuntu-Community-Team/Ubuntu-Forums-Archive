---
title: "Gave up waiting for root device..Dropping to a shell!!!"
date: 2010-11-29
forum: General Help
---

### Post by adamogardner on 2010-11-29
I was upgrading online through my android phone's easytether app.  My phone rang, and I was bounced offline.  When I came back the upgrade did not resume, and when I tried to start over, dpkg and whatever was busy so I closed all my windows and tried to reboot.  This is where I ended up:
Here is a screenshot:

---

### Post by adamogardner on 2010-11-30
I forgot to mention that I don't know what to do and could use some direction.  Thankyou.

---

### Post by adamogardner on 2010-12-04
Is it recommended then that I reinstall?  I was hoping to get inside and move some things around, but...
How long is too long to have this console up?  If I don't bump will I get buried?
Thanks

---

### Post by AlphaLexman on 2010-12-04
Try this:
```
sudo dpkg --configure -a
```

---

