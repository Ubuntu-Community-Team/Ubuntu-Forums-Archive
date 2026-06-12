---
title: "Global Hotkeys - Page Up &amp; Page Down?"
date: 2011-03-26
forum: General Help
---

### Post by &lt;bogisha/&gt; on 2011-03-26
Can anyone tell me how to name Page up & Page down buttons in global-keybindings to use the custom commands with these buttons?

---

### Post by Krytarik on 2011-03-26
Generally, you can use```
xev
```to get key/button infos.

But for this application you can also use "Page_Down" and "Page_Up". Those are different from those displayed by "xev", I got them by combining them with Alt in the grab dialog in "Preferences -> Keyboard Shortcuts". I guess you want to set them up solely, via gconf-editor. I tested that, and it works. :-)

Greetings.

---

