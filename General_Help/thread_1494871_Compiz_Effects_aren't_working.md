---
title: "Compiz Effects aren't working"
date: 2010-05-27
forum: General Help
---

### Post by Schuyler on 2010-05-27
I've tried a few solutions found online... nothing seems to be working though. Compiz appears to be running, as the shortcuts are working, but the effects are not(wobbly windows etc) I am using ubuntu 10.04, with an nvidia 9800. Hardware drivers says that my drivers ARE running - (NVIDIA accelerator graphics driver). When I execute compiz --replace I get: 
```
Xlib:  extension "GLX" missing on display ":1.0".
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :1.0

Launching fallback window manager

```

If it changes anything... I am running dual monitors.

Thanks,
Schuyler

---

### Post by nichipet on 2010-05-30
My setup: Ubuntu 10.4 (Lucid Lynx), a Hannspree external monitor and a television set up as dual monitors, Compiz-switch installed.

I don't know about the error message you are getting, but I can tell you that dual monitors doesn't seem to play nice with Compiz. I can either have dual monitors or I can have Compiz working. It doesn't matter which two monitors (laptop, tv, external) I choose, I can't get Compiz to work.

Have you tested Compiz with only one monitor active? If it works on each monitor separately, then it's probably the dual monitor issue.

---

### Post by jocko on 2010-05-30
I doubt the problem is caused by dual screen. An nvidia geforce 9800 with the proprietary driver should run compiz smoothly even with dual screens.

Schuyler: Post your /etc/X11/xorg.conf and /var/log/Xorg.0.log . They may contain clues to why you get that error message (glx missing).

---

### Post by nichipet on 2010-05-30
I believe it's the total resolution. I think I read once that Compiz supports a total resolution of 2048x2048. When I dropped my resolutions to 800x600 and 1280x1024, Compiz worked.

---

### Post by jocko on 2010-06-01
> **nichipet said:**
> I believe it's the total resolution. I think I read once that Compiz supports a total resolution of 2048x2048. When I dropped my resolutions to 800x600 and 1280x1024, Compiz worked.
Compiz runs very well on my geforce GTS 250 (which is essentially the same card as the op has) at 3600x1080 (TV at 1920x1080, dfp at 1680x1050)...

And on my laptop's geforce Go 7600 (which is several levels below the  op's card) compiz runs fine at 3200x1080 (TV at 1920x1080, DFP at 1280x800).

---

### Post by gdesilva on 2010-12-03
With my Geforce 7300LE (which is ancient) the only way I can get the display to work correctly is by disabling one of the ports. When both ports are enabled it screws up the display effects.

---

### Post by gdesilva on 2010-12-03
Just noticed that in Compiz Settings Manager -> Desktop -> Clone Output option is available. I have not tried this but it may be worth a try to get both ports working. Just an idea.....


EDIT: Tried it out myself but it did not work.

---

