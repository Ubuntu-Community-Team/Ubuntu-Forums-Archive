---
title: "X11 gone after upgrading server from 9.04 to 9.10"
date: 2009-11-09
forum: General Help
---

### Post by bchurchill on 2009-11-09
Hi all,

I've been using the server edition of Ubuntu 9.04 on my laptop (just so I could pick and choose packages) and had X/gnome working nicely on it.  I upgraded to 9.10 using aptitude yesterday, but now X doesn't seem to work at all.

```

$startx
-bash: startx: command not found

$xinit
-bash: xinit: command not found

$whereis X11
X11: /usr/bin/X11 /etc/X11 /usr/lib/X11 /usr/lib64/X11 /usr/include/X11 /usr/share/X11

sudo /etc/init.d/gdm start
-bash: xinit: command not found

```It seems that the X11 config files are fine as well.  gdm seems to have completely disappeared except for some config files in /etc/gdm.  It seems that at least most of gnome is still installed.

Any idea what happened?

---

### Post by renkinjutsu on 2009-11-09
Have you checked if the packages are still installed on your system?

have tried: ```
sudo aptitude install xinit
```

---

### Post by nothingspecial on 2009-11-09
Try ```
sudo service gdm start
```

---

### Post by bchurchill on 2009-11-09
> **renkinjutsu said:**
> Have you checked if the packages are still installed on your system?

have tried: ```
sudo aptitude install xinit
```

I didn't think this would help since the binaries were still on my computer, but it actually did.  I also had to reinstall gdm to get things to work.  It seems there are a handful of other packages I need to install as well (mostly gnome-related things)... It's kind of annoying that I need to do this.  Oh well.

---

