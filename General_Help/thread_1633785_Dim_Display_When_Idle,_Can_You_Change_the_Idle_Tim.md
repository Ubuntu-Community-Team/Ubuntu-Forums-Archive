---
title: "Dim Display When Idle, Can You Change the Idle Time?"
date: 2010-11-29
forum: General Help
---

### Post by onaridge on 2010-11-29
For Dim Display When Idle, Can You Change the Idle Time?
It's a great idea when using the battery but it dims after way too short a time. Can the time interval be extended with a script? Tweak Ubuntu doesn't enable any time frame.

---

### Post by mikewhatever on 2010-11-29
I also thought the idle time interval was too short. The setting can be changed from gconf-editor.
Run **gconf-editor** in a terminal, navigate to /apps/gnome-power-manager/backlight, and click to change the idle_dim_time.

---

### Post by onaridge on 2010-11-29
Thanks, exactly what I wanted. That default should definitely be changed.

---

