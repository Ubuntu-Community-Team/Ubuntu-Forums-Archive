---
title: "Transparent Gnome bars, I cant do it, help"
date: 2010-10-29
forum: General Help
---

### Post by Lancro on 2010-10-29
I tried to look tutorials and stuff, I see a lot of gnome bars, up and down one, transparents, so I installed emerald, and a theme, the theme didnt change them, then I clicked in the upper bar with right button, properties, and found how to made transparent, the center of that bar ¬¬, the sides continues to be the same...

So I give up, Im a noob, how can I made both bars transparent?, the glass efect, I cant, someone helps me?

Thanks.

---

### Post by hhh on 2010-10-29
I think you mean the gnome-panels... this isn't done through theming or Emerald. You were right when you right-clicked a panel, went to Properties>Background>Solid color and then slid transparency to where you wanted it. The "hide buttons" won't go transparent, so in the General tab uncheck the button for "Show hide buttons". Then do it all again for your other panel.

---

### Post by Lancro on 2010-10-29
Yes the gnome pannels, I want them both transparent, with all the stuff on them.

Thanks.

---

### Post by ewz on 2010-10-29
yes you can do it using **Compiz** and **ccsm 'Compiz Config Settings Manager'**, which you can download using **apt** or **synaptic**.

OK this is how I did it, once **ccsm** is installed go to** System - Preferences - Compiz Config Settings Manager**, when opened go to **Accessibility** and click the **Opacity, Brightness,and Saturation** button, in this window you will see towards the bottom **Windows Specific Settings**. Click **New** and copy and paste this into it **(class=Gnome-panel) & ! (type=Menu)** and set the Windows Value to **90** or any number you want, I find 90 is quite good. and your done :-) 

If you want the dropdown menus transparent  as well in the same window click new and copy and paste this into it **Tooltip | Menu | PopupMenu | DropdownMenu** and set the value to 90 

oh, remember to tick **Enable Opacity, Brightness,and Saturation**

:-)

---

### Post by marl30 on 2010-10-29
> **ewz said:**
> yes you can do it using **Compiz** and **ccsm 'Compiz Config Settings Manager'**, which you can download using **apt** or **synaptic**.

OK this is how I did it, once **ccsm** is installed go to** System - Preferences - Compiz Config Settings Manager**, when opened go to **Accessibility** and click the **Opacity, Brightness,and Saturation** button, in this window you will see towards the bottom **Windows Specific Settings**. Click **New** and copy and paste this into it **(class=Gnome-panel) & ! (type=Menu)** and set the Windows Value to **90** or any number you want, I find 90 is quite good. and your done :-) 

If you want the dropdown menus transparent  as well in the same window click new and copy and paste this into it **Tooltip | Menu | PopupMenu | DropdownMenu** and set the value to 90 

oh, remember to tick **Enable Opacity, Brightness,and Saturation**

:-)

Thanks for this tip. Works great for me :D Before coming across this thread, like the OP, I had spent a couple of hours today searching all about on how to get the bars fully transparent.

---

### Post by Lancro on 2010-10-30
Good one, thanks!!!

---

### Post by ewz on 2010-11-03
Noworries all, glad I could help :-)

---

### Post by stinkeye on 2010-11-03
If you want your panel to be fully transparent without also making your
applets transparent see this post.....
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=10032093&postcount=3[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10032093&postcount=3")

You can then right click on panel > properties > background
and change the transparency without the background image for applets remaining.

If you then find your panel text color clashes with your wallpaper you can change the 
color of the text with gnome-color-chooser.

---

