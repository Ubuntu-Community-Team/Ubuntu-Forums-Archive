---
title: "True Type Fonts Diplayed Incorrectly"
date: 2011-11-08
forum: General Help
---

### Post by holy_bazooka on 2011-11-08
Hi
After installing some fonts in /usr/share/fonts I have weird font rendering issues with most but not all true type fonts.
I have tried
```
fc-cache -fv
mkfontdir
mkfontscale
locale-gen

``` but to no avail.
Problem seems to be with X because as ssson as lightdm starts and password is typed, that too is displayed as these rectangles instead of usual stars.
I am on ubuntu/xubuntu 11.10 x64.

---

### Post by holy_bazooka on 2011-11-09
For future reference,
was a permissions problem.
I did
```
sudo -i
cd /usr/share/fonts/
chmod 644 *.ttf
```

And the problem was fixed.

---

