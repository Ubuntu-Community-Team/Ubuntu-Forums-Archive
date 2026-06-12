---
title: "Remove all panels, only have docky?"
date: 2010-10-29
forum: General Help
---

### Post by JavaNut13 on 2010-10-29
I have just installed Docky, its very slick and useful.

I have my dock, and thats all I want, but (thats the problem) Ubuntu want let me delete all my normal Ubuntu panel.

I think you can see my problem, but just in case: I want to remove all my Ubuntu panels.

Churs,

Will. (Ubuntu 10.04, Acer Aspire One)

---

### Post by marin123 on 2010-10-29
i suggest you leave the panel, just minimize it and turn on autohide and put it in top right corner... i did that and it was very useful... if you delete the last panel, you will lose alt+f2 function...
in case youre sure of deleting, go open gconf-editor and unlock the panel so you can delete it... im in windows right now so i dont know the right path...
i think gnome, panels, something like that...

---

### Post by kerry_s on 2010-10-29
gconf-editor, desktop-> session-> required_components

double click "gnome-panel" & put "docky"

log out & back in

---

### Post by JavaNut13 on 2010-10-29
Aha!Sweet! For once something actually works well.

Just on the off-chance.. Can I add a notification area in there? something to show my Bluetooth+Wifi?

Will.

---

### Post by kerry_s on 2010-10-29
> **JavaNut13 said:**
> Aha!Sweet! For once something actually works well.

Just on the off-chance.. Can I add a notification area in there? something to show my Bluetooth+Wifi?

Will.

docky don't do that, dockys the most limited of docks. you can switch docky for "avant-window-navigator"(awn) which can fully replace gnome-panel, gives you more settings & runs lighter.
i recommend you use the ppa's to get the latest.
[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

---

