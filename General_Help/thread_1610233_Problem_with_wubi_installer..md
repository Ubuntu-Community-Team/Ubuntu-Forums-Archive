---
title: "Problem with wubi installer."
date: 2010-10-31
forum: General Help
---

### Post by Ali J on 2010-10-31
Hello everyone,

I have been having a problem installing Ubuntu 10.10 with the 'wubi' installer. You see, I downloaded the image and then extracted the files from it and then launched the wubi installer from the folder where I extracted the files for the Ubuntu disk and when I would go to install it, it would try download the image again. But then I tried after I had reinstalled my version of windows(Windows 7) and then it worked for some reason. But now Ubuntu got stuck for a very long time and would not respond so I turned it off from the power button on my Laptop. Then when I tried boot up, it would just give me the black screen with the underscore and would not go any further than that. I then uninstalled it and tried reinstall it but I have the same problem as before, it tries download it. Even when I disconnect, it just gives me the error that it could not download. What should I do. Any help is appreciated, thank you.

Ali J.

---

### Post by cpmman on 2010-10-31
You need to have the .iso image in the folder where you run wubi - not the extracted files.  Click on the WubiGuide link in my signature for details of installation options.

---

### Post by P4man on 2010-10-31
May I suggest you reconsider your idea of using wubi at all?
If I where you, Id burn the iso to a cd (or create a bootable USB with unetbootin) and boot from that. That lets you test drive ubuntu with no risk, it runs off the CD (or USB). 

If it turns out to work as you expect, install it from that live session, so it gets installed on its own partition, you get a proper dual boot, and you have no wubi issues that you will probably encounter otherwise. Apologies to the above poster, but Im not a wubi fan. Too many problems with that.

---

