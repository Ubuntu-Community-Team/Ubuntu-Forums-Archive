---
title: "Xorg very VERY slow"
date: 2010-12-02
forum: General Help
---

### Post by J V on 2010-12-02
I've had this Lucid install since the RC, and now Xorg is frequently found at about 20% CPU usage (According to top) whenever I move any window change workspace or do anything with compiz.

Half a year ago this was a snappy machine, now with Xorg lagging and sucking resources it's almost as bad as vista (Quite a statement don't you think?!)

Anyone know what's wrong with Xorg and/or what I can do to fix it?

I could do a fresh install but I would need to keep my home folder (Which would slow it down) and I was planning on switching to debian squeeze when it came out.

Normal usage is fine, anything involving the window manager now practically freezes the computer until the operation is complete.

---

### Post by sikander3786 on 2010-12-02
Which graphics card is there? Are the proprietary drivers installed?

---

### Post by J V on 2010-12-02
Nvidia 9500 GT, latest propreitary graphics are installed... This was working fine a few months ago so either an update screwed it up or Xorg (Or compiz) gets bloated very quickly...

---

### Post by Decatf on 2010-12-02
Compiz only gets bloated when there are excessive effects and crap enabled. The default configuration for Normal effects should run quite fine assuming your graphics card/driver can handle it and there is nothing wrong with the rest of the system

---

### Post by sikander3786 on 2010-12-03
I would recommend reconfiguring your graphics.

Backup your existing xorg.conf file,

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

If it says the file is not found or something like that, don't worry, proceed to the next command.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot.

See if their is any improvement.

---

### Post by J V on 2010-12-03
> **Decatf said:**
> Compiz only gets bloated when there are excessive effects and crap enabled.Well, there aren't. Just the cube scale application switcher and a few other functions to keep the windows on the correct workspaces.

I've reconfigured xorg but now it's not using the nvidia driver (I'll reinstall it)

Edit: WOOT, Xorg reconfig did the trick, thanks!

---

