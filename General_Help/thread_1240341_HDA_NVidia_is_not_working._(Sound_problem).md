---
title: "HDA NVidia is not working. (Sound problem)"
date: 2009-08-14
forum: General Help
---

### Post by Xomm on 2009-08-14
I get no sound on kubuntu. I recently reinstalled Kubuntu after messing up several config files, and now sound won't work. (Up until now, sound has always worked.)

---

### Post by Screwdriver0815 on 2009-08-14
open a terminal and type

```
alsamixer
```

then you see some equializer bars. Check if the Master and PCM bar are muted or on "0". If yes, adjust them by using the keyboard arrow buttons.

leave the alsamixer with ESC - this will save your settings.

---

