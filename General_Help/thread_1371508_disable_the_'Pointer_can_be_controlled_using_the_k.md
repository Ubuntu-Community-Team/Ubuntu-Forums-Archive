---
title: "disable the 'Pointer can be controlled using the keypad' function"
date: 2010-01-03
forum: General Help
---

### Post by stoneage on 2010-01-03
Can anyone tell me how to permanently disable the 'Pointer can be controlled using the keypad' accessibility function?

There was a post about it on launchpad, that I used before and since updating to 9.10 I can't find it.

It may be a Gnome bug, and its getting very irritating - maybe 10 - 12 times a day.......

Any useful help is appreciated - esp if you can name it so I can uninstall it :)

---

### Post by stoneage on 2010-01-04
Hello again, I found it.....

For anyone else it is here:-

> 
Ond&#345;ej Buriánek wrote on 2009-11-21: #52 Hello fellow earthlings daily beaten by this bug.
I used this workaround to permanently disable mousekeys shortcut shift+num-lock, alt+shift+num-lock etc...
gksudo gedit /usr/share/X11/xkb/compat/complete
-or-
sudo nano /usr/share/X11/xkb/compat/complete
and comment out lines for mousekeys and accesx(full) (for full keyboard accessibility purge)
resulting file /usr/share/X11/xkb/compat/complete:
// $XKeyboardConfig$
// $Xorg: complete,v 1.3 2000/08/17 19:54:34 cpqbld Exp $
default xkb_compatibility "complete" {
include "basic"
augment "iso9995"
//augment "mousekeys"
//augment "accessx(full)"
augment "misc"
augment "xfree86"
augment "level5"
};
Wish you a lot happy days without moving mouse by keypad
Greets Ondrej
[https://bugs.launchpad.net/xorg-server/+bug/192508](https://bugs.launchpad.net/xorg-server/+bug/192508)

---

