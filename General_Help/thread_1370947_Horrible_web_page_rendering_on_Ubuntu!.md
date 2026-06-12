---
title: "Horrible web page rendering on Ubuntu!"
date: 2010-01-02
forum: General Help
---

### Post by itsols on 2010-01-02
On my computer, the site [www.bravoclassifieds.com](www.bravoclassifieds.com) looks good on ALL my browsers (IE8,IE7, Safari, FF, Chrome) when I'm on Windows.

But if I login to my Ubuntu (7.10 as dual boot), it looks simply horrible on FF (the only browser I have on it).

Is there something wrong with the OS?

My machine has: 1024x768 res., 512MB RAM (it's a laptop).

Any ideas are really appreciated!

---

### Post by Leppie on 2010-01-02
what is it exactly that looks horrible?
is it the graphics? layout in general? things missing? wrong fonts?

---

### Post by itsols on 2010-01-02
Thank you leppie for your prompt response. Here I've attached a screenshot of the image I see. Does it look good on your screen?

I also noticed that my workspace (desktop) looks less spacious than on Windows. Could this possibly be a problem?

Thanks!

---

### Post by Leppie on 2010-01-02
if you say that your desktop looks less spacious, then it's probably some graphics settings issue. have you tried changed desktop resolution in gnome? unfortunately i'm using xubuntu and i know that the gnome control center is nothing like the xfce equivalent, so i can't guide you through that process.
what graphics card is your laptop equipped with?

---

### Post by Leppie on 2010-01-02
i attached a screenshot of what it looks like on my machine.
is that how you see it in windows?

---

### Post by itsols on 2010-01-02
I'm sorry I can't figure out my graphics card. My system is an old Dell Inspiron 1150.

I checked System -> Admin -> screen & graphics. It's set to generic lcd 1024x768 with plug n play

Thanks!

---

### Post by itsols on 2010-01-02
Yes, except for the fact that you're on a wide screen, the rest is similar to the Windows layout.

---

### Post by dcstar on 2010-01-02
> **itsols said:**
> On my computer, the site [www.bravoclassifieds.com](www.bravoclassifieds.com) looks good on ALL my browsers (IE8,IE7, Safari, FF, Chrome) when I'm on Windows.

But if I login to my Ubuntu (7.10 as dual boot), it looks simply horrible on FF (the only browser I have on it).
.........

What version FF, and what is the Subpixel Smoothing setting?

BTW, 7.10 is no longer supported: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by itsols on 2010-01-02
Ok, thanks to the two of you... I was able to dig out more info:

1. Graphics card: 82852/855GM Integrated Graphics Device (Intel experimental modesetting driver...)

2. Subpixel info: 96 dpi, smoothed for LCD. If I reduce this to 90, the desktop fonts look smaller and unclear. So I think 96 is the best.

Please advise...

---

### Post by Leppie on 2010-01-02
> **itsols said:**
> Yes, except for the fact that you're on a wide screen, the rest is similar to the Windows layout.
have you considered upgrading your system?
if you think ubuntu is too demanding on your system, you could try xubuntu karmic or jaunty (require 192mb ram).

---

### Post by itsols on 2010-01-02
Yes, I've considered the upgrade. I'm on 7.10LTS and my system is getting the upgrade for 8.04LTS as we communicate :)

But my fear is that it may not show correctly after the upgrade either.

---

### Post by itsols on 2010-01-03
Leppie and dcstar - Thank you very much for your support.

I finished the upgrade to 8.04 and the problem was fixed. I'm referring to the rendering problem of bravoclassifieds.com.

As for the space on my desktop I did something here as well... The default setting for the LCD monitor was plug n play. I changed it to Generic LCD 1024x768 and it looks great with crisp fonts.

Thank you very much for your wonderful tips and guidelines.

ATB!

---

### Post by Leppie on 2010-01-03
glad you're happy with your system now :)

set the thread to solved, using the thread tools (just above the post on top of the page)

---

