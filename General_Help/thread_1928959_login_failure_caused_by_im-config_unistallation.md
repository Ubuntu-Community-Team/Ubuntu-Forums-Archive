---
title: "login failure caused by im-config unistallation"
date: 2012-02-21
forum: General Help
---

### Post by elephantgod on 2012-02-21
Hi

I'm a linux newbie and i got a login failure when i tried to fix my input method problem.

I can't log into the graphical system. After i input the password, the system go back to the login interface. So i logged in with command line and the **.xession.error **file gives:

```
/etc/gdm/Xsession: Beginning session setup...
.: 20: Can't open /usr/share/im-config/xinputrc.common
```

Actually, i was trying to fix the fcitx input method problem (which is that i cant activate fcitx in emacs), and i installed im-config (which will uninstall im-switch) and then uninstalled in-config and re-installed im-switch. So in fact, there is **no im-config directory** in my /usr/share right now, there is only im-switch directory under /usr/share. So i think what actually happened is somehow the system don't know that i uninstalled im-config and was trying to load a file that doesn't exist.

Does anyone know how to fix this ? Or the "can't activate fcitx in emacs" problem ?

Thank a lot !

---

