---
title: "Top panel of default theme 'breaks' above 24 pixels"
date: 2010-10-17
forum: General Help
---

### Post by danbaark on 2010-10-17
Hi,

Using the default theme in Ubuntu 10.10 I find that setting the top panel to more than the defalt 24 pixels size means that the extra pixels you add at the bottom are a different shade. It looks a bit rubbish, is there any way to fix this?

Screenshot attached. Thanks very much.

---

### Post by Dans564 on 2010-10-17
I have noticed the same.  It's because Ambiance uses a picture as the panel background, and when the panel exceeds 24pt it just starts to repeat the picture.  The only workaround would be to make ur own background in gimp that fits the size u want.  Kind of a pain.  Personally i like the clearlooks theme more which uses a color as the panel background allowing you to make it any size u want.  Hope this helps

dan

---

### Post by danbaark on 2010-10-17
Ok Thanks. Do yoou know where this picture is stored so that I could edit it? Also do you know which file controls what is used as a background? Maybe I could just edit that to make it have a colour rather than a picture?

Thanks

---

### Post by roggenschrotbrot on 2010-10-17
```
sudo gedit /usr/share/themes/Ambiance/gtk-2.0/apps/gnome-panelrc
```
search for the line
> bg_pixmap[NORMAL] = "img/panel.png"
and replace it with
> #bg_pixmap[NORMAL] = "img/panel.png"

---

### Post by danbaark on 2010-10-17
Thanks!

---

