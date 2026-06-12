---
title: "X11, cannot open display"
date: 2011-01-30
forum: General Help
---

### Post by chah on 2011-01-30
We're running Ubuntu 10.4 on our server. When I ssh there, I can open xclock and emacs and the GUI appears on my desktop.

But when I try to open evince, I get the following error:
```

$ evince 
X11 connection rejected because of wrong authentication.
Cannot parse arguments: Cannot open display:

$ echo $DISPLAY
localhost:11.0

```

Sorry, I'm not so familiar with X11 and the X-server, I'm not sure how the $DISPLAY variable is used, but I understand it is used.

Anyone have an idea what might be causing this specific program (evince) to fail?

Thanks

---

### Post by dyous87 on 2011-01-30
As far as I can tell evince uses gnome and gtk libraries and will not be able to run with these dependencies installed. emacs and eclock on the other hand do not use any gnome/ gtk libraries.

This article might explain it better then I can.

[http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

---

### Post by chah on 2011-01-30
Thanks for the speed reply dyous. It looks like an excellent, albeit very long article. I'll go through it and hope to find an explanation, and solution there.

---

