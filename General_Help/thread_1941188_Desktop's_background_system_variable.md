---
title: "Desktop's background system variable?"
date: 2012-03-15
forum: General Help
---

### Post by CProgramming on 2012-03-15
Hello,
Is there system variable for desktop's background path?

such like : ~ = $HOME = /home/username etc.

Thanks ..

p.s. quick reply editor doesn't focusing when clicking

---

### Post by ajgreeny on 2012-03-15
Try **$USER** which should be what you want, I think, though I am not sure exactly what you are asking.

---

### Post by lechien73 on 2012-03-15
Hi,

No - as far as I'm aware, there's environment variable relating to the desktop wallpaper.

The desktop wallpaper settings are stored at the org.gnome.desktop.background key in the dconf database.

---

### Post by CProgramming on 2012-03-15
> **lechien73 said:**
> Hi,

No - as far as I'm aware, there's environment variable relating to the desktop wallpaper.

The desktop wallpaper settings are stored at the org.gnome.desktop.background key in the dconf database.

hey, :)

how do I print the variable in the terminal?

---

### Post by lechien73 on 2012-03-18
Sorry for the delayed response - my laptop had an unfortunate lesson in the power of gravity!

Anyway, to set a shell variable with the path of the background, you can use:

```
BACKGROUND=`gsettings get org.gnome.desktop.background picture-uri`
```

You can export this to be an environment variable with the command:

```
export BACKGROUND
```

---

### Post by tealio on 2012-03-18
So could this be used to keep backgrounds for Plymouth and grub updated with the desktop background?

I've been looking for a way to change the desktop background, and have Plymouth and grub automatically change too.

---

### Post by lechien73 on 2012-03-20
Yes, and to change the desktop background you could supply the **set** argument to gsettings, as follows:

```
gsettings set org.gnome.desktop.background picture-uri 'file:///usr/share/backgrounds/MyNewImage.jpg'
```

Presumably you could use **get** to find the background image, and use the path to set the Plymouth and grub splash.

Maybe you would have to run it using cron. A simple structure might be:

[LIST=1]
[*]Check if the BACKGROUND variable is set. If not, set it.
[*]Periodically check if BACKGROUND == current org.gnome.desktop.background picture-uri
[*]If not, update Plymouth and grub splash (note - you will probably need to add this script to /etc/sudoers using visudo so that it can run without requiring a sudo password.
[/LIST]

---

