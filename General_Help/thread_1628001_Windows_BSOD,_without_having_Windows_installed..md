---
title: "Windows BSOD, without having Windows installed."
date: 2010-11-22
forum: General Help
---

### Post by Coriform on 2010-11-22
I am experiencing a very strange problem.  I was given an older Dell Inspiron E1505 laptop maybe eight weeks ago.  It had Windows XP installed on it; I reformatted the hard drive and installed Ubuntu.  For the most part, everything is working fine.  However, very occasionally (as in, this has happened 2, maybe 3 times) when I boot up the machine, before reaching the Ubuntu splash screen I will get a Windows Blue Screen of Death.  This isn't so much of a problem as it is a curiosity - **how is this even possible?** As I mentioned, there is no dual boot.  I ran fdisk to check my partitions and everything seems normal:

   ```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14223   114240512   83  Linux
/dev/sda2           14223       14594     2977793    5  Extended
/dev/sda5           14223       14594     2977792   82  Linux swap / Solaris
``` I'd like to know if anyone else has experienced something like this, and has been able to figure it out.

---

### Post by mastablasta on 2010-11-22
windows screen? are oyu sure it's wondows and not BIOS screen? Some older BIOS and maybe also some new ones had blue BIOS screens. only you had to access it. does the computer boot normally? is there only one beep?

---

### Post by AnotherMuggle on 2010-11-22
> **Coriform said:**
> I am experiencing a very strange problem.  I was given an older Dell Inspiron E1505 laptop maybe eight weeks ago.  It had Windows XP installed on it; I reformatted the hard drive and installed Ubuntu.  For the most part, everything is working fine.  However, very occasionally (as in, this has happened 2, maybe 3 times) when I boot up the machine, before reaching the Ubuntu splash screen I will get a Windows Blue Screen of Death.  This isn't so much of a problem as it is a curiosity - **how is this even possible?** As I mentioned, there is no dual boot.  I ran fdisk to check my partitions and everything seems normal:

   ```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14223   114240512   83  Linux
/dev/sda2           14223       14594     2977793    5  Extended
/dev/sda5           14223       14594     2977792   82  Linux swap / Solaris
``` I'd like to know if anyone else has experienced something like this, and has been able to figure it out.

Very odd.  Are you absolutely sure it's a "Windows" blue screen and not BIOS related or something?

If it's definitely a Windows blue screen then you have something attached to the computer with Windows on it (most likely in broken form), it must be loading from somewhere...

---

### Post by HermanAB on 2010-11-22
You are not running the screensaver known as BSOD are you?  That one can simulate BSODs from many different computers, even Apple II and Atari.

---

### Post by elliotn on 2010-11-22
its bios as he says it happens before ubuntu boots. what does the bsod says!

---

### Post by Coriform on 2010-11-22
Thanks for the replies!  I can't remember specifically what the BSOD said.  I recall it specifying a memory dump, and I THINK it mentioned Windows (something about "Windows will be shutdown to prevent" etc etc) ... In all likelihood, the "BIOS BSOD" theory sounds probable. Maybe the BIOS manufacturer included the name "Window" for familiarity?  I'll actually record the information if/when this happens again.

---

