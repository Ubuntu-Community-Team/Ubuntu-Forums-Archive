---
title: "05_debian_theme"
date: 2010-06-06
forum: General Help
---

### Post by rymar115 on 2010-06-06
I seem to have a problem with the 05_debian_theme script there is an error in it that I can't find. When trying to update grub I get the following message /etc/grub.d/05_debian_theme: line 48: unexpected EOF while looking for matching ``'
I have gone over this file repeatedly and I'm stumped. I have attached a copy of the script.

---

### Post by Leppie on 2010-06-06
i think the error is here (line 26):
```
# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in [COLOR=Red]{/boot/grub,/usr/share/images/desktop-base}/Plasma-lamp.{png,tga} ${WALLPAPER}`[COLOR=Black] ${WALLPAPER}[/COLOR][/COLOR][COLOR=Black] [/COLOR]; do
```
as it looks like you've merged two different versions here...
try the following:
```
# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in [COLOR=Red]{/boot/grub,/usr/share/images/desktop-base}/Plasma-lamp.{png,tga}[COLOR=Black][/COLOR][/COLOR][COLOR=Black] [/COLOR]; do
```

---

### Post by rymar115 on 2010-06-06
Thanks that seems to have done the trick

---

### Post by Leppie on 2010-06-06
you're welcome

---

