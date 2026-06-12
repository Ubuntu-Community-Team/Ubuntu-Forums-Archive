---
title: "Disable Wallpaper Fade Effect?"
date: 2009-07-15
forum: General Help
---

### Post by Tipped OuT on 2009-07-15
I have been really annoyed when I change my wallpaper, and my entire system comes to a stand still and lags for about 10 seconds, because of a silly fade effect.

Is there anyway to disable this? It would be greatly appreciated for some help.

I'm on Ubuntu 9.04 Jaunty Jackalope.

---

### Post by DeMus on 2009-07-15
> **Tipped OuT said:**
> I have been really annoyed when I change my wallpaper, and my entire system comes to a stand still and lags for about 10 seconds, because of a silly fade effect.

Is there anyway to disable this? It would be greatly appreciated for some help.

I'm on Ubuntu 9.04 Jaunty Jackalope.

Right-click your desktop and choose Change Desktop Background
Choose the last TAB: Visual Effects
Choose: None

---

### Post by KoKuToru on 2009-10-31
> **Tipped OuT said:**
> lags for about 10 seconds, because of a silly fade effect.

The effect is nice .. the cpu usage is horrible..
There are 4 ways to deactive it:
[LIST=1]
[*]Don't change wallpapers
[*]Deactive GTK+ animations
[*]Use old gnome-desktop package
[*]recompile gnome-desktop (I did)
[/LIST]

I downloaded the souce of gnome-desktop and deactivated the fade..
You can get the source with:
```

apt-get source gnome-desktop

```
..in the libgnome-desktop folder is a file called gnome-bg-crossfade.c 
at the function **animations_are_disabled (GnomeBGCrossfade *fade)**
you change this line:
```

return !are_enabled;

```
to
```

return TRUE

```

Then you run in the folder
```

make && sudo make install

```

and then you move the file
```

/usr/local/lib/libgnome-desktop-2.so.11.4.2

```
to
```

/usr/lib/libgnome-desktop-2.so.11.4.2

```

restart login and woolllaaa the fade-effect is deactivated

[SIZE="4"]you can also change the fade effect to something else ![/SIZE]
I changed it to a slide-effect (as experiment)

Just change this line
```

gdk_cairo_set_source_pixmap (cr, fade->priv->end_pixmap,
				    0.0, 0.0);
cairo_paint_with_alpha (cr, percent_done);

```

to

```

//move from left to right
gdk_cairo_set_source_pixmap (cr, fade->priv->end_pixmap,
				    -(1.0-percent_done)*fade->priv->width, 0.0);
cairo_paint/*_with_alpha*/ (cr/*, percent_done*/);

```

you can watch a video on my blog xD of the effect
[http://kokutoru.wordpress.com/2009/10/31/gnome-desktop-fade-effect/](http://kokutoru.wordpress.com/2009/10/31/gnome-desktop-fade-effect/)
sadly it uses as much CPU as fade-effect

---

### Post by Mike Lynch on 2010-01-29
> **KoKuToru said:**
> The effect is nice .. the cpu usage is horrible..
There are 4 ways to deactive it:
[LIST=1]
[*]Don't change wallpapers
[*]Deactive GTK+ animations
[*]Use old gnome-desktop package
[*]recompile gnome-desktop (I did)
[/LIST]

I downloaded the souce of gnome-desktop and deactivated the fade..
You can get the source with:
```

apt-get source gnome-desktop

```..in the libgnome-desktop folder is a file called gnome-bg-crossfade.c 
at the function **animations_are_disabled (GnomeBGCrossfade *fade)**
you change this line:
```

return !are_enabled;

```to
```

return TRUE

```Then you run in the folder
```

make && sudo make install

```and then you move the file
```

/usr/local/lib/libgnome-desktop-2.so.11.4.2

```to
```

/usr/lib/libgnome-desktop-2.so.11.4.2

```restart login and woolllaaa the fade-effect is deactivated

[SIZE=4]you can also change the fade effect to something else ![/SIZE]
I changed it to a slide-effect (as experiment)

Just change this line
```

gdk_cairo_set_source_pixmap (cr, fade->priv->end_pixmap,
                    0.0, 0.0);
cairo_paint_with_alpha (cr, percent_done);

```to

```

//move from left to right
gdk_cairo_set_source_pixmap (cr, fade->priv->end_pixmap,
                    -(1.0-percent_done)*fade->priv->width, 0.0);
cairo_paint/*_with_alpha*/ (cr/*, percent_done*/);

```you can watch a video on my blog xD of the effect
[http://kokutoru.wordpress.com/2009/10/31/gnome-desktop-fade-effect/](http://kokutoru.wordpress.com/2009/10/31/gnome-desktop-fade-effect/)
sadly it uses as much CPU as fade-effect

Ok, so I did all of the above and while it did, in fact, disable the fade effect, a 10 second delay between background image changes still happens.  E.G.  When the background is switched the wallpaper changes to a solid color for 10 seconds then the new image is displayed.  Any clues on what I have to do to get rid of that so the new image is displayed immediately?  Thanks.

---

### Post by albertu on 2011-01-19
I have the same problem on kde desktop (version 4.5.3)
can anybody help me ?
thanks

---

