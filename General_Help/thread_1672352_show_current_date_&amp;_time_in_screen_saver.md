---
title: "show current date &amp; time in screen saver"
date: 2011-01-20
forum: General Help
---

### Post by trpted on 2011-01-20
I tried to follow the advise at [http://ubuntuforums.org/showthread.php?t=1028362](http://ubuntuforums.org/showthread.php?t=1028362)

While I could follow it: For what I am trying to do, it did not work.

Does anyone know why OR can help figure how to get it working?

Thanks.

---

### Post by stinkeye on 2011-01-21
```
gksudo gedit /usr/share/applications/screensavers/gltext.desktop
```

and change the line beginning with **Exec=**
to
```
Exec=/usr/lib/xscreensaver/gltext -root -text "%A%n%d %b %Y%n%l:%M:%S %p"
```

or

You can download an analogue clock screensaver from here:
[**_[COLOR="DarkRed"]gnome-clock-screensaver[/COLOR]_**]("http://www.d8.dion.ne.jp/~pt2k/software/gnome-clock-screensaver/index_e.html")

You will need to compile it.
See here: [**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=10357188&postcount=5[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10357188&postcount=5")

The clock moves around the screen.
See here to make it static: [**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=10360206&postcount=12[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10360206&postcount=12")

---

### Post by trpted on 2011-01-21
Thank you that helps. :)

Before I mark as solved, how do I make /usr/share/applications/screensavers/gltext.desktop 

not move around the screen (if that is possible)?

Thanks.

---

### Post by stinkeye on 2011-01-21
> **trpted said:**
> Thank you that helps. :)

Before I mark as solved, how do I make /usr/share/applications/screensavers/gltext.desktop 

not move around the screen (if that is possible)?

Thanks.
Don't know,sorry. :(

---

### Post by gmargo on 2011-01-21
Read The Fine Man page...**  gltext(6x)** has options for text movement:
```

-wander           Move the text around the screen.  This is the default.

-no-wander        Keep the text centered on the screen.

```

---

### Post by stinkeye on 2011-01-21
> **gmargo said:**
> Read The Fine Man page...**  gltext(6x)** has options for text movement:
```

-wander           Move the text around the screen.  This is the default.

-no-wander        Keep the text centered on the screen.

```
Thanks.

For static text
```
Exec=/usr/lib/xscreensaver/gltext -no-wander -no-spin -root -text "%A%n%d %b %Y%n%l:%M:%S %p"
```

---

### Post by trpted on 2011-01-23
> **stinkeye said:**
> Thanks.

For static text
```
Exec=/usr/lib/xscreensaver/gltext -no-wander -no-spin -root -text "%A%n%d %b %Y%n%l:%M:%S %p"
```

I tried that, but nope.

Any more ideas, before I try gnome-clock-screensaver?

---

### Post by gmargo on 2011-01-23
After you edit a .desktop file, refresh the desktop cache with:
```

sudo dpkg-reconfigure python-gmenu

```then it should show up, although you might have to log out/in.

---

### Post by trpted on 2011-01-23
Thank you :)

Solved.

---

