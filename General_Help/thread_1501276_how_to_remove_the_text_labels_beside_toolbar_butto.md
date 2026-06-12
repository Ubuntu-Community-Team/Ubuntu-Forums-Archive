---
title: "how to remove the text labels beside toolbar buttons?"
date: 2010-06-04
forum: General Help
---

### Post by fwoncn on 2010-06-04
This problem has been bothering me for quite a while. Here is how my  nautilus toolbar looks like:
[IMG]http://imgur.com/WI8UT.png[/IMG]
As you can see, only Back and Forward buttons are labeled. I hope I can  remove these labels to save my screen estate, but I can't find any  possible option in Edit -> Preferences after careful review.:(

---

### Post by inameiname on 2010-06-04
I believe this will work for you:

In the terminal, write:

gconftool-2 --set /desktop/gnome/interface/toolbar_style --type string "icons"

However, I prefer to have the text below, as with:

gconftool-2 --set /desktop/gnome/interface/toolbar_style --type string "both"

---

### Post by fwoncn on 2010-06-04
Yes:) What a magician you are!

---

### Post by inameiname on 2010-06-04
No prob. Took me a second actually to remember as I use nautilus-elementary (as it's just an updated nautilus which blows normal nautilus out of the water HEHE) and it automatically removes the text from the icons in it, yet for programs like gedit, I still have the text below the icons just as I want.

---

### Post by uid313 on 2012-03-20
Since GNOME 3 it changed.


```
gsettings set org.gnome.desktop.interface toolbar-style 'icons'
```

---

