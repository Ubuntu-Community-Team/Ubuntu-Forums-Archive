---
title: "Installing Adobe Flash Player on Xubuntu"
date: 2010-02-26
forum: General Help
---

### Post by morgue on 2010-02-26
Hey guys, I installed the player from both the Add/Remove Applications and downloading with install when asked by Firefox, but neither option works.

It shows as installed but Firefox keeps asking me to install it whenever it needs it...

Any suggestions?

Thanks.

---

### Post by morgue on 2010-02-26
Ok my co-worker found the fix

First we uninstalled the "broken" version

```

sudo aptitude remove flashplugin-installer

```

Then here
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
Download .deb for Ubuntu 8.04 not the APT, which is what I was downloading, since I'm running 9.10... but yeah that fixed it.

Hope it helps.

---

### Post by lovinglinux on 2010-02-26
You can remove any conflicting plugins and install the appropriate version of flash with an [automated installer created by carlee](http://ubuntuforums.org/showthread.php?t=1414595).

For additional tips and instructions see the [COLOR="Sienna"]**Flash Optimization**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

