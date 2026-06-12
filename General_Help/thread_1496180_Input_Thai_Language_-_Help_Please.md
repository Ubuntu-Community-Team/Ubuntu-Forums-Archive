---
title: "Input Thai Language - Help Please"
date: 2010-05-29
forum: General Help
---

### Post by lannatwin on 2010-05-29
I can't get Thai language input to work.

In "language support" I installed Thai, but it remains grayed out.

[IMG]http://i3.photobucket.com/albums/y80/wimpy1/Screenshot-1.jpg[/IMG]

In "ibus preferences / input method", no languages are shown.

[IMG]http://i3.photobucket.com/albums/y80/wimpy1/Screenshot2.jpg[/IMG]

I added:
"export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus"
to $HOME/.bashrc. No effect.

I added: "ibus-daemon --xim" to startup applications.  No effect.

What am I doing wrong here?

Thank you for any assistance.

---

### Post by lannatwin on 2010-05-29
Solved.  For others struggling with this...  You need to install IBus-m17n.

---

