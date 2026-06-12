---
title: "Disable sleep mode shortcut key"
date: 2010-10-14
forum: General Help
---

### Post by Sockerdrickan on 2010-10-14
How can I disable the functionality that puts the computer to sleep when I press the sleep button on my keboard?

I keep hitting it accidentally and I don't even use a swap, so Ubuntu just stalls with a black screen.

---

### Post by trupson on 2010-10-15
Hit Alt+F2 and type gconf-editor. Then go to apps -> gnome-power-manager -> buttons. Edit the value for the suspend button and type "nothing". The sleep key should stop working now.

---

### Post by Sockerdrickan on 2010-10-15
> **trupson said:**
> Hit Alt+F2 and type gconf-editor. Then go to apps -> gnome-power-manager -> buttons. Edit the value for the suspend button and type "nothing". The sleep key should stop working now.
Thanks :popcorn:

---

