---
title: "Refresh rate issues"
date: 2006-03-03
forum: General Help
---

### Post by Phixion on 2006-03-03
Hello, I never usually have problems with my refresh rate, but since installing the new release (5.10) it fails to auto detect my monitors max refresh rate.

I have a Relisys 988TE 19" CRT monitor and I usually run at 1024x768 @ 85Hz.

Can anyone help me? I know I need to change something in /etc/X11/xorg.conf but I'm not 100% sure what I need to change it to.

Cheers

---

### Post by swamytk on 2006-03-03
Add the following lines in /etc/X11/xorg.conf in Monitor section:

HorizSync 30 - 75
VertRefresh 50 - 90

The above values are just examples. If already these lines are there, set with proper values. If you don't know your monitor's setting, refer the monitor manual.

---

### Post by Phixion on 2006-03-03
I managed to sort it thanks, I followed a tutorial and reconfigured the x server :)

---

