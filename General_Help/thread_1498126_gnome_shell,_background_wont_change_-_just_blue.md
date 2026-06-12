---
title: "gnome shell, background wont change - just blue"
date: 2010-05-31
forum: General Help
---

### Post by keytthom on 2010-05-31
hello, i started using gnome shell yesterday... love it.

but it has decided that the background should just be blue, right pain in the ***. if i start in normal gnome, it is fine, but gnome shell - background is blue.

thanks

---

### Post by fishkid257936 on 2010-06-24
Same thing happening to me, 2. It is very frustrating and also I can't put any icons on the desktop. Can ANYONE help us???!!!!

---

### Post by angry_johnnie on 2010-06-24
good ol' metacity & regular gnome uses nautilus to draw your desktop background.

in the case of gnome-shell, i think you're looking at the root window, which is no longer being managed by nautilus.

you could try setting the background with feh, which is, really, pretty simple.

to install feh

```
sudo apt-get install feh
```

and then to set the background

```
feh --bg-scale /path/to/image.file
```

you could change 'scale' to tile, center, or seamless.

```
man feh
```

would give you all the options.


you could also install xloadimage, instead of feh.  the command to set the background would be xsetbg.

---

