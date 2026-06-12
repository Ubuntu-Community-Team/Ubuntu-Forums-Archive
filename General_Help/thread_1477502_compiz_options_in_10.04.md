---
title: "compiz options in 10.04"
date: 2010-05-08
forum: General Help
---

### Post by kmsalex on 2010-05-08
I've recently done a clean install of 10.04 on my main laptop. Now major probloms with 10.04 it's self (though i fond that 2.6.32-22 kernal has a major memory leak) but thats besides the point now with the latest version of compiz that's in the repositrys for 10.04 i've noticed a few options removed such as 3D window layers when your in the cube, the cube deformations that turn the cube into a cylinder, drawing fire on the screen, a few others i can't remember but am shour are gone. now my question is there any way to add these features back to my existing compiz install or is there a way to revert to an earlier version?

Any help is greatly appreciated, i miss my old compiz:sad:

---

### Post by WorMzy on 2010-05-08
Have you got compiz-fusion-plugins-extra installed?

---

### Post by kmsalex on 2010-05-08
No i did'nt but doing a 
```
apt-get install compiz-fusion-plugins-extra
```
did get my compiz to look the way it used to:p thank you for that!
but I've seen some even more extram stuff that compiz can do in different youtube videos such as 
[http://www.youtube.com/watch?v=rIZlpSB0vlI](http://www.youtube.com/watch?v=rIZlpSB0vlI)
are there any other add-on's for compiz?

---

### Post by WorMzy on 2010-05-08
The fire is contained in a plugin called "Animations Add-on" and enabled through the "Animations" plugin (kept in compiz-fusion-plugins-main), and the water is called "Water Effect" (kept in compiz-plugins).

The dock at the bottom is called cairo-dock, but it's not a compiz plugin.

Oh, and the wobbly windows are kept in compiz-plugins too.

---

### Post by kmsalex on 2010-05-08
drawing fire and the water affecti  have the wobly windows i have, and i know that the dock is separate i was more interested in getting the windows to burn onto and off of the screen. is that also in the animations add-ons? if so do you think you could coach me though how to set it up?
p.s. that video was a bit of a bad example but it was all i could find on short notice.

---

### Post by WorMzy on 2010-05-08
Yes, that's what I meant by the fire. I have that effect for closing my windows.

Please forgive the cruity of these screenshots.

_[COLOR="Red"]STEP ONE[/COLOR]_
[[img]http://www.ubuntu-pics.de/thumb/59595/compizconfig_settings_manager_013_2fvwPL.png[/img]](http://www.ubuntu-pics.de/bild/59595/compizconfig_settings_manager_013_2fvwPL.png)
Make sure you have "Animations Add-on" and "Animations" enabled. Then click "Animations".

_[COLOR="Red"]STEP TWO[/COLOR]_
[[img]http://www.ubuntu-pics.de/thumb/59598/compizconfig_settings_manager_016_kJy3fi.png[/img]](http://www.ubuntu-pics.de/bild/59598/compizconfig_settings_manager_016_kJy3fi.png)
Click "New", and in the pop-up box, change the effect to "Burn", the duration to 200, and enter this for the window match: ```
((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)
```
Click close, then select it in the list and click "Up", until it is at the top of the list. Repeat for the close animation, minimize animation, etc, if you want to.

_[COLOR="Red"]STEP THREE[/COLOR]_
There is no step three. ;D

---

### Post by kmsalex on 2010-05-08
thank you so much! this is what I've wanted out of compiz since i first started using it!

---

### Post by cmpgm88 on 2010-06-07
> **WorMzy said:**
> Yes, that's what I meant by the fire. I have that effect for closing my windows.

Please forgive the cruity of these screenshots.

_[COLOR=Red]STEP ONE[/COLOR]_
[[IMG]http://www.ubuntu-pics.de/thumb/59595/compizconfig_settings_manager_013_2fvwPL.png[/IMG]]("http://www.ubuntu-pics.de/bild/59595/compizconfig_settings_manager_013_2fvwPL.png")
Make sure you have "Animations Add-on" and "Animations" enabled. Then click "Animations".

_[COLOR=Red]STEP TWO[/COLOR]_
[[IMG]http://www.ubuntu-pics.de/thumb/59598/compizconfig_settings_manager_016_kJy3fi.png[/IMG]]("http://www.ubuntu-pics.de/bild/59598/compizconfig_settings_manager_016_kJy3fi.png")
Click "New", and in the pop-up box, change the effect to "Burn", the duration to 200, and enter this for the window match: ```
((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)
```Click close, then select it in the list and click "Up", until it is at the top of the list. Repeat for the close animation, minimize animation, etc, if you want to.

_[COLOR=Red]STEP THREE[/COLOR]_
There is no step three. ;D

Curious, but how did you do the window decorations?

---

### Post by WorMzy on 2010-06-07
I used Emerald window decorator and made a custom theme. You can download it here if you're interested: [http://compiz-themes.org/content/show.php?content=125845](http://compiz-themes.org/content/show.php?content=125845)

Edit: Wait, that's the latest version. I haven't uploaded the older "solid" button version. Would you like me to upload it?

---

