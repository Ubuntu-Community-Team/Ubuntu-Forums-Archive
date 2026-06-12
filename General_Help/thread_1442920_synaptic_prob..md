---
title: "synaptic prob."
date: 2010-03-30
forum: General Help
---

### Post by nischalinn on 2010-03-30
When I open the_** synaptic**_ via terminal,it shows:

[B]XXX@XXX-desktop:~$ gksu synaptic
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".

What is this?How can I remove it?
[/B]

---

### Post by DeMus on 2010-03-30
> **nischalinn said:**
> When I open the_** synaptic**_ via terminal,it shows:

[B]XXX@XXX-desktop:~$ gksu synaptic
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".

What is this?How can I remove it?
[/B]

Why do you start it using gksu? Just start it normally and it will ask you for your password. It probably doesn't make any difference.
I have no idea what these codes mean. I hope somebody else does.

---

### Post by 2hot6ft2 on 2010-03-30
It may have to do with your theme, just guessing but the command would be
```
gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
```
That's what it runs when you start it from the menu.

---

