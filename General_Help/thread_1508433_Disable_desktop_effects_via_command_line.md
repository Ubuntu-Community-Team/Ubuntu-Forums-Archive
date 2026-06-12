---
title: "Disable desktop effects via command line?"
date: 2010-06-12
forum: General Help
---

### Post by 4rk3typ3 on 2010-06-12
I have a computer I'm using as a media server, I currently have Ubuntu 10.04 on it and I've installed Boxee as my media program. It works great, however, if I have any desktop effects enabled when it starts then video playback is very jumpy. Disabling the effects resolves this but Boxee is a fullscreen program and I'd like to be able to tie it into a script that disables the Desktop Effects and starts Boxee so that I don't have to worry about it. Is there any easy way to do this like an on/off switch?

I just need the command for the desktop effects, I'll take care of the rest.

---

### Post by kerry_s on 2010-06-13
off = metacity --replace
on = compiz --replace

---

### Post by 4rk3typ3 on 2010-06-13
Thanks a bunch!

---

