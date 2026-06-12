---
title: "alsamixer shows only 1 control ( master )."
date: 2009-12-03
forum: General Help
---

### Post by endBc on 2009-12-03
How do I add more controls ( PCM, Surround, Microphone, etc. ) ?

```
pcm.pulse {
    type pulse
}

ctl.pulse {
    type pulse
}

pcm.!default {
    type pulse
}

ctl.!default {
    type pulse
}

```

[[IMG]http://img256.imageshack.us/img256/5473/200912031434201280x1024.th.png[/IMG]](http://img256.imageshack.us/i/200912031434201280x1024.png/)

---

### Post by lidex on 2009-12-03
Key combo Alt+F2. Enter "gnome-alsamixer". In "edit" menu select "soundcard properties"

---

