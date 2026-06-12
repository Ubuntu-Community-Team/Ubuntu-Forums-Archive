---
title: "Serious theme confusion"
date: 2009-09-12
forum: General Help
---

### Post by Comzee on 2009-09-12
Ok, I've never successfully applied a complete theme before to my system.
I get my themes from gnome-look.org, I use the gtk 2.0 ones. Whenever I try to install the theme using the default Ubuntu theme selector, the one that has the themes like "human" and "clearlooks", they never apply. I always revert to getting some program like emerald or gtk-chtheme, which never do what I want and only make certain parts of my desktop change to the theme, like only the window borders.

When I use my Compiz fusion Icon selector, I get the following options.

#Select Window Decoder
: GTK window decoder
: Emerald

#Select window manager
: Compiz
: Matacity

I don't even know what the window decoder or manager have to do with themes but which ever options I select always seems to blow everything up.

A recurring problem I get too is I never get the theme icons to work, like the icon templates for folders and things like that, they never work. It always defaults to the ugly default "gnome" icons.

[http://dl.getdropbox.com/u/486946/themes.jpg](http://dl.getdropbox.com/u/486946/themes.jpg)  EDIT: I don't know the bb code to thumbnail that image?

---

### Post by blackened on 2009-09-12
> **Comzee said:**
> Ok, I've never successfully applied a complete theme before to my system.
I get my themes from gnome-look.org, I use the gtk 2.0 ones. Whenever I try to install the theme using the default Ubuntu theme selector, the one that has the themes like "human" and "clearlooks", they never apply. I always revert to getting some program like emerald or gtk-chtheme, which never do what I want and only make certain parts of my desktop change to the theme, like only the window borders.

When I use my Compiz fusion Icon selector, I get the following options.

#Select Window Decoder
: GTK window decoder
: Emerald

#Select window manager
: Compiz
: Matacity

I don't even know what the window decoder or manager have to do with themes but which ever options I select always seems to blow everything up.

A recurring problem I get too is I never get the theme icons to work, like the icon templates for folders and things like that, they never work. It always defaults to the ugly default "gnome" icons.

[http://dl.getdropbox.com/u/486946/themes.jpg](http://dl.getdropbox.com/u/486946/themes.jpg)  EDIT: I don't know the bb code to thumbnail that image?

In the Appearance Preferences dialog, press the customize button to open a world of oppurtunity.

---

### Post by Comzee on 2009-09-12
> **blackened said:**
> In the Appearance Preferences dialog, press the customize button to open a world of oppurtunity.

I know, it's still gimped though. It won't let me use the themes icon templates and various other things. It's like it only uses half the theme.

---

### Post by blackened on 2009-09-12
> **Comzee said:**
> I know, it's still gimped though. It won't let me use the themes icon templates and various other things. It's like it only uses half the theme.

The vast majority of "themes" that can be had from gnome-look are not themes in the way you're thinking they are: a gtk2 theme contains (unless otherwise specified and including additional files) only a theme for window controls; metacity themes contain files that only alter the look of your window borders, etc.

Most full-fledged themes (using the common definition) come in the form of deb packages that can be installed with dpkg, and often include icons, window decorations, window controls, and more.

---

### Post by Comzee on 2009-09-12
> **blackened said:**
> Most full-fledged themes (using the common definition) come in the form of deb packages that can be installed with dpkg, and often include icons, window decorations, window controls, and more.


Hmm, ok, I didn't know that. When I unpack the gtk themes that I use I can see the .png files for the icons and stuff, idk w/e. Where do I get these full fledged themes?

---

### Post by blackened on 2009-09-13
> **Comzee said:**
> ...When I unpack the gtk themes that I use I can see the .png files for the icons and stuff, idk w/e... 

You can manually install themes very simply: for global installation, copy the theme's top-level directory (as superuser) to /usr/share/themes or, in the case of icons, to /usr/share/icons; for single-user installation place the top-level directory in ~/.themes or, for icons, in ~/.icons.

> **Comzee said:**
> Where do I get these full fledged themes?

For packed full themes look at System -> Administration -> Synaptic Package Manager. Do a search for "theme" under "not installed" status. Should yield tons of results. Stuff you find on the web will usually be tarred/gzipped archives that you have to manually install by extracting and placing them in the appropriate place(s) as described above.

---

### Post by Comzee on 2009-09-13
> **blackened said:**
> You can manually install themes very simply: for global installation, copy the theme's top-level directory (as superuser) to /usr/share/themes or, in the case of icons, to /usr/share/icons; for single-user installation place the top-level directory in ~/.themes or, for icons, in ~/.icons.



For packed full themes look at System -> Administration -> Synaptic Package Manager. Do a search for "theme" under "not installed" status. Should yield tons of results. Stuff you find on the web will usually be tarred/gzipped archives that you have to manually install by extracting and placing them in the appropriate place(s) as described above.

Thanks man, you a pretty kool broski.

---

