---
title: "Most games don't have proper sound on 9.10"
date: 2010-04-01
forum: General Help
---

### Post by Blake. on 2010-04-01
Graphics are fine, but the audio for my 3d games (trigger, TORCS, tuxcart) work for about a minute, and then start making really annoying crackly sounds, and then cuts out over all. Running Kubuntu 9.10 Karmic koala, dual booting with vista. Dedicated 30gigs to Linux. Installed with wubi. Works fine on vista.

---

### Post by Blake. on 2010-04-02
i hate to do this, but........









bump

---

### Post by gabak on 2010-04-02
same problem here

---

### Post by Blake. on 2010-04-02
pointless. at least TRY to help.

---

### Post by Blake. on 2010-04-04
24hrs, bump

---

### Post by kostkon on 2010-04-04
I assume most of them are SDL-based, thus try installing the package
```
libsdl1.2debian-pulseaudio
```

---

### Post by Blake. on 2010-04-04
> **kostkon said:**
> I assume most of them are SDL-based, thus try installing the package
```
libsdl1.2debian-pulseaudio
```

command not found. i just switched to 9.10 kubuntu  to see if that helped, but it did not. is that for normal ubuntu only?

---

### Post by kostkon on 2010-04-04
> **Blake. said:**
> command not found. i just switched to 9.10 kubuntu  to see if that helped, but it did not. is that for normal ubuntu only?
Actually, it is a package you need to install; you can search for it in *Synaptic* and select it for installation or you can give the following command to install it:
```
sudo apt-get install libsdl1.2debian-pulseaudio
```

---

### Post by Blake. on 2010-04-04
seems to have worked. it still krackels every now and again but its WAYYYY better. thanks a bunch!

---

