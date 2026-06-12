---
title: "Changing Window Border Color?"
date: 2010-03-21
forum: General Help
---

### Post by Tamalin on 2010-03-21
Ok, I have been struggling to change the border color of the windows on Ubuntu without actually changing the theme (e.g., Keeping the "Human" theme, but having the frame borders be a different color than orange.)  I have searched Google for some help, but found nothing that works.  I have gone to System > Preferences > Appearance and set the 'Selected Items' color (as suggested by [http://ubuntuforums.org/showthread.php?p=8926484]("http://ubuntuforums.org/showthread.php?p=8926484"), but to no avail.  Only the controls changed color, not the window borders.  What should I do now?  (I am using 8.04)

---

### Post by blueridgedog on 2010-03-21
System - Preferences - Appearance - Customize, Color Tab, then adjust "windows" color to suit your needs.

---

### Post by Tamalin on 2010-03-21
Well, that just changed my window background color, not the color of the window frame/border.  That's all I really want to do.  None of the options visible seem to indicate I can change this from the "Colors" tab.

[IMG]http://dl.dropbox.com/u/5510944/Screenshot-Customize%20Theme.png[/IMG]

---

### Post by blueridgedog on 2010-03-21
So you want a different color around the window, other than the base color that is typically used for the menu area and such (tabs in Firefox for example?).  I don't think such a thing exists.  You can control the title bar color, the control style, the window color and the scroll bar design.

---

### Post by Tamalin on 2010-03-21
I just found an interesting piece of information.  Changing the "Selected items" color value changes the window border color in every theme except "Human".  Human, I don't know why, seems to want to cling dearly to the color orange.  Unfortunately, this is the style I want to switch colors for...

---

### Post by fanofai on 2011-03-20
I am facing the same problem, of not being able to change the color of the window color. Would also like to add that changing the color in Selected items does not change the color of the border as suggested by Tamalin

I am using Ubuntu 10.10

---

### Post by blueridgedog on 2011-03-20
Gnome Color Chooser my help:

[https://launchpad.net/gnome-color-chooser](https://launchpad.net/gnome-color-chooser)

---

### Post by mcduck on 2011-03-20
> **fanofai said:**
> I am facing the same problem, of not being able to change the color of the window color. Would also like to add that changing the color in Selected items does not change the color of the border as suggested by Tamalin

I am using Ubuntu 10.10
it depends on the Metacity theme you are using.

The theme creator can either specify certain color(s), or make the Metacity theme to pick some color from your GTK theme.

So some themes have fixed color, some might use the window background color from your GTK theme, and some use selected item color from the GTK theme.

The only way to change how a Metacity theme works is to modify the theme. As far as I know there is no graphical tool available for editing Metacity themes, so this is something you'll have to do by hand.

---

### Post by pqwoerituytrueiwoq on 2011-03-20
You may want the emerald theme manager
IIRC you will also need compiz to use it
also i think you will need to use* emerald --replace* to get it working after installation

---

