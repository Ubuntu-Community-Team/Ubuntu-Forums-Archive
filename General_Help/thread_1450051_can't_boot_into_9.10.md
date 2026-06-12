---
title: "can't boot into 9.10"
date: 2010-04-08
forum: General Help
---

### Post by blazini on 2010-04-08
I was trying to get rid of some sound issues, in the process I removed Pulseaudio, then I found a post with a couple of packages from a ppa that were made for using Alsa without pulseaudio. I can't find the link now as I'm on a different pc, but 1 package was named Gnome applet, another Gnome media (I think) and I can't recall the third. It really did nothing so I removed them and reinstalled the Pulseaudio packages to atleast get some sound back. I got right back where I started until I rebooted.

Now it gets to the splash screen, flickers a couple times and I get a giant generic login screen If I log into that, I go back to the splash screen and the same login all over again. I tried to repair packages with the recovery mode but it didn't do any good. I also tried renaming xorg.conf just for the hell of it so a new one would be made but that really didn't do anything either.

Any ideas?

---

### Post by oldfred on 2010-04-08
If you uninstalled gnome you uninstalled the entire desktop (converted it to a command line only server)
This is the GNOME Desktop environment, an intuitive and attractive
desktop, with extra components.

If you can get to a terminal line. log in. This will uninstall everything related to make sure it is a clean reinstall.

sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

Ubuntu continues to use any application that is in use when deleted until you stop using it. So when you rebooted it deleted your desktop.

---

### Post by blazini on 2010-04-08
I was thinking something along those lines, but I thought the packages I installed would safely remove. I can get a command line so I'm gonna go try this now.

---

### Post by blazini on 2010-04-09
Yep, that did the trick.

---

