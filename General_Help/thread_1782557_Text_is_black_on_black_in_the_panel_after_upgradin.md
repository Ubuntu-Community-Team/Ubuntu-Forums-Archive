---
title: "Text is black on black in the panel after upgrading to 11.04, Dust theme"
date: 2011-06-14
forum: General Help
---

### Post by SirPsychoMantis on 2011-06-14
Just upgraded my netbook to 11.04 and now for the Dust theme the text (such as the time) is black on the black background on the Unity panel.  In the settings the text options did not change the text color in the panel.

Anyone know how to get the text to be white instead?

---

### Post by danep on 2011-07-13
I'm also experiencing this- text on the menu bar ('File', 'Edit', 'View', the system clock, etc...) is completely unreadable with the Dust theme.

---

### Post by bapoumba on 2011-07-13
[https://bugs.launchpad.net/unity/+bug/730968](https://bugs.launchpad.net/unity/+bug/730968)

---

### Post by danep on 2011-07-13
Thanks- that seems like the proper place to discuss this. Unfortunately, I tried the fixes mentioned in that issue but none of them worked.

Jeff is absolutely right when he says "This kind of thing is going to stir a LOT of bad sentiment when our  established user base upgrades from Maverick or older to Natty"...

---

### Post by bapoumba on 2011-07-13
I even have this bug with other themes.

I did not try any fix and had no time to comment or troubleshoot. I just chose a working theme. Themes and looks etc. are not that important to me, I have been using the same background pic for a long time :)

---

### Post by danep on 2011-07-20
Does anyone know what the heck you need to do to get things back to 'defaults', i.e. not black-on-black? I've tried reinstalling the Dust theme (via gnome-themes-ubuntu) but it doesn't help.

---

### Post by danep on 2011-07-20
Ahah- I added the following line to the gtkrc file in the Dust theme folder:
text[NORMAL] = @selected_fg_color

This follows the advice at [http://ubuntuforums.org/showthread.php?p=11024027#post11024027](http://ubuntuforums.org/showthread.php?p=11024027#post11024027)

Yeesh, what a mess. Why should that be necessary?

---

### Post by Dummy321 on 2011-07-24
Hi all

Firstly I am a noob on themes. But I have found a solution, although for a different theme....

I am using the Balanzan Theme where the unity panel is dark brown with black text on Natty 10.04. Naturally this is not kosher.....

Other threads and help did not solve my problem as they either did not focus on the right file or theme. Most of the advice focused on the usr/share/themes/yourtheme/gtk-2.0/gtkrc file. The items that controls the font color on the upper panel is specified by "text[NORMAL]      = @text_color". However, in my case this was in the section "style "theme-default" section. When I changed that to white, it also changes the font color in the terminal window and thus was not useful.

Basically all themes differ on the files that they contain and the theme engine that they use. Sometimes the author uses different techniques to set the color/fonts, etc. The problem is to find the correct setting to change.

In my case it was in the file "panel.rc" . You have to find the file that works for you.
In my case the author chose to define a style and define parameters in that. He then allocated this style to the "class "PanelApp*"        style "theme-panel". It is just a matter of browsing your files and common sense....

I then added the defintion "text[NORMAL]       = "#FFFFFF" " under the "style "theme-panel" " and , voila, it worked. The upper panel is still referred to as a panel (well I think so).

In any case to apply it, go to the system settings/appearances and change the them to another one and back, and the new modified theme is applied.

---

