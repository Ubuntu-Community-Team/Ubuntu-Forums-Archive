---
title: "How to add application to startup automatically?"
date: 2011-10-15
forum: General Help
---

### Post by mmcmonster on 2011-10-15
Can't believe I'm asking this since I've been using Ubuntu for >5 years now, but...

**How can I add an application to start automatically upon login?**

I installed xbmc (team-xbmc maverick repository), and want it to start automatically so I can use the computer as a media center. (No mouse or keyboard, just remote control.)

Any help would be appreciated.

---

### Post by mmcmonster on 2011-10-20
Bump.

Seriously, no one else has this problem?

---

### Post by IBUA on 2011-10-20
I might be being presumptious here, but have you tried startup applications?

Go to Dash, type in Startup Applications, then just add the xbmc command there...?

SORRY! If your running Lucid: (I think) Menu -> Preferences -> Startup Applications

---

### Post by mmcmonster on 2011-10-21
Not running lucid.  Have to change that in my profile. :-)

I tried adding the startup application, and the system just hung the next time I rebooted.

I'll try again when I get home.

Anyone else add an application with the startup application?  Does it work for you?

---

### Post by mmcmonster on 2011-10-21
Okay.  I'm getting somewhere now. :-)

Using the "startup Applications" application, I am able to get XBMC started up...

BUT it starts up in a window.  It will eventually go into full screen mode after a few keypresses with the keyboard (and presumably with the remote control as well).

Anyone know how to force XBMC to start in full screen mode?

---

### Post by agillator on 2011-10-21
Have you tried putting a startup script in /etc/init.d and linking it to the various rcx.d directories?

---

### Post by stinkeye on 2011-10-21
> **mmcmonster said:**
> Okay.  I'm getting somewhere now. :-)

Using the "startup Applications" application, I am able to get XBMC started up...

BUT it starts up in a window.  It will eventually go into full screen mode after a few keypresses with the keyboard (and presumably with the remote control as well).

Anyone know how to force XBMC to start in full screen mode?
Even though man xbmc shows
> **-fs    Runs XBMC in full screen**
for me xbmc will start in the the mode (windowed or fullscreen) it was in
when I last closed it, even if I run ```
**xbmc -fs**
```

---

