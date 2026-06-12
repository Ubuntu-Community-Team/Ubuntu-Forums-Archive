---
title: "Getting feh's Wallpaper to Stay on Fluxbox"
date: 2011-04-14
forum: General Help
---

### Post by EMABrad on 2011-04-14
Whenever I set a new wallpaper on Fluxbox with feh, it goes away as soon as I log out and log back in.  It is probably relevant to say that my login wallpaper just so happens to be the same one that Fluxbox automatically switches to when it logs in, which I changed (somehow, can't remember how).  Halp?

---

### Post by kerry_s on 2011-04-14
There's a command for feh you have to put in the start up. Type "man feh" in terminal.
you do know fluxbox can do it's own backgrounds? No need to run an extra app.

---

### Post by EMABrad on 2011-04-14
I thought it might be something along those lines.  How does Fluxbox set it's own backgrounds, though?  I was under the impression that it can't.

---

### Post by m_duck on 2011-04-14
IIRC Fluxbox uses the fbsetbg command to set the wallpaper, but in turn, fbsetbg calls another program to actually set the wallpaper - e.g. feh, eterm, others that I cannot remember... If you have feh installed, there is a good chance fbsetbg would use it to set the wallpaper anyway.

---

### Post by kerry_s on 2011-04-14
personally, i'd go with something like nitrogen.
(random google link)
[http://maketecheasier.com/nitrogen-a-background-setter-for-lightweight-desktop-manager/2008/12/02](http://maketecheasier.com/nitrogen-a-background-setter-for-lightweight-desktop-manager/2008/12/02)

ps: it's already in the repo, just select & install.

---

### Post by EMABrad on 2011-04-14
Hmmm... Nitrogen looks pretty good.  Would it have the same problem as feh?  And am I correct when I say that my problem is the result of feh not starting automatically when Fluxbox starts?  Because if that's the case, that's easily fixed.

---

### Post by kerry_s on 2011-04-14
Yeap, you would have to add that nitrogen.

---

### Post by EMABrad on 2011-04-14
Hmmm... I understand.

Thanks!

---

