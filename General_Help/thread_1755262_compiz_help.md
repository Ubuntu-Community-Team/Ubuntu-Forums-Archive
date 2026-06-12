---
title: "compiz help"
date: 2011-05-11
forum: General Help
---

### Post by Unguidedone on 2011-05-11
if you check this vid out:

[http://www.youtube.com/watch?v=xC5uEe5OzNQ](http://www.youtube.com/watch?v=xC5uEe5OzNQ)

skip to 1:42

how do i get that window effect?  

thanks : )


[IMG]http://i913.photobucket.com/albums/ac340/Happy_Mask_Salesman/ghaaaaaaaaaaaaaaaa.png[/IMG]

---

### Post by Unguidedone on 2011-05-11
help :(

---

### Post by WorMzy on 2011-05-11
It's the burn animation with randomly coloured fire. You'll need the Animations Add-on plugin, which is (or was) part of the compiz-fusion-plugins-extra package. You'll also need the compizconfig-settings-manager package.

Run ccsm, enable the Animations and Animations Add-on packages
[[IMG]http://img29.imageshack.us/img29/7236/screenshot110511151811.th.png[/IMG]](http://img29.imageshack.us/i/screenshot110511151811.png/)

Next, click the Animations Add-on plugin, expand the Burn settings, and check the Randomly Coloured Fire option.
[[IMG]http://img838.imageshack.us/img838/6619/screenshot110511152132.th.png[/IMG]](http://img838.imageshack.us/i/screenshot110511152132.png/)

Finally, go back to the main screen and click the Animations plugin. Click on the Close tab, and add/edit an effect to use the burn effect for the windows you want.
[[IMG]http://img807.imageshack.us/img807/9462/screenshot110511152426.th.png[/IMG]](http://img807.imageshack.us/i/screenshot110511152426.png/)
Here's what I have mine set to:
```
((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver) & !(name=smplayer)
```

---

### Post by Unguidedone on 2011-05-11
it seems i dont have that add on where can i go to get it?

[IMG]http://i913.photobucket.com/albums/ac340/Happy_Mask_Salesman/effectsarelacking.png[/IMG]

---

### Post by WorMzy on 2011-05-11
Have you installed the compiz-fusion-plugins-extra package?

---

### Post by Unguidedone on 2011-05-11
I was able to get the fire working but not the random colors.  But so far its really fun to play with thanks for the screen shots i was clueless on how to get this to work : )

---

