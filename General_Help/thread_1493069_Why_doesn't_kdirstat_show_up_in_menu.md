---
title: "Why doesn't kdirstat show up in menu?"
date: 2010-05-25
forum: General Help
---

### Post by Andy F on 2010-05-25
Hi,

I've finally got around to installing Lucid, which I did as a fresh install. I installed *kdirstat* (which I prefer to *Baobab*) using [FONT=Courier New]apt-get install kdirstat[/FONT]. I'm fairly sure this is how I did it previously, and that it created a menu item automatically. This time no menu items (I did check it wasn't a disabled menu item via *right-click -> Edit Menus*). I looked to see if it was available in the Ubuntu Software Centre, and when I saw it was I uninstalled and reinstalled using that. Still no menu item. So a couple of Qs:

[LIST=1]
[*]Does it make a difference if you install using [FONT=Courier New]apt-get[/FONT] or the Software Centre?
[*]Is there a way for me to get the menu item now without manually adding it?
[/LIST]
Thanks all,

Andy

---

### Post by Rube T. on 2010-06-11
I had the same issue when I installed via the Software Center, although I, and you probably could too, run it by "Alt+F2" to get the Run box, then "kdirstat."

If you can run anything on the Run box, it's definitely in "/usr/bin." 

So head on to create a new menu item and insert "/usr/bin/kdirstat" to the Command box. Somehow it manages to add the icon automatically. If it doesn't, it's in "/usr/share/icons/hicolor/32x32/apps/kdirstat.png"

Hope that helps. Any idea why didn't it show up automatically? Does all KDE apps behave the same way when installed in Gnome?

---

### Post by Andy F on 2010-06-11
Yeah thanks, I know how to do it manually - but I'd be interested in knowing the answers to the two questions.

> Does all KDE apps behave the same way when installed in Gnome? 
No - I have okular, kdiff3, and knetwalk installed (using apt-get) and they all automatically showed up appropriately in the menu system.

Cheers,

Andy

---

