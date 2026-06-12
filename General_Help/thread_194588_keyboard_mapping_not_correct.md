---
title: "keyboard mapping not correct"
date: 2006-06-11
forum: General Help
---

### Post by jstritar on 2006-06-11
I have a Thinkpad T40. I recently used a USB keyboard on it, and ever since doing so, the keyboard mappings in X for the built in keyboard are not correct. For example, "jkl" ends up being "123".

Even after removing the USB keyboard and restarting X and the computer, the mappings are still incorrect. They are correct everywhere but inside X (the login screen and terminals work). My xorg.conf looks the same as it was before using the USB keyboard. How can I fix this?

---

### Post by jstritar on 2006-06-13
bump..

My xorg.conf looks correct. I replaced it with a backup. Does anyone have any ideas? How can I return X to its installed settings?

---

### Post by bertilow on 2006-06-13
[QUOTE=jstritar]I have a Thinkpad T40. I recently used a USB keyboard on it, and ever since doing so, the keyboard mappings in X for the built in keyboard are not correct. For example, "jkl" ends up being "123".[/QUOTE]

It seems you have num-lock turned on. That makes part of your
keyboard serve as a surrogate for the numeric key pad on a full scale
keyboard.

---

### Post by jstritar on 2006-06-13
Ahh... thanks! It all makes sense now (i turned num lock on b/c i was using an external keyboard for a little). Damn... I've been trying to figure this out for a couple days. Thanks.

---

