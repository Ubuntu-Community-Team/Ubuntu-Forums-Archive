---
title: "please stop resetting the time"
date: 2009-12-03
forum: General Help
---

### Post by akashiraffee on 2009-12-03
How can I stop ubuntu from messing with my system clock everytime it boots?  I have several OS's on my harddrive and I have my the hardware clock set to local time. 

Everytime ubuntu boots it adjusts *the hardware clock*, meaning I have to adjust it back when a boot a different OS.  I have grepped thru init.d but there is no mention of "clock" or "date" or "time".  Evidently this is part of a new spirit of opacity and taking control away from the user.

---

### Post by jegerjensen on 2009-12-03
Could it be the ntpd?

 [http://en.wikipedia.org/wiki/Ntpd]("http://en.wikipedia.org/wiki/Ntpd")

---

### Post by wojox on 2009-12-03
If your hardware clock is set to local time, then what is your Ubuntu clock set to ?

---

### Post by michy99 on 2009-12-03
```
gksudo gedit /etc/default/rcS
```Make sure that ```
UTC=no
```

---

### Post by akashiraffee on 2009-12-03
> **michy99 said:**
> ```
gksudo gedit /etc/default/rcS
```Make sure that ```
UTC=no
```

Thanks!

---

### Post by lidex on 2009-12-03
Are you saying ubuntu sets it to the wrong time?
For a gui go to "system>administration>time and date". Unlock with your password. You can change to manual here or select a different ntp server.

---

