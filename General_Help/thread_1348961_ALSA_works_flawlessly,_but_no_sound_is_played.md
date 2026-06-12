---
title: "ALSA works flawlessly, but no sound is played"
date: 2009-12-07
forum: General Help
---

### Post by UseBees on 2009-12-07
ALSA works flawlessly, the channels are all at non-zero values and not muted. i've tried different headphones/speakers, and many other guides on how to solve this, but nothing seems to work. there is no sound. any and all help is appreciated.

---

### Post by MooPi on 2009-12-07
Open a terminal and type 
> alsamixer
Check to see if if master or center are zero'd out

---

### Post by UseBees on 2009-12-07
both channels are unmuted and at 100%

---

### Post by MooPi on 2009-12-07
Check this file /etc/libao.conf. It should indicate that alsa as default driver.
Lastly use the live CD to test sound .

---

### Post by UseBees on 2009-12-07
etc/libao.conf
default_driver=alsa

sound works on the liveCD

---

### Post by UseBees on 2009-12-07
not at all sure what i changed, but it started working again after rebooting after using the liveCD (none of the other reboots, oddly enough)
EDIT: thanks for the help, though

---

