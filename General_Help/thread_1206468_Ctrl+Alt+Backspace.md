---
title: "Ctrl+Alt+Backspace"
date: 2009-07-07
forum: General Help
---

### Post by elliotn on 2009-07-07
In 8.10 when I hit Ctrl+ALT+backspace  system use to log me out and log me in, now in 9.04 it does nothing at alt. Has the cmd been changed?

---

### Post by tad1073 on 2009-07-07
They have disabled that command.

---

### Post by derekeverett on 2009-07-07
They just disabled it with nothing to replace it?

Geez I learn something new every few days that scares me off of upgrading...

---

### Post by CatKiller on 2009-07-07
From the [Release Notes]("http://www.ubuntu.com/getubuntu/releasenotes/904")

> The Ctrl-Alt-Backspace key combination to force a restart of X is now disabled by default, to eliminate the problem of accidentally triggering the key combination. Users who do want this function can enable it in their xorg.conf, or by running the command dontzap --disable.

---

### Post by mcduck on 2009-07-07
> **derekeverett said:**
> They just disabled it with nothing to replace it?

Geez I learn something new every few days that scares me off of upgrading...

SysRq-k has pretty much the same effect and still works. Ctr-Alt-backspace can also be enabled in xorg.conf if you feel you need it.

---

### Post by derekeverett on 2009-07-07
Thanks guys.

---

### Post by bobbyshane on 2009-07-30
> **tad1073 said:**
> They have disabled that command.

That is ridiculous.

Everyday I use Jaunty I miss I miss Ibex more and more. Between the hardware problems I've had, how slow it runs comparatively, and things like this, I think it's time to downgrade. Oh, yeah, and the reason I looked this up. I have Jaunty on my daughter's computer and when she goes to log into her edubuntu account she get's nothing but a yellow screen and I can't even simply ctrl-alt-backspace to restart x. Wtf?

---

### Post by The Cog on 2009-07-30
Yes, they broke it on purpose. To fix it again, add this clause to /etc/X11/xorg.conf:
```

Section "ServerFlags"
        Option          "DontZap"               "false"
EndSection

```

---

### Post by jerome1232 on 2009-07-30
> **mcduck said:**
> SysRq-k has pretty much the same effect and still works. Ctr-Alt-backspace can also be enabled in xorg.conf if you feel you need it.

Maybe it's because I'm on a laptop but SysRq+k does nothing (I've heard R alt+SysRq+k and that doesn't work for me either)

---

### Post by VeskoJl on 2009-07-30
Ubuntu (Linux) teams make a lot of stupid things! Moving conf files around , disabling such stuff, adding "new features"... I've reinstalled jaunty three times (just different builds of Jaunty) and ..... pain......  Yes, we users "must" follow the "mood" of "geeks" !

---

### Post by DaithiF on 2009-07-30
Just an observation ... I am surprised by how vehemently some people complain about little things like this.  

This was a change made to make Ubuntu more User Friendly, it was not something 'for the geeks'.   If Linux/Ubuntu is to become mainstream for non-techincal users, it seems right to me that there should not be a 'kill-switch' enabled and attached to often-used keys.  How surprised would a new user be to lose their desktop and any unsaved work because they hit this key-combo?  They would be entitled to feel pretty aggrieved I think.

Those of us who are used to this behaviour can restore it very easily.  Heck there was even a utility written specifically to make it EVEN easier for us to do that!  The change was fully documented, honestly what more could the developers do?

Just my opinion.

---

### Post by jerome1232 on 2009-07-30
Just to note Ubuntu got the change from Debian.

---

