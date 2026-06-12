---
title: "Xorg error even after install"
date: 2009-08-10
forum: General Help
---

### Post by bt4-pre-final on 2009-08-10
I am running ubuntu 8.10 (bt4 mod) bt4 = backtrack 4, I load the live cd & get error in xorg that xorg might be overwriting a modified configuration & backs it up to xorg.conf.200xxxx How do I keep that configureation so I can load the desktop? I install it to te hard drive & same exact error occours even if I update the xorg.config with the backup it still overwrites the thing..  it throws me into the horrid terminal every time & I cannot even get the gnome desktop to load after I try fixvesa & restart it keeps on overwriting the needed file.  WHAT is the command to load the gnome desktop from the terminal I am at my wits end getting it to work properly & use it on my main pc that operates in ubuntu 8.10 backtrack 4 mod.....

---

### Post by HappySmack on 2009-11-15
I'm having the same problem only with the backtrack4 mod. All is well in Karmic 32 and 64. I am running a HP dv6605us. I installed the Nvidia driver ver. 190.42 for the 7150m from the Nvidia website (as instructed by BT4 moderators). It generates the xorg.conf and all is well until i reboot. Before i start the Xserver i have to cp /etc/X11/xorg.conf.good /etc/X11/xorg.conf . With xorg.conf.good being the proper xorg.conf that was generated.

 Has anyone had any luck with finding the cause?

---

