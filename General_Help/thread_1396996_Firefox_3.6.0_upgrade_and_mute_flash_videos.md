---
title: "Firefox 3.6.0 upgrade and mute flash videos"
date: 2010-02-02
forum: General Help
---

### Post by MarcoPau on 2010-02-02
Just upgraded to firefox 3.6.0 with ubuntuzilla in my karmic, but flash videos in the browser are mute. I can only hear a "boom" at start then just no sound. Tried with killall pulseaudio already but no effect.

Do you guys have any hint?

TIA

---

### Post by nanotube on 2010-02-03
hrm, no idea offhand... maybe a reboot might help (sometimes it takes that to get pulseaudio to wake up)? 
does other sound work fine otherwise? 
how about html5-video as opposed to flash?
maybe try getting the freshest flash plugin from adobe, and stick it into ~/.mozilla/plugins ?

just throwing out a bunch of stuff, and seeing what sticks :)

---

### Post by lovinglinux on 2010-02-03
Can you still get sound with Firefox 3.5?

You can start it with this command:

```
firefox-3.5
```

Also take a look at the [SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) wiki page.

---

### Post by MarcoPau on 2010-02-03
Thanks nanotube, solved with a fresh new plugin as you suggested :-)

---

### Post by nanotube on 2010-02-03
> **MarcoPau said:**
> Thanks nanotube, solved with a fresh new plugin as you suggested :-)

excellent! :)

---

