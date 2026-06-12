---
title: "Starting Ubuntu without GDM no sound"
date: 2010-05-10
forum: General Help
---

### Post by Oddbio on 2010-05-10
I want to run the ratpoison window manager without GDM. By getting a terminal login and typing "startx"

I have all that setup. But, if I start ratpoison WITH GDM I get sound just fine. When I start it without GDM I get no sound.

The only error message I see that could help figure out what is wrong is at the login screen:

```
[   23.392035]AC'97 1 access is not valid [0xffffffff], removing mixer.
[   23.392237] ali mixer 1 creating error.
```When I start it with GDM I can type "alsamixer" to change the volume successfully.
However, when I start ratpoison without GDM then typing "alsamixer" says "cannot open mixer: No such file or directory"


I could use GDM but then I don't get wireless access. The tutorials I found are for doing it this way. This is the closest I've come to the setup being perfect.
I just need sound.
I am guessing that Ubuntu relies on GDM by default to start whatever it needs for audio so now I probably have to do it manually, I just don't know what needs to be done.

Please help.

---

### Post by Kappy on 2010-07-02
Hi,
I spent a lot of time with this problem too. The solution is simple. You must add user to the group **audio** (adduser <username> audio) and restart system.

:-)

---

