---
title: "Tweaking Xubuntu!"
date: 2011-10-19
forum: General Help
---

### Post by xtremo on 2011-10-19
I've recently installed Xubuntu 11.10 because I just can't get on with Unity.

It runs well.....and I'm generally quite happy with it.

But one thing I miss (and really need as I'm a web developer) from Gnome 2 is the right click Nautilus Image Converter.

That thing saved me so much time it was unreal....50 pics resized in seconds.....but now I've lost it.

So....is there any similar option you can suggest on Xubuntu?

---

### Post by Toz on 2011-10-19
Thunar (the default xubuntu file manager) supports Custom Actions. Here is a link to a page of thunar custom actions, including one for resizing images. Look for the post by aicardi.

[http://salinelinux.proboards.com/index.cgi?board=software&action=print&thread=98]("http://salinelinux.proboards.com/index.cgi?board=software&action=print&thread=98")

---

### Post by xtremo on 2011-10-19
Thanks....I'll check it out!

---

### Post by ajgreeny on 2011-10-19
Have you tried installing nautilus and the resize plugin as it will also work in xubuntu, I think.

---

### Post by xtremo on 2011-10-19
> **ajgreeny said:**
> Have you tried installing nautilus and the resize plugin as it will also work in xubuntu, I think.

I'm sure I read somewhere that it wouldn't.

---

### Post by Toz on 2011-10-19
I just tested that script ([http://salinelinux.proboards.com/index.cgi?board=software&action=print&thread=98]("http://salinelinux.proboards.com/index.cgi?board=software&action=print&thread=98")) and its not working properly. Let me see if I can muscle my way through it and figure out whats wrong.

---

### Post by Jose Catre-Vandis on 2011-10-19
Here's a script and custom action I use to resize with convert. I could have made it more complicated (e.g. size choices etc with zenity) but instead I just added 2 or 3 of my most converted to sizes as individual custom actions.

Command in custom action:

```
/home/user/320.sh %F
```

bash script in ~/home/user/320.sh:
```
#!/bin/bash

for i in "$@"
do
convert "$i" -set filename:original %t -bordercolor black -border 1 -resize 320x 320x-%[filename:original].jpg
done
```

This script will create a new file, resizing the image to 320px wide whilst maintaining the aspect ratio for the height, and putting a thin black border around the image. edit to suit.


Or you can use gThumb's (now installed by default in 11.10) resize Tool

---

### Post by Toz on 2011-10-19
That's a nice clean script - much better than the one I linked to. Thanks for sharing.

---

### Post by xtremo on 2011-10-20
Had to put the desktop back to 11.04.....no Nautilus Image Converter is a deal breaker for me.

Xubuntu 11.10 will stay on the desktop as it's not used that much, and it'll give me the opportunity to check out the options listed here, and any other tweaks.

Thanks for the help guys!

---

### Post by nothingspecial on 2011-10-20
You could use xfce on top of Ubuntu.

---

### Post by Gatemaze on 2011-10-21
> **xtremo said:**
> Had to put the desktop back to 11.04.....no Nautilus Image Converter is a deal breaker for me.

Xubuntu 11.10 will stay on the desktop as it's not used that much, and it'll give me the opportunity to check out the options listed here, and any other tweaks.

Thanks for the help guys!

Why not install gnome-shell on top of xubuntu? Or the traditional gnome2: see [http://ubuntuforums.org/showthread.php?t=1859961](http://ubuntuforums.org/showthread.php?t=1859961)

---

