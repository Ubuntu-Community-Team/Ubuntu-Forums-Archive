---
title: "Disable all Menu Icons"
date: 2009-11-01
forum: General Help
---

### Post by samrat1985 on 2009-11-01
Before Ubuntu 9.10, I used to remove all icons from 
menu by unchecking 

"Menus have icons" & 
icons from buttons by "gconf - Desktop - Interface - Buttons have icons"

In Ubuntu 9.10 this doesn't work. Though buttons don't have icons
by default but "half" the menu has it like "application" & "Places" part.

How can I remove them completely?

---

### Post by diafanos on 2009-11-01
I have the same problem. And I want to make my desktop/nautilus as iconless :) as possible...

---

### Post by JugglinPhil on 2009-11-01
> **diafanos said:**
> I have the same problem. And I want to make my desktop/nautilus as iconless :) as possible...
Doesn't this look pretty boring?

---

### Post by samrat1985 on 2009-11-01
we all have are choices:) any suggestions as to the problem I posted?

Attached are some of screens of my desktop. jaunty 9.O4

---

### Post by diafanos on 2009-11-01
> **JugglinPhil said:**
> Doesn't this look pretty boring?

No, not boring at all. Especially when you use a dark themed desktop (as I do), the colourful icons make it seems quite ugly... 

IMHO, simplicity is the best...

---

### Post by diafanos on 2009-11-03
*bump*

---

### Post by JockeF on 2009-11-04
It may seem like a small problem. But I quite liked the clean look of my Ubuntu 8.10 installation. The first thing I tried to do when I got my 9.10 running was to remove those ugly (randomly multicolored!!!) menu icons. 
To be fair, 9.10 seem like a super upgrade, I installed the 64 bit version and everything on this Dell D830 works just great! 
But I think Ubuntu should embrace that it can look great for us who hate animations and icon jungles on our desktops. Minimalism! Drop that attention grabbing boot screen too, we do not want to be entertained while booting, not all of us anyway.

---

### Post by samrat1985 on 2009-11-04
[FONT="Courier New"]any ideas anyone?[/FONT]

---

### Post by pulp on 2009-11-05
I do have the same problem. Does a bugreport exist already?

---

### Post by samrat1985 on 2009-11-06
problem : cannot remove menu icons from "[FONT="Courier New"]Applications[/FONT]" & "[FONT="Courier New"]Places[/FONT]" bug of "gnome-panel" ??

---

### Post by PteHarper on 2009-11-06
Do we know if this is getting fixed?

---

### Post by samrat1985 on 2009-11-11
this is not a bug they say!!!

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/478980](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/478980)

---

### Post by major.stubble on 2009-11-11
Seems they are right.  Here is what I think is the relevant code:




Since 2.16
    **gtk_image_menu_item_get_always_show_image ()**

 [gboolean]("http://library.gnome.org/devel/glib/unstable/glib-Basic-Types.html#gboolean")            gtk_image_menu_item_get_always_show_image
                                                        ([GtkImageMenuItem]("http://library.gnome.org/devel/gtk/2.17/GtkImageMenuItem.html") *image_menu_item);  Returns whether the menu item will ignore the ["gtk-menu-images"]("http://library.gnome.org/devel/gtk/2.17/GtkSettings.html#GtkSettings--gtk-menu-images")  setting and always show the image, if available.
  
     *image_menu_item* :
  a [GtkImageMenuItem]("http://library.gnome.org/devel/gtk/2.17/GtkImageMenuItem.html")    *Returns* :
  [TRUE]("http://library.gnome.org/devel/glib/unstable/glib-Standard-Macros.html#TRUE--CAPS") if the menu item will always show the image

CORRECTION:
Should have pasted this entry instead...
**gtk_image_menu_item_set_always_show_image ()**

 void                gtk_image_menu_item_set_always_show_image
                                                        ([GtkImageMenuItem]("http://library.gnome.org/devel/gtk/2.17/GtkImageMenuItem.html") *image_menu_item,
                                                         [gboolean]("http://library.gnome.org/devel/glib/unstable/glib-Basic-Types.html#gboolean") always_show);  If [TRUE]("http://library.gnome.org/devel/glib/unstable/glib-Standard-Macros.html#TRUE--CAPS"), the menu item will ignore the ["gtk-menu-images"]("http://library.gnome.org/devel/gtk/2.17/GtkSettings.html#GtkSettings--gtk-menu-images")  setting and always show the image, if available. 
  Use this property if the menuitem would be useless or hard to use without the image.
  
     *image_menu_item* :
  a [GtkImageMenuItem]("http://library.gnome.org/devel/gtk/2.17/GtkImageMenuItem.html")    *always_show* :
  [TRUE]("http://library.gnome.org/devel/glib/unstable/glib-Standard-Macros.html#TRUE--CAPS") if the menuitem should always show the image    
 Since 2.16

---

### Post by major.stubble on 2009-11-11
Interesting related read.

[http://www.linuxjournal.com/content/gnome-decides-ditch-drawings](http://www.linuxjournal.com/content/gnome-decides-ditch-drawings)

---

### Post by samrat1985 on 2009-11-13
So how do i remove them? Recompile gtk or what? This sucks!

---

### Post by PteHarper on 2010-01-20
So what do we have to do then?

---

### Post by samrat1985 on 2010-01-21
compile gnome from source! I think also try this (I haven't) [http://ubuntuforums.org/showthread.php?t=973564](http://ubuntuforums.org/showthread.php?t=973564) 

I got fed up & removed the upper panel completely & am using gnome-do similar to this ...

[http://ubuntuforums.org/attachment.php?attachmentid=126759&d=1251582356](http://ubuntuforums.org/attachment.php?attachmentid=126759&d=1251582356)

(source - [http://ubuntuforums.org/showthread.php?t=1253074](http://ubuntuforums.org/showthread.php?t=1253074) )

---

### Post by pahatlem on 2010-04-29
bump for justice

---

### Post by Woody1987 on 2010-04-29
Try loading gconf-editor, go to desktop->gnome->interface->uncheck menus_have_icons.

---

### Post by samrat1985 on 2010-05-02
gconf editor doesn't work && I don't think that 
devel guys would pay any attention to these trivial matters @ 1O.O4 :(

---

### Post by tech-no-logical on 2010-05-04
i've 'fixed' it by installing the gnome color chooser, and setting all icon-sizes to 1x1 pixel (0x0 doesn't work unfortunately). the pixels are almost unnoticeable for me, looks a lot better than the fugly icons. haven't noticed any other serious side-effects.

still, not being able to remove icons without re-compiling gtk or gnome is a ridiculous idea. i hope the ubuntu devvers will reconsider in the future.

---

### Post by mbuller10 on 2010-06-01
> **tech-no-logical said:**
> i've 'fixed' it by installing the gnome color chooser, and setting all icon-sizes to 1x1 pixel (0x0 doesn't work unfortunately). the pixels are almost unnoticeable for me, looks a lot better than the fugly icons. haven't noticed any other serious side-effects.

still, not being able to remove icons without re-compiling gtk or gnome is a ridiculous idea. i hope the ubuntu devvers will reconsider in the future.

I installed gnome color chooser and under icons I set Menue to 1 and Start Menue to 1....nothing happened please tell me what to do, I have the atlanta window border installed and the humanity icon theme set

---

### Post by tech-no-logical on 2010-06-02
it could be the theme specifies the icon-size (see the warning in gnome color chooser about that). this solution won't work if that's the case...

---

