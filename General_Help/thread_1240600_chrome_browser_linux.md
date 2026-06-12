---
title: "chrome browser linux"
date: 2009-08-14
forum: General Help
---

### Post by bu2971x on 2009-08-14
I hear its getting better... If I download it and keep it on the desktop like Opera( my backup browser) will it screw anything up to use it once in awhile...??  I use fox3 usually   ubu 9.04

---

### Post by warp99 on 2009-08-14
Best thing is to use the Ubuntu Personal Package Archive (PPA) for the Chromium builds instead of downloading and installing from Google. You'll get updates through the package manager when new builds are available. Here's the link:

[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

---

### Post by aysiu on 2009-08-14
And this is how you actually use the PPA to install Chromium:
[How to Install Chromium Daily Builds in Ubuntu](http://www.psychocats.net/ubuntucat/chromium/)

---

### Post by arm-c on 2009-08-14
Chromium is not Chrome; however, Chromium served as the basis for Chrome as I recall.... so may NOT be what you are looking for...

---

### Post by aysiu on 2009-08-14
> **arm-c said:**
> Chromium is not Chrome; however, Chromium served as the basis for Chrome as I recall.... so may NOT be what you are looking for...
I've tried Chrome in Windows and Chromium in Ubuntu, and I can't tell the difference.

What's the difference?

---

### Post by bu2971x on 2009-08-14
i did the whole thing ,added the sources etc
 went fine
 still no chromium browser in synaptic
just some stupid game called chromium...

---

### Post by aysiu on 2009-08-14
> **bu2971x said:**
> i did the whole thing ,added the sources etc
 went fine
 still no chromium browser in synaptic
just some stupid game called chromium...
Paste in those commands I just gave you.

Paste the output back here.

That's how you will get help. Using the words *bogus* and *stupid* does not solve your problem.

---

### Post by Nu2Ubunutu0769 on 2009-08-15
I followed the instructions in the link above and it worked flawlessly.  Thanks!  I've missed Chrome since moving to Ubuntu 9.04.

---

### Post by P4man on 2009-08-15
> **bu2971x said:**
> i did the whole thing ,added the sources etc
 went fine
 still no chromium browser in synaptic
just some stupid game called chromium...

You installed chromium instead of chromium-browser

```
sudo apt-get install chromium**-browser**
```

edit: oops, you already got it. Oh well :)

---

