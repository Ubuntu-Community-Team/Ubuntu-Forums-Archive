---
title: "Key Pad Not Working in VNC Session"
date: 2011-08-05
forum: General Help
---

### Post by tranbo2@yahoo.com on 2011-08-05
Hi, I'm using XUbuntu 1104.  The keypad is not working Under the TightVNC viewer session.  Followed the solution below didn't work.

Thanks for your help

-----------------------------------------------------------------------------------------
-Fix Numlock not working under VNC Session

I used this workaround to permanently disable mousekeys shortcut shift+num-lock, alt+shift+num-lock etc…

sudo mousepad /usr/share/X11/xkb/compat/complete
and comment out lines for mousekeys and accesx(full) (for full keyboard accessibility purge)
resulting file /usr/share/X11/xkb/compat/complete:
// $XKeyboardConfig$
// $Xorg: complete,v 1.3 2000/08/17 19:54:34 cpqbld Exp $
default xkb_compatibility “complete” {
include “basic”
augment “iso9995&#8243;
//augment “mousekeys”
//augment “accessx(full)”
augment “misc”
augment “xfree86&#8243;
augment “level5&#8243;
};
Wish you a lot happy days without moving mouse by keypad
Greets Ondrej

---

