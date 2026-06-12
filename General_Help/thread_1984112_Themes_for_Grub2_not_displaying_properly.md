---
title: "Themes for Grub2 not displaying properly"
date: 2012-05-21
forum: General Help
---

### Post by satish_j on 2012-05-21
I cannot get the theme (ubuntu2) for grub2 display properly on boot.
1. copied the theme folder to /boot/grub/themes
2. edited /etc/default/grub to add GRUB_THEME=<path to theme txt file in /boot/grub/themes....>
ran update-grub and it detected the theme properly.
Upon reboot,the theme is not displayed properly,i mean splash image is displayed,but the boot options are stucked in a small space at upper
left corner.
I tried uncommenting GRUB_GFXMODE in /etc/default/grub and used various combinations of resolutions,each time updating grub,but the splash image of theme still refuses to display correctly.
Is there any other setting that iam missing?

---

### Post by oldfred on 2012-05-21
I do not use themes, but some info here:

Post Your Grub 2 Themes -  drs305
[http://ubuntuforums.org/showthread.php?t=1823915](http://ubuntuforums.org/showthread.php?t=1823915)
A Beginner's Guide to Theming GRUB2 - towheedm
[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)

---

### Post by satish_j on 2012-05-24
Problem got resolved.
It was the incorrect theme file.I downloaded same theme from another source & replaced the existing one.

---

