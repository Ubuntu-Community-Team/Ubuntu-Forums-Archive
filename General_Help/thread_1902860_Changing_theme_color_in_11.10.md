---
title: "Changing theme color in 11.10"
date: 2012-01-01
forum: General Help
---

### Post by as2000 on 2012-01-01
I like unity. But I cannot seem to find a way to get rid of that orange color anywhere. I like blue and thats all. I have found a way to reduce the size of the launcher which really helped out a lot. I am not a big theme guy and just need blue instead of orange to please my eyes. Heck, I would even stand for Aubergine!

---

### Post by syerges on 2012-01-01
from your dash home type 'appearance'
there is the word theme at the bottom and some choices on the right. as well as the background changes in the middle.

---

### Post by yugnip on 2012-01-01
I think you might like the [Ambiance Blue]("http://satya164.deviantart.com/art/Ambiance-Blue-Theme-Suite-196833665") theme. It stays pretty close to Ambiance, but makes it blue rather than orange.

---

### Post by as2000 on 2012-01-01
Found a solution so I will share;

Code: sudo apt-get install dconf-tools

Path: org => gnome => desktop => interface
Find the line “gtk-color-scheme” and add this string:
bg_color:#f0f1f2;selected_bg_color:#023C88

Did not want to add the link, but I found this from Ask Ubuntu. dconf-tools locked up the system after I installed and edited the above said location, but after restart (and changing the bg_color hex) I have what I am looking for.

---

### Post by as2000 on 2012-01-01
> **yugnip said:**
> I think you might like the [Ambiance Blue]("http://satya164.deviantart.com/art/Ambiance-Blue-Theme-Suite-196833665") theme. It stays pretty close to Ambiance, but makes it blue rather than orange.


That was a good tip. However, when I followed the link I had to create a .themes folder. Not a big deal, but still got more choice!

---

