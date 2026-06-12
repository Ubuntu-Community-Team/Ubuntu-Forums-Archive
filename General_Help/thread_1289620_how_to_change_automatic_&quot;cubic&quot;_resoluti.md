---
title: "how to change automatic &quot;cubic&quot; resolution to automatic widescreen resolution"
date: 2009-10-12
forum: General Help
---

### Post by rusma on 2009-10-12
Hi, 

When I start up my Ubuntu/amd64 9.04 system on my DELL Latitude E5400, it starts up with a "cubic" screen resolution - instead of a windscreen one. I have to press Fn+F8 each time I log in to ajust back to fullscreen resolution again. How can I work around this so I do not have to press these keys every time i start up to get decent resolution? 

Any help is greatly appreciated.

---

### Post by P4man on 2009-10-13
Fn+F8 switches external monitor on/off right? Not sure, but you might want to look in the bios for a default setting for the external monitor.

---

### Post by rusma on 2009-10-13
Hi, I think the problem is solved for now. I noticed xrandr said TV-output was connected and that forced the resolution to a max 1024x768. I blew into the s-video outlet - and now xrandr reports it as "disconnected", and the resolution on startup is right.

---

### Post by rusma on 2009-10-14
No way! The problem has reappeared! 

My TV-output is reported as disconnected by xrandr. Now what? 

sooo frustrating....

---

### Post by rusma on 2009-10-15
Can someone confirm if this is going to work if i blacklist my TV-output?

---

### Post by P4man on 2009-10-15
Nope (meaning, I can't *confirm* it), but it sounds worth trying. 

However, id check the bios first, Fn+F8 is a bios shortcut to toggle external monitor on/off, it wouldn't surprise me you could change the default in the bios to cure the problem.

---

### Post by rusma on 2009-10-15
Naa, my school pc admin has set a password on the bios - as my local authorities apparently don't like me fiddling around with the bios settings (they own the computer).. 

This is'nt a problem in windows xp pro on the same computer.

---

