---
title: "suddenly disappeared compiz effects"
date: 2010-02-23
forum: General Help
---

### Post by joselitux on 2010-02-23
Hi


Suddenly, i was working fine with my Karmic, and now can't activate desktop effects.

First windows lost borders, so I reset X (ctrl+backspace) and since then, effects went to hell.

I've reinstalled nVidia drivers. All went fine, but desktop effect still disappeared.

See the commands output below:


**glxinfo | grep rendering**
direct rendering: Yes

**compiz --replace**
Checking for Xgl: not present.
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity


Thanks in advance

---

### Post by Sef on 2010-02-23
What video card do you have?

---

### Post by joselitux on 2010-02-24
Nvidia geforce 8400M GS

---

