---
title: "multiple keyboard shortcuts, or how to make one key represent several."
date: 2010-09-23
forum: General Help
---

### Post by bgugi on 2010-09-23
sorry for the ambiguous title, but here's the situation:  i have a question. I have ctrl+alt+home/end/pgup/pgdwn set up in the gnome keyboard shortcuts dialogue to control my media players. in addition to the keyboard, i sometimes like to use a wiimote through wminput, but as far as i can tell wminput can only associate a single key to each button. to get around this until now, i've used odd xf86 keys (like bassboost) to send "rhythmbox-client --play-pause" and such to rhythmbox. currently, i'm using rhythmbox and pithos interchangeably (depends on whether i have internet) basically, i'm wondering if i can: a) map more than one key to the gnome "play" command, b) map one key into multiple (xf86bassboost = ctrl+alt+home) or c) something else?

---

### Post by bgugi on 2010-09-26
bump?

another idea, could i map a series of keystrokes to a single key? (for example, ctrl+alt+home to xf86bassboost)? 

also of note: at one point or another, perhaps through an update, my computer has concluded that my right alt is now ISO_Level_3_Shift, and thus should be mod5. this can be fixed with two commands (see below), but is reset to it's mod5 status every reboot. what caused this? is there a permanent fix? i think this has happened on at least one other install.

```
bgugi@OPERATOR:~$ xmodmap -e "remove mod5 = ISO_Level3_Shift"
bgugi@OPERATOR:~$ xmodmap -e "add mod1 = ISO_Level3_Shift"

```

---

### Post by VCoolio on 2010-09-26
I'm not sure if this is what you're looking for, but with xbindkeys you can combine any keybinding with any command; I don't see the point of mapping a key(binding) to another keybinding that is supposed to launch a command.

The xmod commands can be added to ~/.xinitrc I think, create the file if it's not there yet, or create a little script and add it to system > preferences > startup applications, like:
```

#!/bin/sh
xmodmap -e "remove mod5 = ISO_Level3_Shift";
xmodmap -e "add mod1 = ISO_Level3_Shift"
```
Save and add as command startup apps something like 'sh /path/to/script'. But it would be better to solve the real problem behind; don't know about that though.

---

