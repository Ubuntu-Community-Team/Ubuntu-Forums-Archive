---
title: "SDL sound"
date: 2011-06-16
forum: General Help
---

### Post by chips24 on 2011-06-16
Im not sure where to post this, so please move if its not in the right place, its not something I deal with everyday.

How do i install the SDL sound package? Im sure i have it, but how do I make my terminal read it? where can i find it if i have it?


checking for SDL - version >= 1.0.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version >= 1.0.0 not found.

---

### Post by chips24 on 2011-06-16
i found the missing files, and i moved them into their proper places, but my terminal is still not recognizing it.

---

### Post by chips24 on 2011-06-20
any help?

---

### Post by Yellow Pasque on 2011-06-20
```
sudo apt-get install libsdl1.2-dev libsdl-sound1.2-dev
```
Also, you may need to use --prefix=/usr option. If that stuff doesn't work, give more detail about what you're trying to do.

---

