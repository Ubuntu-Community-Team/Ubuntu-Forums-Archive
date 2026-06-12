---
title: "Boot hangs, but console (alt F2) available"
date: 2011-08-21
forum: General Help
---

### Post by swissbusinet on 2011-08-21
Hello Gurus,

I have an updated Ubuntu server and had problems with the windowmanger. Now treated the system and now it will not start anymore. I do need help.

Symptom:
Starts up to "Checking battery state... // Running local boot scripts (etc/rc.local) 
than it hangs.
> which logfile should I look in?
in /var/log/messages nothing special

I could login remote via ssh
I could activate the second tty (alt F2) but no language settings are loaded.

I run aptidue, dpgk-reconffigure and commented some entries in /etc/apt/sources.list:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
are active, rest is excluded by comments

If I start X with startx a gray screen with a mouse X comes up, but there is nothing. No keystrokes or mouse buttons effects anything.

What informations do you need to help?

---

### Post by Lampi on 2011-08-21
hallo swissbusinet

Why still use the former LTS (hardy) instead of lucid, the current LTS?

Xserver activities are logged in /var/log/Xorg.0.log - check the lines starting with (EE)

Maybe you are better of if you test a fresh lucid server edition from an installer image than hardy dist-upgrade? This will give you an idea what changed between former LTS and current LTS.

---

