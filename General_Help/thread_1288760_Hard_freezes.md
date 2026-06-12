---
title: "Hard freezes"
date: 2009-10-11
forum: General Help
---

### Post by FreezWay on 2009-10-11
sometimes when i boot up Google Earth or nexuiz i get hard crashes. ctrl-alt-bksp ctrl-alt-F[1-6] and ctrl-alt-del do not work i have have to hold down my power button. i am using 2.6.31 kernal, self compiled. i have a gateway SX computer (if u need hardware info.)

---

### Post by radar2020 on 2009-10-11
To enable ctrl+alt+backspace in Jaunty install dontzap. 

```
sudo aptitude install dontzap
```

Then disable dontzap.

```
sudo dontzap --disable
```

If that doesn't work try Alt + SysRq (Print Screen) and type reisub with a 1 second delay between letters.

---

