---
title: "Changing the Ubuntu start Icon. (nothing I have read is working!)"
date: 2009-07-11
forum: General Help
---

### Post by Gamfrek on 2009-07-11
I have Ubuntu 9.04 (well, the Super OS version of it...) and I have tried EVERYTHING to change the start icon next to Applications, Places, and Systems.

[IMG]http://yaysd.wikispaces.com/file/view/21.png[/IMG]

I have already tried the way where you go into the gconf-editor, but nothing changes...

[IMG]http://yaysd.wikispaces.com/file/view/Screenshot-Configuration_Editor_-_menu_bar_screen0.png[/IMG]

I don't know why but nothing seems to be working. Can ANYBODY out there help?

---

### Post by dhughes on 2009-07-11
[http://strabes.wordpress.com/2006/10/16/change-the-menu-bar-logo-on-ubuntu-dapper/](http://strabes.wordpress.com/2006/10/16/change-the-menu-bar-logo-on-ubuntu-dapper/)

 That looks like what you're looking for.

---

### Post by Gamfrek on 2009-07-11
How can I create an image with a *.svg extension? You can't in GIMP and that's what I use...

---

### Post by Gamfrek on 2009-07-11
Bump.

---

### Post by drs305 on 2009-07-11
I am running Jaunty 64-bit. The Ubuntu icon on my machine is /usr/share/icons/Human/24x24/places/start-here.png

The quickest way to tell if that is the one you are using is probably to open Gimp, add a mark to it, save it, then refresh the panel, and see if your icon changed, If it did, you have found your icon and can replace it with another of your choosing. You can check it's properties in Gimp to create a similar icon.

```

sudo cp /usr/share/icons/Human/24x24/places/start-here.png  /usr/share/icons/Human/24x24/places/start-here.png.bak
gksudo gimp /usr/share/icons/Human/24x24/places/start-here.png
# make a change, then refresh the panel
killall gnome-panel
# undo the change in gimp or restore the backup copy of the original before saving it.

```

---

### Post by Yvan300 on 2009-07-11
The easiest thing to do is use an icon theme that changes your gnome icon  to one you like.

---

### Post by Gamfrek on 2009-07-11
> **drs305 said:**
> I am running Jaunty 64-bit. The Ubuntu icon on my machine is /usr/share/icons/Human/24x24/places/start-here.png

The quickest way to tell if that is the one you are using is probably to open Gimp, add a mark to it, save it, then refresh the panel, and see if your icon changed, If it did, you have found your icon and can replace it with another of your choosing. You can check it's properties in Gimp to create a similar icon.

```

sudo cp /usr/share/icons/Human/24x24/places/start-here.png  /usr/share/icons/Human/24x24/places/start-here.png.bak
gksudo gimp /usr/share/icons/Human/24x24/places/start-here.png
# make a change, then refresh the panel
killall gnome-panel
# undo the change in gimp or restore the backup copy of the original before saving it.

```


What? I didn't understand any of that! Could you put it into a format like the one that fallows?

1.go here
2.do this
3.ect...

---

### Post by Gamfrek on 2009-07-11
> **Yvan300 said:**
> The easiest thing to do is use an icon theme that changes your gnome icon  to one you like.

And how would that work?

---

### Post by drs305 on 2009-07-11
Gamfrek,

1. Open a terminal (System, Accessories, Terminal).
2. Paste the commands into the terminal one at a time and execute them by hitting ENTER.
  To paste into an ubuntu terminal, copy the command you see normally. to paste into the terminal, use CTRL-SHIFT-V. (Likewise to copy something displayed in the terminal, highlight it and CTRL-SHIFT-C). Even easier, highlight it and you can use your middle mouse button to copy and paste.
3. The commands do:
a. The first line makes a backup of the original ubuntu menu icon. When you run the command, it will ask for your password since you are using "sudo" to alter a system file. Enter your password, you won't see it as you type but it is being recorded. Hit ENTER when you have typed it. If there are no errors, you won't see anything in the terminal window.
b. Open Gimp, a linux picture/bitmap editor. Use another editor if you prefer. Make a change to the file and save it. If you aren't familiar with how to use GIMP, I would recommend you not proceed until you do. Learning how to use GIMP to change this icon is probably more work than you will want to do at this point.
c. This command refreshes the panel. If you put a red dot in the icon with GIMP, see if a red dot appears in the panel. If it did, the file you are working with is the correct icon. If nothing happens, it means you aren't working with the correct icon and you will have to find the answer from someone else.  ;-)

If it is the correct icon, you would save your new icon to the same location and name.

If this is too complicated, I apologize. We deal with a wide variety of experience levels here on the forums. Generally on the Beginners Forum I provide a bit more instruction than I do in the General forum.

---

### Post by Gamfrek on 2009-07-11
YAY!!!! :p Thank you SOOO much!!!

I'm such an idiot!!! :lolflag:

---

### Post by dhughes on 2009-07-12
I see drs305 wrote a nice step-by-step for you.

> **Gamfrek said:**
> How can I create an image with a *.svg extension? You can't in GIMP and that's what I use...

 I searched a bit and see people recommend Inkscape instead of the GIMP (can open but not create .svg graphics) to create Scalable Vector Graphics (SVG), it's in the repositories, just use apt-get or Synaptic to install it.

---

