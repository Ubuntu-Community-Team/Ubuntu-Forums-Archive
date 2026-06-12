---
title: "Blank screen after a sudo apt-get dist-upgrade"
date: 2011-01-18
forum: General Help
---

### Post by kybishop on 2011-01-18
The only thing I remember being updated is xserver, but I know there were other packages updated.

After the splash screen, a text login is shown. If I do nothing, it goes right to a black screen, but first there are weird red pixels randomly strewn about the screen. If I quickly login via the text screen, it then goes to the same black screen. Either way, there are the weird red pixels and a few flashes of the screen before going black.

This happens 100% of the time.

I have tried:
booting with recovery mode and selecting repair packages (no packages are broken, missing, etc.)
booting with recovery mode and selecting startx with failsafe (same black screen)
booting with older kernels (same thing)

Currently dual-booting into windows to post, help would be greatly appreciated.

---

### Post by Rubi1200 on 2011-01-19
You could try the following:

boot into recovery mode and drop to a command prompt then run these commands:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg
```

Also, what graphics card do you have installed?

---

### Post by Sef on 2011-01-19
> ...after a sudo apt-get dist-upgrade

Sudo apt-get dist-upgrade is not recommended anymore. Instead to upgrade the recommended way,read [this]("http://www.ubuntu.com/desktop/get-ubuntu/upgrade").

---

### Post by kybishop on 2011-01-19
I'm running kubuntu, so the page you linked doesn't apply as I don't have synaptic. Is there an alternative method recommended for upgrading with kubuntu?

I tried downgrading some of my packages in recovery mod, including x (which I imagine does a reconfigure?) but I'll try that command.

My graphics card is an ati mobility radeon 4300 HD
I am running the proprietary drivers.

EDIT: clarification, sudo apt-get dist-upgrade does NOT upgrade your ubuntu (or kubuntu) version, sef I think you're confusing it with a different apt-get command. I forget what it is, but I know it has -d as an option.

---

### Post by kybishop on 2011-01-19
> **Rubi1200 said:**
> You could try the following:

boot into recovery mode and drop to a command prompt then run these commands:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg
```

Also, what graphics card do you have installed?

This worked. Give this man some beans :D
Thanks Rubil, I'll be sure to remember this command.

---

### Post by Rubi1200 on 2011-01-19
> **kybishop said:**
> This worked. Give this man some beans :D
Thanks Rubil, I'll be sure to remember this command.
Excellent! No problem, you are more than welcome :)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

