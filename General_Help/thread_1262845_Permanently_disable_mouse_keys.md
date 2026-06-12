---
title: "Permanently disable mouse keys?"
date: 2009-09-10
forum: General Help
---

### Post by Kyle_S on 2009-09-10
How would you permanently disable mouse keys?

They keep on getting turned on randomly on my system, and it's a big pain.

I need a way of permanently disabling them.  If it's a configuration, editing files, removing programs, I don't care, I just need to get rid of the mouse keys!

Thanks

---

### Post by Penguin Guy on 2009-09-10
Turning it off in [COLOR="Green"]System -> Preferences -> Keyboard -> Mouse Keys[/COLOR] works for me.

---

### Post by Kyle_S on 2009-09-10
> **Penguin Guy said:**
> Turning it off in [COLOR="Green"]System -> Preferences -> Keyboard -> Mouse Keys[/COLOR] works for me.

Sadly it doesn't for me.  It turns on all on it's own over and over and over and over and over and over again....

I usually have to turn it off once or twice a day.

---

### Post by zerem on 2009-11-20
--- as i posted in [https://bugs.launchpad.net/ubuntu/+bug/192508](https://bugs.launchpad.net/ubuntu/+bug/192508) ---

Hello fellow earthlings daily beaten by this bug.

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

Wish you a lot happy days without moving mouse by keypad ;)
Greets Ondrej

---

### Post by Phezz on 2010-05-21
You sir, have made my day.  I've replaced my keyboard 3 times before I found out about this issue.  This should a checkbox in the mousekeys gui pane.

---

### Post by CX23882 on 2010-12-20
I'm running Ubuntu 10.04 and I've commented out those two lines, but still mousekeys gets re-enabled. I'm certainly not pressing anything to enable it either - it's either getting renabled on boot (possibility, since there have been so many updates that require a reboot lately), or VNC is doing something. 

It is very annoying because if I accidentally use the numpad via a VNC login, the X session crashes.

---

### Post by scarf on 2011-07-02
commenting out the lines for me doesn't work either.  using 10.04 also.  mouse keys is disabled in the GUI keyboard preferences as well as in the gconf settings.

---

### Post by wv9k on 2012-02-15
> **scarf said:**
> commenting out the lines for me doesn't work either.  using 10.04 also.  mouse keys is disabled in the GUI keyboard preferences as well as in the gconf settings.

 Not working here either.

---

