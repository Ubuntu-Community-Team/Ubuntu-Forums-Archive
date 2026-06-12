---
title: "KMix Problem, Volume down but no Volume up???"
date: 2006-06-17
forum: General Help
---

### Post by adie273 on 2006-06-17
Hey, i searched on the forums, and with no luck, I use ubuntu and installed KDE, Kmix can do all the usual stuff fine when using the multimedia keys on my keyboard, volume down, mute etc. EXCEPT for some reason doesn't work with volume up. and only volume up.

Anyone happen to have any idea's how to solve this?

Done xev, found the key number etc, checked keyboard shortcuts, and global shortcuts and what not. still no idea myself how to sort this problem.

Any help would be greatly appreciated.

Adie

---

### Post by LordRaiden on 2006-06-17
Go to KMix >>> Settings >>> Configure Shortcuts ... (not Configure Global Shortcuts) then put your settings there. The more thorough way would be to do it through xmodmap. Can't remember how to that off the top of my head though. 

try [HTML]http://doc.gwos.org/index.php/MultimediaKeys[/HTML].

Ignore any of the stuff about gnome-bindings since you are a KDE user. Look at the xmodmap recipe and use that.

---

