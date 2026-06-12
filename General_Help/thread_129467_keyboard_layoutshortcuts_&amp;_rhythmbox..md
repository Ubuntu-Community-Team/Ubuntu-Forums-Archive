---
title: "keyboard layout/shortcuts &amp; rhythmbox."
date: 2006-02-13
forum: General Help
---

### Post by fangorious on 2006-02-13
I have an MS Natural Pro keyboard, with multimedia keys, and have specified that layout in System->Preferences->Keyboard. I have then specified all the media keys for actions like play/pause, stop, next, prev, vol up, vol down, and mute using System->Preferences->Keyboard Shortcuts (gnome-keybinding-properties). Using the correct keyboard layout, these keys seem to map to XF86AudioNext, XF86AudioPrev, etc. Using the Generic 104 key layout, the keys map to hex codes like 0x90. I would like to use these keys in rhythmbox (0.9.1) but neither layout seems to work. It works just fine in amarok either way.

---

### Post by joehill on 2006-02-25
Sorry, this isn't an answer to your question, just a similar experience with this bug.  If I want to assign <ctrl><alt> x to skip back a track using the "keyboard shortcuts" dialogue, x is completely remapped to something else (0xf4 or something) and stops working altogether, and I have to reset the keyboard layouts (in System -> Preferences -> Keyboard) if I want to use key x again.  (That is to say, it's permanently changed so I can't fix it through the keyboard shortcuts dialogue.)

So there's some kind of bug in the keyboard shortcuts program or rhythmbox or something.  I hope someone works this bug out soon, and until then I'm just using Amarok.

---

### Post by Trab on 2006-02-25
just wondeirng, are u trying to use rythebox stuff to edit ur keys, or gnome, or even hardwiring it in...?

there are some tricks, ill look into it...

---

### Post by joehill on 2006-03-05
I'm using the "keyboard shortcuts" dialogue under System -> Preferences.

Ok, I've figured out a workaround using gconf-editor (Applications -> System tools -> System Configuration).  I find gconf-editor far more useful than the limited-functionality "Keyboard Shortcuts" dialogue.

I just add my own custom commands under "apps -> metacity -> keybinding_commands."  You just have to bind command-line rhythmbox functions (like "rhythmbox --play-pause", "rhythmbox --next", and any other command you get from typing "rhythmbox --help").  This seems to work because it's just using simple shell commands.

---

### Post by justinjstark on 2006-03-05
[QUOTE=joehill]I'm using the "keyboard shortcuts" dialogue under System -> Preferences.

Ok, I've figured out a workaround using gconf-editor (Applications -> System tools -> System Configuration).  I find gconf-editor far more useful than the limited-functionality "Keyboard Shortcuts" dialogue.

I just add my own custom commands under "apps -> metacity -> keybinding_commands."  You just have to bind command-line rhythmbox functions (like "rhythmbox --play-pause", "rhythmbox --next", and any other command you get from typing "rhythmbox --help").  This seems to work because it's just using simple shell commands.[/QUOTE]

That does work but I find it's a lot laggier than just using gnome's keyboard short-cuts.

Sorry but I can't really help in getting it to work, however.  My binds are all displayed as hex codes.

---

