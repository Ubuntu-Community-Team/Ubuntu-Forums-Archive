---
title: "Error installing Wesnoth game"
date: 2006-05-20
forum: General Help
---

### Post by handband2 on 2006-05-20
I'm running Ubuntu Breezy and from the Dappers Universe Collection I tried to install the game Wesnoth ([http://www.wesnoth.org/](http://www.wesnoth.org/))

Does anyone know how to fix this error:

E: /var/cache/apt/archives/libsdl-net1.2_1.2.5-3_i386.deb: trying to overwrite `/usr/lib/libSDL_net-1.2.so.0', which is also in package sdl-net

To give a little more information on my situation.  At first I tried to install everything (the game and dependencies) from source but when I tried to compile the game it would not see libsdl-net so I decided to just add Dappers Universe Collection and install it from there.

Now I get the error above. :-k 

Thanks!!

---

### Post by sinkxdie on 2006-05-20
Did you do it as root?

---

### Post by handband2 on 2006-05-20
Yea, I recall making the file as user then installing it as root (sudo).

---

### Post by handband2 on 2006-05-20
Found the problem ... I needed to uninstall the package sdl-net.  :p

---

