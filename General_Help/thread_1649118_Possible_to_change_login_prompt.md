---
title: "Possible to change login prompt?"
date: 2010-12-19
forum: General Help
---

### Post by wearetheborg on 2010-12-19
The login prompt is very...unaesthetic.

I managed to change the background by copying over a new image file to some directory. However, there is still the big boring login window. Is there any way to change that? I'd like something darker, and smaller.   

EDIT:I copied over the image file to /usr/share/backgrounds/warty-final-ubuntu.png My image file was actually a jpeg file, but copying it over to /usr/share/backgrounds/warty-final-ubuntu.png posed no problems.

---

### Post by x1a4 on 2010-12-19
Sadly, GDM has been significantly downgraded and (among other important things) graphical themes are not supported.  You can still change the look of the Standard GDM theme like so: 

To change the background
```

sudo -u gdm gconftool-2 -t str -s /desktop/gnome/background/picture_filename /path/to/pic.jpg

```
Where /path/to/pic.jpg is the full path and file name of the background image.

To change the GTK theme
```

sudo -u gdm gconftool-2 -t str -s /desktop/gnome/interface/gtk_theme ThemeName

```
Where ThemeName is the name of the theme.  Look in /usr/share/themes/ for GTK theme names.

---

### Post by OxentroT on 2010-12-19
Try clicking on your panel with main menus, path; *System -> Administration -> Login Window.*

And you can go click to the link below to find more that can suit to you interests and download them. DOn't extract the tar.gz files when downloaded but rather remember where you saved them to and change to them when you are at the GUI for changing the login screen.

[http://gnome-look.org/index.php?xcontentmode=150](http://gnome-look.org/index.php?xcontentmode=150)

Hope this helps!

:guitar:

Happy Holidays!

---

### Post by wearetheborg on 2010-12-20
> **x1a4 said:**
> Sadly, GDM has been significantly downgraded and (among other important things) graphical themes are not supported.  You can still change the look of the Standard GDM theme like so: 

To change the background
```

sudo -u gdm gconftool-2 -t str -s /desktop/gnome/background/picture_filename /path/to/pic.jpg

```Where /path/to/pic.jpg is the full path and file name of the background image.

To change the GTK theme
```

sudo -u gdm gconftool-2 -t str -s /desktop/gnome/interface/gtk_theme ThemeName

```Where ThemeName is the name of the theme.  Look in /usr/share/themes/ for GTK theme names.

 What do GTK themes do? Do they affect the login screen or the theme after login?

---

### Post by x1a4 on 2010-12-20
> **wearetheborg said:**
> What do GTK themes do?
[GTK]("http://www.gtk.org/") is a tool-kit for user interfaces(windows, text boxes, etc.)  On Windows they're called ActiveX controls.  Changing the GTK theme for [GDM]("http://projects.gnome.org/gdm/") should change the standard dialogue box for the login screen.

---

### Post by wearetheborg on 2010-12-20
Thanks guys. I used the instructions here to change to high contrast login prompt: [http://georgia.ubuntuforums.org/showthread.php?t=1616388](http://georgia.ubuntuforums.org/showthread.php?t=1616388)  I would to install new themes for gdm..is this safe?  I have installed new themes in my user account, but I'm a bit security apprehensive doing it while as root.

---

### Post by x1a4 on 2010-12-20
A GTK theme is just a plain text file and occasionally a few images.  There really is no danger.  Sill, installing themes to your user account is fine, except other users will not have access to them.  Don't be afraid to explore your system and look in things.  

A few safe places to get GTK themes include: 

[http://art.gnome.org/themes/gtk2]("http://art.gnome.org/themes/gtk2")
[http://gnome-look.org/index.php?xcontentmode=100]("http://gnome-look.org/index.php?xcontentmode=100")
[http://xfce-look.org/index.php?xcontentmode=100]("http://xfce-look.org/index.php?xcontentmode=100")
[http://customize.org/gtk]("http://customize.org/gtk")
[http://browse.deviantart.com/designs/?q=GTK%20themes]("http://browse.deviantart.com/designs/?q=GTK%20themes")
[http://browse.deviantart.com/customization/?q=GTK%20themes]("http://browse.deviantart.com/customization/?q=GTK%20themes")

You can also write your own themes.  Just have a look [here]("http://live.gnome.org/GnomeArt/Tutorials/GtkThemes").

---

### Post by wearetheborg on 2010-12-21
> **x1a4 said:**
> A GTK theme is just a plain text file and occasionally a few images.  There really is no danger.  Sill, installing themes to your user account is fine, except other users will not have access to them.  Don't be afraid to explore your system and look in things.  


 I am fine with and have installed themes in my user account, I was just apprehensive about installing themes as root.

---

### Post by Chazz44able on 2010-12-27
> **wearetheborg said:**
> The login prompt is very...unaesthetic.

I managed to change the background by copying over a new image file to some directory. However, there is still the big boring login window. Is there any way to change that? I'd like something darker, and smaller.


Sorry, what directory did you put the new picture into to change the login background? The code given for the terminal doesn't work for me

---

### Post by wearetheborg on 2010-12-27
> **Chazz44able said:**
> Sorry, what directory did you put the new picture into to change the login background? The code given for the terminal doesn't work for me

 I copied over the image file to /usr/share/backgrounds/warty-final-ubuntu.png  My image file was actually a jpeg file, but copying it over to /usr/share/backgrounds/warty-final-ubuntu.png posed no problems.

---

### Post by Chazz44able on 2010-12-27
Did you just copy the picture over and then change the name to: "warty-final-ubuntu.png"?
That doesn't work for me, there are loads of other pictures in that directory for you?

---

### Post by Chazz44able on 2010-12-27
dw, I've done it with Ubuntu Tweak, however need to still change the login prompt...

---

### Post by wearetheborg on 2010-12-27
> **Chazz44able said:**
> Did you just copy the picture over and then change the name to: "warty-final-ubuntu.png"?
That doesn't work for me, there are loads of other pictures in that directory for you?

Yes there are other pics in that directory; there is already a "warty-final-ubuntu.png" file which was the default login background. I _**overwrote**_ it with my jpeg file.

I assume you also had a "warty-final-ubuntu.png"  present there? After overwriting it, your login background did not change?

See post #6 in this thread for changing the login prompt, I changed it to high contrast login prompt from the built in themes.

---

