---
title: "Removed fonts"
date: 2009-08-12
forum: General Help
---

### Post by akrchstn on 2009-08-12
I installed a new font earlier but when I refreshed awesome wm it looked bad and it was small (even after changing the sizes in the theme file) so I decided to remove it. I removed it from /usr/share/fonts and /usr/local/share/fonts but /etc/fonts/fonts.conf and ~/.fonts were text files that couldn't be read so I just deleted them (i think that's the problem) then I refreshed awesome and the same fonts were still there even after changing the font section in my theme file and going into gnome and changing the fonts back to default. I tried re installing fontconfig packages too but nothing has worked yet

---

### Post by CatKiller on 2009-08-12
> **akrchstn said:**
> /etc/fonts/fonts.conf and ~/.fonts were text files that couldn't be read so I just deleted them

I have no idea what state of mind makes that seem like a good plan. You'd have had to have put in your password for sudo, even.

Anyway, it's possible that ```
sudo dpkg-reconfigure fontconfig-config
```might correct that mistake (although I've never tried it, obviously).

---

### Post by akrchstn on 2009-08-12
Well, suddenly it's fixed..it might have just been the reboot

---

### Post by kerry_s on 2009-08-12
run-> **sudo fc-cache -vf**
and it will fix your font cache files.

---

