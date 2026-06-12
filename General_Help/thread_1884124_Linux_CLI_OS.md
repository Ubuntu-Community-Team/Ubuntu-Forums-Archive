---
title: "Linux CLI OS"
date: 2011-11-20
forum: General Help
---

### Post by PCFreak2 on 2011-11-20
Is there a Linux/Unix OS that works off of just a CLI
NO GUI??
Similar to Ubuntu Server, but with no server??

Thanks!!

---

### Post by lechien73 on 2011-11-20
Well...you can perform a minimal installation of Ubuntu, by using [this link]("https://help.ubuntu.com/community/Installation/MinimalCD").

Additionally, you can re-purpose Ubuntu after installation. From a terminal window type:

```
sudo tasksel
```

Uncheck the desktop and front-end options, and just have "Ubuntu Basic Server" checked.

Or, you could try a distro like Arch.

---

### Post by papibe on 2011-11-20
You can install Ubuntu using the 'Minimal Installation CD'. If you choose the command line option, you end up with a text base OS.

You can find the CD downloads [here]("https://help.ubuntu.com/community/Installation/MinimalCD"), and this is nice a [tutorial]("http://www.psychocats.net/ubuntu/minimal") on how to do it.

Note that because of a bug, you may boot into a black screen, but pressing Ctrl+Alt+F1 solves it. To solve it for ever, take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1873069&highlight=minimal"). 

I hope this works for you.
Regards.

---

### Post by PCFreak2 on 2012-02-28
Thanks dude
Works great dual-booting with my Windows ME rig

Decided on Debian 6.0.4 without GUI
Installed fxce4

---

