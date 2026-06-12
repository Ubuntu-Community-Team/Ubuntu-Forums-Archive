---
title: "Set custom Unity defaults?"
date: 2012-05-27
forum: General Help
---

### Post by spillin_dylan on 2012-05-27
Hey, this might be a silly question, but what can I do to keep my custom Unity settings such as transparency, icon size, etc, persistent or saved when I have to do a "unity --reset"?  Everything defaults back to gigantic icons that I don't want, but I'm (sometimes) tweaking other settings in CCSM that lock up, and I am stuck resetting back to the defaults.

---

### Post by wilee-nilee on 2012-05-27
> **spillin_dylan said:**
> Hey, this might be a silly question, but what can I do to keep my custom Unity settings such as transparency, icon size, etc, persistent or saved when I have to do a "unity --reset"?  Everything defaults back to gigantic icons that I don't want, but I'm (sometimes) tweaking other settings in CCSM that lock up, and I am stuck resetting back to the defaults.

Try alt-f2 compiz --replace if you just need a compiz restart, can be run in the terminal as well.

---

### Post by diesch on 2012-05-27
[Unsettings](http://www.florian-diesch.de/software/unsettings) lets you save your Unity setting to and load from a file.

---

### Post by stinkeye on 2012-05-27
Use the preferences in ccsm to export your settings and then import 
when needed.
...and as wilee-nilee said, use **compiz --replace** first
and then **unity --reset** if compiz still fails to load properly.

---

### Post by spillin_dylan on 2012-05-28
Thanks for all the suggestions everyone!  I will try exporting my settings!

---

