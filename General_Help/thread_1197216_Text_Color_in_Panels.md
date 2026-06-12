---
title: "Text Color in Panels"
date: 2009-06-25
forum: General Help
---

### Post by robobart on 2009-06-25
Hi,

I want to change the Text color in the panel.

It is easy to change the background color - but the text color is tied to the theme, which I don't want to change. 

I did some searching, and it appeared that I should create 

$ ~/.gtkrc-2.0 

with the following in it

style "my_color"
{
fg[NORMAL] = "#E6E6E6"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"


However, I've logged out and back in but this seems to have no effect.

Any suggestions?

Thanks!

---

### Post by Tyke91 on 2009-06-25
E6E6E6 will give you an off shade of white.

is that what you wanted? :)

if you wanna see if it really worked, try something like FF0000


EDIT: I tried this. The text that was directly related to the panel changed, but the Applications/Places/System buttons didn't change and neither did the username button. You need to find more widgets (probably widget button and menu item or something) and change those as well

---

### Post by robobart on 2009-06-25
Ah you're right!!

I see now my clock has changed - but I was looking at

"Applications" "Places" etc....

OK - now I need to figure out what I need to add to make this work. 

Thanks!

(Also can I change the color of the menus in my applications as well?)

---

### Post by jerrrys on 2009-06-25
[attach]119001[/attach]

---

### Post by robobart on 2009-06-26
I think what jerrys is (not) saying is that we should just customize the theme colors under

System => Pref => Appearance

etc.

This doesn't work. Depending on the theme, the text color for the panel and other applications seems to be somehow fixed.

Oddly enough one can always change the background of a panel - but not the foreground - by right clicking on the panel and selecting "properties." 


I would much rather change these things with a GUI rather than messing with the .gtkrc-2.0

---

### Post by fooman on 2009-06-26
i used the following guide to change the color of my panel/main menu fonts:

[http://ubuntuforums.org/showthread.php?t=334570](http://ubuntuforums.org/showthread.php?t=334570)

its outdated...but it works just fine in jaunty 64.  :)

---

