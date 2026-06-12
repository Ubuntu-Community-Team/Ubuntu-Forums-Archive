---
title: "killing caps lock (standard methods fail)"
date: 2010-10-17
forum: General Help
---

### Post by drhex on 2010-10-17
I'd like to make a few changes to the keymap; disabling caps lock and a few other changes.

First I tried what has worked before:

editing */usr/share/X11/xkb/symbols/pc*
and commenting out a line there:

[FONT="Courier New"]//  key <CAPS> {   [ Caps_Lock  ]   };[/FONT]

But changes in the xkb-files apparently only takes effect after login, and this particular system is set to autologin (i.e. it only works after I log out and log in again, not right after a reboot).

I also tried putting

[FONT="Courier New"]xmodmap -e "clear Lock"[/FONT]

in one of the shell's startup-files  (*/etc/zsh/zshrc*)

No luck with that either. The above command works fine if I manually type it at the prompt, but for some strange reason it won't work in the shell startup script (and I know it has been executed since the lines before and after it in the script work fine).

What more can I try?   (Ubuntu 10.04 / Amilo M3438G portable)

---

### Post by mike555 on 2010-10-17
install "xkeycaps" , then start it in terminal and set it as you want , restart and accept the change.

---

