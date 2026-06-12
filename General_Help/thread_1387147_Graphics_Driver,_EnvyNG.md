---
title: "Graphics Driver, EnvyNG"
date: 2010-01-21
forum: General Help
---

### Post by leeds_shrew on 2010-01-21
Let's start from the beginning:

Everything was fine once I installed Karmic, except that my screensavers had very jumpy graphics, and I couldn't play a simple game like supertuxkart because the graphics had massive holes in it. I tried to do something about this by installing EnvyNG thinking that perhaps I had the wrong drivers installed or something (I'm really not that ofay with any of this technical stuff...)

On running EnvyNG and enabling the only ATI driver that appeared (not any of the 3 NVIDIA drivers) [NB: All 4 of these drivers have a big red cross in both the 'recommended' and 'compatible' columns - as they were the only ones that appeared I assumed they were OK but now having 2nd thoughts about that!] I was asked to restart my computer and did. All went predictably wrong, I ran it in safe mode and disabled the driver I'd just installed.

Unfortunately, I am now looking at a terrible display. I have a widescreen laptop and it's not got the right resolution.  When I go to System -> Preferences -> Display it tells me "Monitor: Unknown" (It knew it before).

I'm going with a hunch here: EnvyNG uninstalled my graphics driver, and I disabled the one it replaced it with?  When I go to System -> Administration -> Hardware Drivers it doesn't help me.

A few questions:

1) What has gone wrong do you reckon?
2) How do I get Ubuntu to recognise my monitor again?
3) How can I get my display back to how it was [or preferably]
4) How do I sort it so that my screensavers are perfect and I can play supertuxkart (which may well be rubbish anyway!)?

Much obliged to all of you who know what's going on but help out us amateurs anyway!

G

---

### Post by philinux on 2010-01-21
Open a terminal and do this.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.back
```

Log out then back in.

If it fails to work then reverse the instruction above.

---

### Post by leeds_shrew on 2010-01-21
Thanks, Phil. Such a simple command, so effective! Everything is back to how it was and it now recognises a laptop monitor. Do you know what I did wrong? (Presumably those big red crosses in EnvyNG mean 'not good' as opposed to 'good'!)

Of course I still can't play that stupid game (maybe it's amazing...) and I assume that my screensavers are still rubbish... Does anyone have any idea how I could improve them? System -> Preferences -> Appearance seems to make no or little difference.

Cheers,

G

---

### Post by leeds_shrew on 2010-01-21
Is there no [SOLVED]ish button?! :D

---

