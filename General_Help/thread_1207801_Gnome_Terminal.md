---
title: "Gnome Terminal"
date: 2009-07-08
forum: General Help
---

### Post by renec2006 on 2009-07-08
Can somebody anybody show me how to get rid of these annoying messages or quotes when I launch gnome terminal. It's the one that sometimes has a moose or something like that. It was funny at first, but it now annoying.  Thanks

---

### Post by darolu on 2009-07-08
```
sudo apt-get remove cowsay
```

That should work.

This app usually don't come with Ubuntu, it is on Linux Mint though; I like the slackware quotes more, but yeah both can get annoying in time.

---

### Post by pennacook on 2009-07-08
Sounds like you might have fortune running. Check /etc/bash.bashrc to see if it running fortune and then comment it out.

---

