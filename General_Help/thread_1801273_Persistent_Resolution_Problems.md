---
title: "Persistent Resolution Problems"
date: 2011-07-10
forum: General Help
---

### Post by freshtoast on 2011-07-10
Hi,

I've got a resolution issue with 11.04.

The correct resolution for the monitor is 1440 x 900, but this is not detected as an option by ubuntu.

If I run the following I can get the resolution correctly for the rest of the session:
```
xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr --addmode VGA1 1440x900_60.00
xrandr --output VGA1 --mode 1440x900_60.00
```

So my next challenge it to make this persistent. I thought I would make adjustments to xorg.conf however when I attempt to generate an xorg.conf file it fails because "*the number of created screens does not match the number of detected devices*".

I've googled this problem extensively, and although I see that other people have run into this problem I've not actually found a solution.

Any help will be gratefully received!

Edit - I have found a way to do it by adding the above to /etc/gdm/Init/Default just before the line "/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm"... is there a better way?

---

