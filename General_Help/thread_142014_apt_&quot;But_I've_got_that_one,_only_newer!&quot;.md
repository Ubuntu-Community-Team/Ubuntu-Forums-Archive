---
title: "apt: &quot;But I've got that one, only newer!&quot;"
date: 2006-03-09
forum: General Help
---

### Post by kiwibird on 2006-03-09
The game Cube tells me I need libsdl-mixer, so I try getting it with synaptic, which tells me I need libsmpeg0, searching for which I find I have libsmpeg0c2 already installed. What should I do? Install double? Remove the newer one? I've had issues like this before, I'm not sure if it's because of backports or what, but it seems strange that there should be doubles like that anyway...

---

### Post by Sutekh on 2006-03-09
[QUOTE=kiwibird]The game Cube tells me I need libsdl-mixer, so I try getting it with synaptic, which tells me I need libsmpeg0, searching for which I find I have libsmpeg0c2 already installed. [/QUOTE]

libsdl-mixer actually depends on libsmpeg0c2.  Check it out

[http://packages.ubuntu.com/breezy/libs/libsdl-mixer1.2]("http://packages.ubuntu.com/breezy/libs/libsdl-mixer1.2")

Does Synaptic actually fail when installing libsdl-mixer?  It should work out the dependancies for you so you don't have to worry about this kind of thing

---

