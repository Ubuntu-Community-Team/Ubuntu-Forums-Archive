---
title: "xrandr permanent new resolution? (I searched)"
date: 2010-02-07
forum: General Help
---

### Post by ciaastek on 2010-02-07
Hi

As I mentioned in topic title I searched a little about this one but nothing worked, sadly. 

So, I think that it's well-known problem. I have Ubuntu Karmic and Intel's integrated graphics. And I can't set 1280x1024 resolution. So I'm doing cvt, xrandr newmode, addmode, output and - PUFF! - there it is. But then it goes to restart aaaaand it's not looking good. 1024x768 again. 

And! What I tried:
1. put my file in /etc/init.d 
here's my file:
```
#!/bin/bash

xrandr --newmode "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA1 "1280x1024"
xrandr --output VGA1 1280x1024
```

2. /etc/gdm/Init/Default changes (before initctl -q emit login-session-start DISPLAY_MANAGER=gdm)

Anything else? Please help. I had previous installation and I had it working. But I don't know how :/

---

### Post by mushwars on 2010-02-07
Xorg-server doenst think your card can support that resolution. Here might be the solution

you need to stop gdm and then killall Xorg

then run sudo X -configure
make a backup of your old /etc/X11/xorg.conf and move the new one in.

If this doesnt fix it then you are probably using either the wrong driver for your graphics or you are using the free driver and you need the non-free one.

Do you mind telling me what kind of graphics card you have. 

Also try going to system -> admin -> and then the item that says something about drivers.

If you can install the restricted drivers from there that would be the best option.

---

### Post by mushwars on 2010-02-07
I point you to this thread

[http://ubuntuforums.org/showthread.php?t=1399308](http://ubuntuforums.org/showthread.php?t=1399308)

---

### Post by ciaastek on 2010-02-08
Graphics:

```
ciaastek@ubuntu-desktop:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)
```

And my xorg.conf ;) 

```






```

And the System>Admin>Drivers says (something like this because I have polish language) "This system doesn't use possesive(?) drivers"

---

