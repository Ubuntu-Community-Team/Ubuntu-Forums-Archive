---
title: "Plymouth and AHCI"
date: 2011-09-28
forum: General Help
---

### Post by x-shaney-x on 2011-09-28
I have just returned an HP laptop (many issues) and now have an Acer (I forget the model number off-hand).

Both had the same problem on boot:

Instead of the nice plymouth splash, I had blocky looking "ubuntu/kubuntu" text with dots underneath.
Unlike many plymouth complaints, where the text is large and in the centre of the screen, this is in the top corner and small, indicating plymouth IS running at the correct resolution and there is some other problem.

After reading an article, I tried going into BIOS and changing the hard drive mode from AHCI to IDE.

On both laptops this made the boot process run as normal.  The correct looking logo and at the correct resolution.

Problem is, when switched to IDE mode, windows refuses to boot.

Can anyone tell me what the problem is here and how I can fix it?
I know the boot screen isn't a huge issues but it will just eat away at me knowing it's not right.

---

### Post by LowSky on 2011-09-29
yeah the problem is that Windows only has the AHCI drivers running. so switching to IDE makes it crash. You should stay in AHCI!!! 

What does it matter if the splash screen is off center? Heck mine is just a blank screen because Nvidia's driver isn't supported.

---

### Post by x-shaney-x on 2011-09-29
Like I said, it's just the fact I know it's not working how it should just gets to me.

Besides which, since most modern computers that I know of come with AHCI enabled, is this not a linux related bug that needs fixing?

---

