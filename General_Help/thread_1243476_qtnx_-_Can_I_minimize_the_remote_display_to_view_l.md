---
title: "qtnx - Can I minimize the remote display to view local display?"
date: 2009-08-18
forum: General Help
---

### Post by mjwalfredo on 2009-08-18
I wasn't really sure where to ask this question and it doesn't seem that qtnx is very popular here at Ubuntu Forums but maybe I will get lucky...

Does anyone know how I can minimize the qtnx display of my remote machine so that I can work with the local machine without logging out of the session on the remote machine?

---

### Post by mjwalfredo on 2009-08-18
Well, I solved my own problem.  Ctrl + Alt + F will toggle fullscreen mode.  I ended up installing NoMachine's FreeNX client and found the fullscreen toggle command for it.  It just happened to be the same for qtNX.

I am not sure which client I like better.  qtNX fits my gnome theme but the freenx client doesn't segfault every time I log out from my remote session.

---

### Post by midden on 2011-03-12
Ah, you saved my bacon. I have been stuck in fullscreen mode and the only way I could get back to my local screen was logging out of the remote session. Ctrl-Alt-F works like a charm.

I have been playing around with both qtnx and freenx clients and prefer qtnx so far. The fullscreen mode is working without any hitches. My only complaint is I can't figure out how to suspend my session like I can on freenx.

EDIT: I finally figured out the suspend thing -- just exit full screen and then close the window. A dialog box will open asking if you want to suspend or terminate the session. If you suspend it, you are given the option to resume it the next time you log into qtnx. Fantastic.

---

