---
title: "How to enable icons in System menu in Ubuntu 10.04?"
date: 2010-05-01
forum: General Help
---

### Post by abcuser on 2010-05-01
Hi,
in Ubuntu 9.10 this settings is in System | Preferences | Appearance, but where is it in Ubuntu 10.04?
Thanks

---

### Post by inameiname on 2010-05-01
To add menu icons, which was left out as an easy option in Lucid:

Just type gconf-editor into the Alt+F2 run dialog to open the Gnome Configuration Editor.
Now browse down to the following key:
desktop \ gnome \ interface \ menus have icons   
And check 'menus have icons'.


If want....which I use....

To add text below icons, which was left out as an easy option in Lucid:

Just type gconf-editor into the Alt+F2 run dialog to open the Gnome Configuration Editor.
Now browse down to the following key:
desktop \ gnome \ interface \ toolbar_style \ both   
On the bottom, you&#8217;ll see the different options, and choose 'both'.

---

### Post by abcuser on 2010-05-01
Hi,
thanks for tips, especially "text below icons"!

BTW, I have found found first setting in Ubuntu Tweak.
Thanks

---

### Post by inameiname on 2010-05-03
No problem. Yeah, Ubuntu Tweak is great for that.

---

### Post by SlaughterDog on 2010-05-05
I'm just curious, does anybody know why they first disabled them by default, and then removed the easy way to change it from the appearances tab?

Personally, I like both the icons in the menus and on the buttons (which I now know where to re-enable those as well). Makes it a lot easier to see what's what.

---

### Post by inameiname on 2010-05-06
I think they just thought it was too cluttered having both. Though, from reading a lot of Ubuntu users' responses, most look at icons over text and really don't like the change.

And I have no idea why the option to restore them and/or change them like you could in the Appearance section was removed.

---

### Post by filip007 on 2010-05-11
Is there a direct command...?

This is for Fedora only.
gconftool-2 &#8212;type boolean &#8212;set /desktop/gnome/interface/menus_have_icons true

or this

gconftool-2 --type boolean --set /desktop/gnome/interface/menus_have_icons true

Both they don't do anything.

This just open... 
gconf-editor /desktop/gnome/interface/menus_have_icons true

---

### Post by inameiname on 2010-05-11
gconftool-2 --set /desktop/gnome/interface/menus_have_icons --type bool true

gconftool-2 --set /desktop/gnome/interface/toolbar_style --type string "both"


....and if you want buttons to have icons too....

gconftool-2 --set /desktop/gnome/interface/buttons_have_icons --type bool true

---

### Post by Yaroslav_L on 2010-06-29
Can anybody help with Gimp? Can't find where to turn on icons showing in Gimp's menu. Now I have only text.
For example: Colours>Brightness-Contrast - there are no icons near the text.
Thanks.


> **inameiname said:**
> To add menu icons, which was left out as an easy option in Lucid:

Just type gconf-editor into the Alt+F2 run dialog to open the Gnome Configuration Editor.
Now browse down to the following key:
desktop \ gnome \ interface \ menus have icons   
And check 'menus have icons'.


If want....which I use....

To add text below icons, which was left out as an easy option in Lucid:

Just type gconf-editor into the Alt+F2 run dialog to open the Gnome Configuration Editor.
Now browse down to the following key:
desktop \ gnome \ interface \ toolbar_style \ both   
On the bottom, you’ll see the different options, and choose 'both'.

---

