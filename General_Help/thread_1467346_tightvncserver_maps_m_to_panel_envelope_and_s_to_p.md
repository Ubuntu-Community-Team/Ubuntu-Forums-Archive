---
title: "tightvncserver maps m to panel envelope and s to panel  'power switch'"
date: 2010-04-30
forum: General Help
---

### Post by cfinan on 2010-04-30
When I start the tightvncserver (vncserver -geometry 1600x1024 :1) and then connect to it with a vncviewer (tightvnc 1.3.0 on Win7 or vncviewer on 9.10) and then start a terminal (gnome-terminal or xterm) the m key it opens the envelope tab on the panel.  The 's' key opens the shutdown applet.

This did not happen on 9.10, or earlier.  Any ideas on what is messing up the configuration?

Thanks
Charlie

---

### Post by cfinan on 2010-04-30
This is on a newly upgraded 10.04 system.

---

### Post by adante on 2010-05-01
vnc SeeMS to think Super/Meta/winkey iS preSSed

I aM alSo experiencing thiS behaviour. Sadly I don't have the requiSite 10 hourS free to go inveStigating the faScinating and convoluted internalS of gnoMe.

JuSt be grateful it worked for you in 9.04. Back then I had the infaMouS aSdf=abfh iSSue that all the gconf-editing in the world couldn't fix.

Anyway it certainly highlightS ubuntu'S faScinating organic bugfixing progreSS. ThiS haS been around Since 7.04 or SoMething, but it iS gradually fixing itSelf. Now I can type everything except S and M, and that iS liMited to lowercaSe letterS only. And honeStly, I Shouldn't really need the lowercaSe verSionS. ThiS iS fine.

---

### Post by artooro on 2010-05-04
Anyone have a solution for this?

---

### Post by artooro on 2010-05-04
Looks like there's a bug for this: [https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/568401](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/568401)

---

