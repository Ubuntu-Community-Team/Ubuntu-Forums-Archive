---
title: "dual screen on lucid"
date: 2010-09-14
forum: General Help
---

### Post by capybara! on 2010-09-14
Dear all,

I try to set up a second screen on lucid. After plugging in, my second screen is mirroring the first one. 
I tried configuring with xrandr and grandr to have a real 2 monitor setting, but this does not work.

Other solutions, like Xinerama and TwinView require editing my xorg.conf. When I looked for /etc/X11/xorg.conf , it was not there. A 'locate xorg.conf' doesnt find it either. Is this some new X version that does not need a xorg.conf?
I tried 'dpkg-reconfigure xserver-xorg' but this does not generate an xorg.conf.

My graphic card is as follows, I think
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
01:05.1 Display controller: ATI Technologies Inc Radeon Xpress Series (RS482)

I'd be glad if someone could help me,

thanks in advance!!

---

### Post by realzippy on 2010-09-14
xorg.conf does not exist anymore.KMS does the job..
But you can still create one...

**dpkg-reconfigure xserver-xorg**
is outdated.
Run:
```
Xorg -configure

```

to create vanilla xorg.conf;have to stop GDM/X

Edit:

..you tried all that xrandr stuff (right-off options aso?)

---

