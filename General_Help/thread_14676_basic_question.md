---
title: "basic question"
date: 2005-02-09
forum: General Help
---

### Post by butt on 2005-02-09
Why does my mouse work in LIVE version but not in the other versions, ive tried warty and hoary, neither auto detect my ps/2 mouse..........

and so far noone has been able to help me get them working

---

### Post by alastair on 2005-02-09
Check the contents of /etc/modules

Mine has mouse modules :

mousedev
psmouse

what is the output of : grep mouse /var/log/dmesg ? (maybe check this file for errors "round" any mouse report - and also mouse logs in /var/log/syslog.

Is it a real PS/2 mouse or something else?

---

### Post by alastair on 2005-02-09
Oh - forgot X ... :-)

What is the "InputDevice" section of /etc/X11/xorg.conf? i.e. the "mouse" input device (CorePointer)?
Any errors in the X logs /var/log/Xorg.0.log ?

---

