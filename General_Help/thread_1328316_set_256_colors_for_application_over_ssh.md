---
title: "set 256 colors for application over ssh"
date: 2009-11-16
forum: General Help
---

### Post by xir_ on 2009-11-16
Hi all

I've just introduced a friend to Ubuntu as he needs an xserver based OS for his research.

He runs an application over ssh and he has told me that it must be run in 256 colours or it wont display.

Anyone know how to set this? Maybe in the .bashrc?

---

### Post by Giblet5 on 2009-11-16
FYI: You can install CygWin under Windows. The X server works quite well...

Ask your friend whether the remote app *requires* an 8-bit (256 colors) visual, or if it requires _at least_ an 8-bit visual.

If it's the latter, it'll just work on higher-color X servers.

If it requires an 8-bit visual, it should install its own colormap and allocate an 8-bit visual for its windows. If it doesn't, it's broken. If the code isn't available for your friend to fix it, then the X server can be forced into 8-bit mode using xorg.conf by changing the default server color depth from ```
    DefaultDepth   24
``` to ```
    DefaultDepth    8
```

---

### Post by xir_ on 2009-11-17
thanks for the help.

I have considered cygwin but it really can bog down windows (his wasn't going to cut it), he does know about linux, but he only ever used it as a number cruncher.

I'm fairly sure that the program requires 8 bit (and doesn't seem to forward that configuration to the client side), so it probably is broken in some way as it's scientific software, which tends to be poorly coded.


Whilst i do appreciate the reply, i would imagine that he doesn't have sufficient privileges to change xorg.conf on the server (but i will check). Is there no way to set his .bashrc on the server to export the xorg display in 256 colours.

---

