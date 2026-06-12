---
title: "Back to text mode"
date: 2010-03-31
forum: General Help
---

### Post by eng_asa on 2010-03-31
Hi,

As I am new in linux. I was playing with its features and lost my GUI (login screen window)

I have Ubuntu 9.10 and I know that it is using X11. and many were recomended to use gdm.
So I installed gdm2.2 by synabtic. but after that found that I have a problem with non-unicode display.
So I uninstalled gdm :(

Now when I start my laptop. I can login via a screen window. I always get to TTY (text mode)

I tried init 2 & CTRL+ALT+F7 but no way. I think by installing gdm I removed some main pkgs and by uninstall it lost every thing!

How can I fix that and back my GUI ??7

Thanks.

---

### Post by nothingspecial on 2010-03-31
Did you remove evolution?

With a wired connection from "text mode"

```
sudo ifconfig eth0 up
sudo dhclient
sudo apt-get install ubuntu-desktop
```

---

### Post by eng_asa on 2010-03-31
Many thanks.

---

### Post by nothingspecial on 2010-03-31
No problem, it`s a common pitfall :D

---

