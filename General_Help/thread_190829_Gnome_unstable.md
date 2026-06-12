---
title: "Gnome unstable?"
date: 2006-06-06
forum: General Help
---

### Post by cleentrax on 2006-06-06
Overall, Ubuntu is quite stable I have it on and active at least 14 hours a day. But my laptop suddenly bumps me out to the login page about twice a week, which means I lose open documents and applications. This doesn't seem to be tied to any particular application or activity. I always have Firefox, Gaim, Evolution and Bittornado (Dapper uploads!!) running. 

I don't think it's a hardware issue, because it doesn't totally reboot, and I never had this issue in Windows. I dont' get a warning message, though there may be something in a log somewhere.

Any thoughts?

Inspiron 8600, 1.2gb RAM, Ubuntu 6.06, nvidia proprietary driver, xgl/compiz.

---

### Post by graigsmith on 2006-06-06
mabey, you are hitting ctrl alt backspace accidently and inadvertently resetting X?  I know some laptop keyboards can be a little small, and are easy to hit certain combinations of keys.

---

### Post by helpme on 2006-06-06
I'd guess that it's an Xgl/compiz issue. After all they are both still pretty much alpha software. 

Did you take a look at the xorg.org logs to see if you can find anything there?

---

### Post by cleentrax on 2006-06-06
[QUOTE=graigsmith]mabey, you are hitting ctrl alt backspace accidently and inadvertently resetting X?  I know some laptop keyboards can be a little small, and are easy to hit certain combinations of keys.[/QUOTE]

Well, the behavior is identical to the resetting of X, but it can happen while I'm away from the computer.

---

### Post by musicinmybrain on 2006-06-06
This probably isn't the cause your problem, but I had this problem when I was running an updated video driver from NVIDIA in Breezy. The resets occurred whenever something (like a screensaver, say) used OpenGL. Turned out I needed to recompile the driver whenever there was a kernel update. This won't be a problem if you're using the nvidia-glx from the repos. Again, probably not what's going on from what you say, but thought I'd throw it out there anyway.

---

