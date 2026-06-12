---
title: "released key code repeating problem, where is hot-key setup?"
date: 2009-12-07
forum: General Help
---

### Post by 999alfred on 2009-12-07
After installing 9.10 I find I am having the repeating "key pressed and released" messages in syslog caused by the wireless mouse/keyboard. However, when I go to /usr/share/hotkey-setup looking for the generic.hk file to fix the problem as I did before, IT DOESN'T EXIST ANYMORE!!... A find says it doesn't exist aanywhere.
So tweo questions.
1. How now is the proper way to get rid of the problem. I put the setkeycodes command in rc.local.
2, What the heck happened to the hotkeys-setup directory and why is it gone?

tj

---

### Post by antony.s on 2009-12-27
It appears hotkey-setup was deprecated - [https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/458961](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/458961)

---

