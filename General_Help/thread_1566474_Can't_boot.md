---
title: "Can't boot"
date: 2010-09-02
forum: General Help
---

### Post by evworld on 2010-09-02
I tried to fix splash screen resolution on boot up in 10.04 from instructions I found on the net.  I updated lines in grub.   Now when I boot I see the dual boot menu but hit linux i just get a black screen.  I can't get into my system from there.  Any help?

---

### Post by anirudhtomer on 2010-09-02
try running ubuntu in recovery mode & undo the changes you made.
I donno if it would work(Trial n Error) but I would have tried this in such situation

---

### Post by evworld on 2010-09-02
> **anirudhtomer said:**
> try running ubuntu in recovery mode & undo the changes you made.
I donno if it would work(Trial n Error) but I would have tried this in such situation
 
 
I did try that and i just get a black screen on that option too.

---

### Post by evworld on 2010-09-02
Never mind I am reinstalling the operating system.

---

### Post by Elboully on 2010-09-02
And does it work now?

---

### Post by gypsumwolf on 2010-09-02
> **evworld said:**
> Never mind I am reinstalling the operating system.

Would sudo update-grub, or a fresh reinstall of grub work?

---

### Post by evworld on 2010-09-04
> **gypsumwolf said:**
> Would sudo update-grub, or a fresh reinstall of grub work?
 
 
I did a fresh install.  I tried update grub with directions on the internet using alternative cd and it still led me to a black screen after I seen the dual boot menu.  I think It had something to do with video drivers.  
 
I just reinstalled the whole operating system and I will leave the ugly big ubuntu screen at boot.  It is working but it would be nice to see the correct resolution at startup.

---

### Post by JimBuntu on 2010-09-04
Funny, I just posted a new thread about why the splash screen is now low resolution. Upon first install it was nice and clear and crisp. I'm wondering if it has anything to do with enabling the Nvidia drivers. I'm on the 195 drivers and noticed the splash screen change after I activated the driver.

---

