---
title: "Lubuntu - Autostart command line applications"
date: 2010-03-23
forum: General Help
---

### Post by madwoollything on 2010-03-23
I'm testing a beta release of Lubuntu 10.04 on an old laptop and am very impressed.

I'm able to autostart applications by adding icons to the ~/.config/autostart directory but have yet to discover where I can autostart command line applications such as xbindkeys and htop.

Which hidden file needs to be edited to autostart xbindkeys and htop?
(In openbox I would have edited ~/.config/autostart.sh)

---

### Post by Alex22 on 2010-11-09
Hi,

[http://ubuntuforums.org/showthread.php?t=1457053](http://ubuntuforums.org/showthread.php?t=1457053)

global:
/etc/xdg/lxsession/Lubuntu/autostart

for current user:
$HOME/.config/lxsession/Lubuntu/autostart

---

