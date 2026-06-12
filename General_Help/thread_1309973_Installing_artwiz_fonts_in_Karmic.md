---
title: "Installing artwiz fonts in Karmic"
date: 2009-11-01
forum: General Help
---

### Post by Grimnir512 on 2009-11-01
So I've been trying to install the artwiz fonts in Karmic following this guide: [http://urukrama.wordpress.com/2008/05/25/artwiz-fonts-on-ubuntu-hardy/]("http://urukrama.wordpress.com/2008/05/25/artwiz-fonts-on-ubuntu-hardy/")

However I've hit a stumbling block - "sudo dpkg-reconfigure fontconfig-config" doesn't give me the option to configure anything, and I get no output of any sort. All I want to do is enable bitmap fonts. Suggestions?

---

### Post by Grimnir512 on 2009-11-01
Bump :)

---

### Post by reduzent on 2009-11-02
i had the very same problem and then i did two things and now i don't know whether both were necessary and if not, which one would have helped. anyway, this is what i did:

```
sudo rm /etc/fonts/conf.d/70-no-bitmaps.conf
```

this will remove the disabling of bitmap fonts
then i did this in order to tell X about the path of my artwiz fonts:
```

xset +fp /usr/share/fonts/X11/misc/artwiz-latin1/
```

(you might have to adapt this path, if you do not have artwiz-latin, but some other artwiz collection)

---

### Post by Grimnir512 on 2009-11-02
> **reduzent said:**
> i had the very same problem and then i did two things and now i don't know whether both were necessary and if not, which one would have helped. anyway, this is what i did:

```
sudo rm /etc/fonts/conf.d/70-no-bitmaps.conf
```

this will remove the disabling of bitmap fonts
then i did this in order to tell X about the path of my artwiz fonts:
```

xset +fp /usr/share/fonts/X11/misc/artwiz-latin1/
```

(you might have to adapt this path, if you do not have artwiz-latin, but some other artwiz collection)

Hi there

That worked pretty much perfectly, just had to ln-s 70-yes-bitmaps.conf to /etc/fonts/conf.d/ and it worked :)

---

### Post by reduzent on 2009-11-02
Thanks. That is the way to do it. just for the record:

Forget about the 'xset +fp' command, since it works only for the current session.

Roman

---

### Post by Izobalax on 2009-11-15
> **Grimnir512 said:**
> Hi there

That worked pretty much perfectly, just had to ln-s 70-yes-bitmaps.conf to /etc/fonts/conf.d/ and it worked :)


How do I do this?

/izo\

---

### Post by Grimnir512 on 2009-11-18
> **Izobalax said:**
> How do I do this?

/izo\

First remove the no-bitmaps .conf:

```
sudo rm /etc/fonts/conf.d/70-no-bitmaps.conf
```

Then link the yes-bitmaps .conf:

```
sudo ln -s /etc/fonts/conf.avail/70-yes-bitmaps.conf /etc/fonts/conf.d/70-yes-bitmaps.conf
```

And restart your X server :)

---

### Post by matias_tati on 2009-11-29
Tank you

---

### Post by hv71 on 2010-01-17
Hello all,

I've been giving this a go on Ubuntu 9.10 and I'm not having any luck getting the artwiz fonts to show up when I run xlsfonts in a terminal. They do show up in GTK applikations, however (such as gnome-terminal) .... what I was looking for was to use artwiz with things like dzen2, conky and/or xmobar.... and that doesn't work as long xlsfonts doesn't pick up the artwiz fonts. Any thoughts???

---

### Post by Izobalax on 2010-01-31
> **Grimnir512 said:**
> First remove the no-bitmaps .conf:

```
sudo rm /etc/fonts/conf.d/70-no-bitmaps.conf
```

Then link the yes-bitmaps .conf:

```
sudo ln -s /etc/fonts/conf.avail/70-yes-bitmaps.conf /etc/fonts/conf.d/70-yes-bitmaps.conf
```

And restart your X server :)


That didn't work for me, unfortunately, still can't see the fonts. =[

/izo\

---

