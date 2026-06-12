---
title: "Extra screensavers no longer working"
date: 2010-05-26
forum: General Help
---

### Post by Fibonacci on 2010-05-26
Hello.

I've recently installed the package xscreensaver-gl-extra, and noticed not one of the screensavers on that package works - all I get is a blank screen on all of them.
However, I remember those screensavers working under Jaunty on exactly the same hardware (didn't test them on Karmic).
How can I make them work again?

---

### Post by Fibonacci on 2010-05-29
Bump.

---

### Post by rtimai on 2010-05-29
Fibonacci, do you have a legacy nVidia graphics card, by any chance? Since Karmic the non-free nVidia drivers dropped support for some of the older cards, e.g., RIVA TNT2 such as I have. Lucid now by default installs updated nouveau drivers (open source support for legacy nVidia cards,) and GL acceleration was restored. If you're still on Karmic, upgrade to Lucid.

---

### Post by N8N on 2010-05-30
I haven't had good luck with the screensavers.  I used to run the "engine" one on 9.10 and thought it was cool as heck... but for some reason all the GL screensavers occasionally locked up my machine when I upgraded.  I just let the screen go blank now and all I have to do is hit "esc" and it gives me a login screen in a couple seconds (unless I've been away so long the computer has gone to sleep.)  I don't use compiz either.

ATI is the only video that I've been mostly happy with under 10.04 - Intel crash0rs your system, and nvidia proprietary drivers caused weirdness with my laptop and docking station (nouveau did not however.)

---

### Post by Fibonacci on 2010-05-30
> **rtimai said:**
> Fibonacci, do you have a legacy nVidia graphics card, by any chance? Since Karmic the non-free nVidia drivers dropped support for some of the older cards, e.g., RIVA TNT2 such as I have. Lucid now by default installs updated nouveau drivers (open source support for legacy nVidia cards,) and GL acceleration was restored. If you're still on Karmic, upgrade to Lucid.

I'm on Lucid, using a GeForce 6200 card with the proprietary nVidia driver.

> **N8N said:**
> I haven't had good luck with the screensavers.  I used to run the "engine" one on 9.10 and thought it was cool as heck... but for some reason all the GL screensavers occasionally locked up my machine when I upgraded.  I just let the screen go blank now and all I have to do is hit "esc" and it gives me a login screen in a couple seconds (unless I've been away so long the computer has gone to sleep.)  I don't use compiz either.

ATI is the only video that I've been mostly happy with under 10.04 - Intel crash0rs your system, and nvidia proprietary drivers caused weirdness with my laptop and docking station (nouveau did not however.)

Well, I've had some problems with ATI on my laptop, the least of which is that the Ubuntu logo doesn't look round at boot time.
But I disgress. nVidia is the only video that has worked correctly on Ubuntu for me - that is, until I upgraded to Lucid and tried to use GL screensavers.

---

### Post by Ozymandias_117 on 2010-05-30
> **N8N said:**
> ATI is the only video that I've been mostly happy with under 10.04 - Intel crash0rs your system, and nvidia proprietary drivers caused weirdness with my laptop and docking station (nouveau did not however.)

And ATI's 5xxx series can only have one monitor plugged into the dvi-0 slot until you get proprietary drivers installed, Some models you even have to set nomodeset to get them running until you can get drivers.

---

### Post by Fibonacci on 2010-05-30
Is there any way to make those screensavers work?

---

### Post by Fibonacci on 2010-06-01
Why keep the package, then, if they're not gonna work at all?

---

