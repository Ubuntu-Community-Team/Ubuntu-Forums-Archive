---
title: "Open terminals at startup"
date: 2010-09-12
forum: General Help
---

### Post by BuSaad on 2010-09-12
Hi everyone

This is my first post EVER so please be gentle with me!!! ;)

I have Lucid Lynx (10.04) installed, and have this annoyance with various terminals and the Help Menu automatically opening at startup. So every time i boot up i get a screen full of open terminals:
1. Ubuntu Help Centre
2. File Browser
3. Desktop Terminal

plus a few others.

I have tried looking at the Startup menu under Preferences but there is no entry for any of the above. Would really appreciate any pointers and ideas anyone can give.

Thanks in advance.

---

### Post by TeoBigusGeekus on 2010-09-12
In the same menu, look for something like Save Session and disable it. Perhaps you saved a session and ubuntu keeps trying to open your saved apps again.

---

### Post by BuSaad on 2010-09-12
> **TeoBigusGeekus said:**
> In the same menu, look for something like Save Session and disable it. Perhaps you saved a session and ubuntu keeps trying to open your saved apps again.


Hi TeoBG and thanks for your response. Did you mean the OPTIONS tab on  the Startup menu? The 'Automatically remember running applications when  logging out' option is definitely disabled. Do u have any other ideas?

---

### Post by BuSaad on 2010-09-12
Hey TeoBG... THANKS!

Your idea got me thinking... what if i close everything and click 'Remember currently running applications'?

What i did was make sure that there were no running applications. Then i clicked 'Remember currently running applications' and rebooted. At startup i had a clear Desktop! :D

So at the risk of starting a new thread, does anyone know which file stores the 'currently apps'?

Thanks a lot!

---

### Post by TeoBigusGeekus on 2010-09-12
There's not actually a file, but you can put your startup scripts in
```
/home/yourusername/.config/autostart
```

---

### Post by BuSaad on 2010-09-12
Thanks again TeoBG

I will mark this thread as solved, and go and read up about startup scripts and saving sessions.

All the best for now.

BuSaad. :D

---

