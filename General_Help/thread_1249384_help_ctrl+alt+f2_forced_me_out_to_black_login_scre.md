---
title: "help: ctrl+alt+f2 forced me out to black login screen"
date: 2009-08-25
forum: General Help
---

### Post by Ascenti0n on 2009-08-25
I pressed: ctrl+alt+f2 keys, thinking I was activating a kwin shortcut, but I was forced out into a black login screen.

Can someone tell me where in Kubuntu I can disable this key combo for this action?

---

### Post by P4man on 2009-08-25
control + alt + function keys will give you a virtual terminal (different one for each function key). Control + alt +F7 is normally the one on which X runs, so use that to return to KDE or gnome.

I dont know if its possible to override those, but you may as well pick another key combo. windows key (super key) combinations arent used a lot, so perhaps pick one with that.

---

### Post by nikhilk on 2009-08-25
> **Ascenti0n said:**
> I pressed: ctrl+alt+f2 keys, thinking I was activating a kwin shortcut, but I was forced out into a black login screen.

Can someone tell me where in Kubuntu I can disable this key combo for this action?

I am not at a Linux box right now so cannot confirm but I found this in the xorg.conf manpage
> Option "DontVTSwitch"  "boolean"
              This  disallows  the use of the Ctrl+Alt+Fn sequence (where Fn refers to one of the numbered function keys).
              That sequence is normally used to switch to another "virtual terminal" on operating systems that  have  this
              feature.   When  this  option is enabled, that key sequence has no special meaning and is passed to clients.
              Default: off.

This option should be added in a section named "ServerFlags".

---

### Post by Ascenti0n on 2009-08-25
> **P4man said:**
> control + alt + function keys will give you a virtual terminal (different one for each function key). Control + alt +F7 is normally the one on which X runs, so use that to return to KDE or gnome.

I don't know if its possible to override those, but you may as well pick another key combo. windows key (super key) combinations aren't used a lot, so perhaps pick one with that.

I appreciate the tip to get back to the KDE desktop should i hit an undesired key combo in future.

re using Super/Windows key - that was actually in my thinking too.

Thanks

---

### Post by Ascenti0n on 2009-08-25
> **nikhilk said:**
> I am not at a Linux box right now so cannot confirm but I found this in the xorg.conf manpage


This option should be added in a section named "ServerFlags".

Thanks - another good tip.

---

### Post by nikhilk on 2009-08-25
> **Ascenti0n said:**
> I appreciate the tip to get back to the KDE desktop should i hit an undesired key combo in future.

If you get to a text terminal by hitting any of the Alt+Ctrl+Fn (where can be 1 through 6, i.e. F1 to F6) keys, you can get back to your desktop by pressing Alt+Ctrl+F7

---

