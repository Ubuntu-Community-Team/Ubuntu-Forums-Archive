---
title: "Text-based login"
date: 2009-10-11
forum: General Help
---

### Post by Bit101 on 2009-10-11
I've been trying to get a text-based login on 9.04 nad just can't. When I disable GDM, it loads up fine, let's me log in through console/TTY but refused to let X load. Every time I run startx if just flickers a bit to the X(TTY7) screen, then X dies. Any help?

---

### Post by Bit101 on 2009-10-11
Bump?

---

### Post by yabbadabbadont on 2009-10-11
You say that you use startx, but you haven't said if you have configured your ~/.xinitrc file.  Ideally, it (startx) should at least drop you into a failsafe xterm if you haven't configured .xinitrc, but I know that Ubuntu changes a lot of stuff from upstream.

---

### Post by wojox on 2009-10-11
If startx doesn't work try:

```
sudo /etc/init.d/gdm start
```

---

### Post by Bit101 on 2009-10-11
> **wojox said:**
> If startx doesn't work try:

```
sudo /etc/init.d/gdm start
```

That's currently what I have to do, however it sort of defeats the purpose since it just starts up the GDM login manager. however, it DOES get X to start up correctly

---

### Post by wojox on 2009-10-11
Like yabdba said create a .xinitrc file in your home dir. Make it executable.

Add:

```

#!/bin/sh
exec gnome

```

Then startx or xinit

---

### Post by yabbadabbadont on 2009-10-12
> **wojox said:**
> Like yabdba said create a .xinitrc file in your home dir. Make it executable.

Add:

```

#!/bin/sh
exec gnome**-session**

```

Then startx or xinit

There, fixed it for you.  :D

Also, execute permissions are unneeded.
```
/home/daffy $ ls -la ~/.xinitrc
-rw------- 1 daffy daffy 39 2009-09-26 22:00 /home/daffy/.xinitrc
/home/daffy $ cat ~/.xinitrc
startfluxbox > ~/.xsession-errors 2>&1

```

---

### Post by Bit101 on 2009-10-12
...In hindsight, that should have been incredibly obvious to me. But thank you for your help guys, it works like a charm.

---

### Post by Bit101 on 2009-10-12
Actually, I have reached a new problem. Sound no longer works when done from X. However, if I type in cvlc <music_file.mp3> into a TTY, the sound plays.

---

### Post by Bit101 on 2009-10-12
Bumpity bump

---

### Post by yabbadabbadont on 2009-10-12
You should probably mark this thread solved and then start a new one, with an appropriate subject line, in the Multimedia subforum.

(and you shouldn't bump more often than every few hours.  if the mods notice, you'll get an infraction.)

---

