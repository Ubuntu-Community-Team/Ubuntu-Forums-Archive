---
title: "on boot Error activating XKB configuration."
date: 2009-08-07
forum: General Help
---

### Post by mamakubwa on 2009-08-07
2 week old ubu 9 setup, i could cry, this is about the 6th time my install has started screwing up after a few weeks!

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10600000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "pc105", "us", "", ""
_XKB_RULES_NAMES(STRING) = "evdev", "pc105", "us", "", ""

and  model = 
 options = []
 layouts = [aa]

respectively.

the recent upgrade asked me about my virtualbox install... something about the old kernel..

i also recently installed truecrypt

thanks.

---

### Post by SoftwareExplorer on 2009-08-08
I have the same error message. It seemed to happen after I moved my /home to another partition and symbolic linked to it. I'll post the command output the next time it happens.

mamakubwa, sorry I'm of so little help. But I am looking for the same answer.

---

### Post by mamakubwa on 2009-09-06
> **SoftwareExplorer said:**
> I have the same error message. It seemed to happen after I moved my /home to another partition and symbolic linked to it. I'll post the command output the next time it happens.

mamakubwa, sorry I'm of so little help. But I am looking for the same answer.

well, mine seems to be from the change to the keyboard, in the configuration editor, keyboard section. i deleted the [aa] to make [ ] and this cleared it up. 

i originally put an entry in the brackets because my remote keyboard was not working properly in tightvnc. then i stopped using tightvnc and switched to x11vnc which worked much better for me.

---

### Post by SoftwareExplorer on 2009-09-06
Glad you got it working. My problem mysteriously quit happening, so I would say my problem is fixed.

---

