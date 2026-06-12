---
title: "Installing a GTK+2.0 theme"
date: 2010-03-23
forum: General Help
---

### Post by Carpentr on 2010-03-23
This is my first time installing a GTK+2.0 theme. I downloaded the tarball containing the theme and then extracted it. When I extracted the tarball into a folder, it contained the following files:

[IMG]http://i180.photobucket.com/albums/x173/kingdoms_photos/GTKThemeInstall.png[/IMG]

I'm not sure if it's readable on some computers, but there are two folders within the main folder. They are labeled as gtk-2.0, metacity-1, and a notepad file called "ColorBit" which is the name of the the actual theme.

The notepad file has some writing in it, which reads:
```

[Desktop Entry]
Name=ColorBit
Type=X-GNOME-Metatheme
Comment=

[X-GNOME-Metatheme]
GtkTheme=ColorBit
MetacityTheme=ColorBit
IconTheme=Elementary_1.5.3

```

I'm not sure what to do next, as I have no prior experience with Ubuntu's desktop environment and GNOME. I am running the beta version of Lucid Lynx.

Help would be appreciated. Thanks.

---

### Post by l.billon on 2010-03-23
Hi!
Select your tarball archive in the System -> preferences -> theme, it should do the trick.

---

### Post by darolu on 2010-03-23
The most common way to install themes is to copy those files to /usr/share/themes/<yourthemename>; or you can simply drag the tar.gz file to your themes window.

---

### Post by Carpentr on 2010-03-23
@I.Billon That was a whole lot easier than I thought it would be. Thank you.

@darolu Alright, that'll be good to know incase the other way ever starts being difficult. Thank you.

Once again, thank you both.

---

