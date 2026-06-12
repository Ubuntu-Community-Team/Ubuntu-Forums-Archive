---
title: "Keyboard layout switching in Karmic - Problem"
date: 2010-04-09
forum: General Help
---

### Post by r_avital on 2010-04-09
Hi all,

Just upgraded from Jaunty to Karmic (laptop is MSI gx710), running under gnome.  In Jaunty I could switch the language on the keyboard layout indicator by just clicking on it (I have four layouts set up), it would switch with no problems and even show the corresponding flag.  All works well under Karmic, EXCEPT - I now have to press both shift-keys to switch layouts, mouse-click no longer switches the layout.

What I've tried:

[LIST]
[*]Cleared all options under keyboard preferences for keys to use to switch layouts
[*]Made sure kxkb and xbindkeys were installed and running (not sure that both are relevant here)
[*]Same result.  I can assign any key/combination available from the above-mentioned options menu to switch keyboard layouts, but can't switch by clicking.
[/LIST]
Any thoughts?

---

### Post by r_avital on 2010-04-09
Update:

I found out that if I disable the diplay of flags through the configuration editor, clicking on the indicator does actually switch.  

Yet this is working perfectly on another Karmic system (a desktop), flags and all.

This kind of stuff (and worse) is exactly why I waited until now to upgrade to Karmic.  Sorry, folks, this is a sloppy release.  Only reason I updated from Jaunty is I don't want to make a fresh install of Lucid in three weeks, and there is no direct update from Jaunty to Lucid.

Can anyone tell me what to expect, generally, for this feature in Lucid? I already know the keyboard indicator applet is gone for good, and the keyboard layout indication is done in the notification area, but besides that, how is it working for you? Stable?

Thanks

---

### Post by hotani on 2010-04-14
On a fresh install the keyboard layout is indicated in the notification area. No flags, and no indication of which layout is currently active. I have standard US and Dvorak, only when I mouseover the "USA" in notification area does it show "USA Dvorak" or "USA".

An updated machine behaves differently: there is just a space in the notification area where the indicator would live. There is nothing there. Mousing over, and clicking does nothing. Right-click brings up some options, but no way to change layouts.

--
Edit: On the updated machine, I just went into the keyboard prefs, removed and re-added the "US" layout and now I have the indicator in notification area same as the fresh install. Quirky, but it's working now.

---

### Post by r_avital on 2010-05-03
True, and by default, when you install additional keyboard layouts, they never have flags (not in gnome, anyway).  I followed [this thread]("http://ubuntuforums.org/archive/index.php/t-528890.html") for instructions on how to set them up, but here's a shorter version of the procedure:


[LIST=1]
[*]Download the country flags from Wikipedia (search on each country's name), they shoudl be *.svg files.
[*]Scale them down to 42x47 pixels, in Gimp.  Some have reported that you don't even need to go through that step.
[*]Give the files appropriate names, like us.png for USA, fr.png for France (not france.png), es.png for Spain (not spain.png) etc.  If in doubt, look up the layout name in the keyboard layouts screen.
[*]Store the images in  /usr/share/pixmaps (you'll need sudo cp for that, or gksudo dolphin, etc).
[*]Hit Alt+F2 and enter gconf-editor.  When the editor opens, navigate to desktop>gnome>peripherals>keyboard>indicator on the left pane.  On the right pane, you should see an entry named "showFlags" with an empty box next to it.  Click in the box to place a checkmark in it.
[/LIST]
I resolved the problem of switching between them by assigning the Scroll-Lock key as the keyboard shortcut to switch layouts (in Lucid and Karmic).  Of course, right-clicking on the layout name/flag also brings up a set of options including switching to another layout.

I have to say, placing it in the notification area was the right move, that's where it belongs.

---

