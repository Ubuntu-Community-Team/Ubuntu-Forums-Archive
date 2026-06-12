---
title: "ratpoison hiccough"
date: 2006-03-15
forum: General Help
---

### Post by evaristegalois on 2006-03-15
Just installed ratpoison and it works great with one exception: when I try calling xterm with C-t x and the configuration file below all I get is a message telling me ``/bin/sh -c "xterm" finished (127)'' but I want it, of course, to just open an xterm window for me. What's wrong? (The same happens when I want to call up emacs. xbindkeys is installed properly.) --evaristegalois
exec xbindkeys
bind e exec emacs
bind x exec xterm
startup_message off
exec xrdb -merge ~/.Xresources

---

### Post by LxP on 2006-11-10
It sounds like xterm might not be in ratpoison's path.  Try changing the appropriate line in your .ratpoisonrc file to point to xterm absolutely:

```
bind x exec /usr/bin/xterm
```

---

