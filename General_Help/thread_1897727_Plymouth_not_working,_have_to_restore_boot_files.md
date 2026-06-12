---
title: "Plymouth not working, have to restore boot files"
date: 2011-12-19
forum: General Help
---

### Post by Hovercat on 2011-12-19
I tried changing the boot logo with plymouth, (I used plymouth-manager for help), but every time I restart my computer, there is nothing displayed on the monitor and I have to boot from the Live CD and restore my files in /boot.

How can I get this to work? I'm on 10.04 and kernel 2.6.38-13-generic.

---

### Post by bluexrider on 2011-12-19
if everything is installed but just not working try

```
sudo update-initramfs  -u
```

---

### Post by bluexrider on 2011-12-19
Here is a tutorial for the issue too

[http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html)

---

