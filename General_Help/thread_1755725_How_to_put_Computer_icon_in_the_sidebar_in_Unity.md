---
title: "How to put Computer icon in the sidebar in Unity?"
date: 2011-05-11
forum: General Help
---

### Post by zia.newversion on 2011-05-11
I see many people are a little uneasy with the new desktop of Ubuntu. I think it's marvelous, though... Not because of a reason other than just that a change after a short while is always good.

So, in the Gnome desktop, I would go to gconf-editor and set some keys and I'd get my computer folder and home folder shortcut on my desktop.

This time since the unity desktop has come with a nice sidebar, I'd like to put the same icon there, in the sidebar. But I can't even access computer as Computer:/// anymore... What to do?

---

### Post by anaconda on 2011-05-11
open terminal and type:
```
nautilus --no-desktop computer:
```
and then just right click it on the unity panel, and select the "keep in panel"

Atleast it works on my machine, but I have started the "gnome-panel" even while I am in unity... Keeps it more familiar.

---

### Post by zia.newversion on 2011-05-12
Too bad it doesn't appear in the Unity panel!
It just gets merged with the "Home" icon already on top in the Unity Panel...

And I thought about keeping the gnome-panel as well. But there is a dilemma. I don't want it on the Unity desktop, only in the Ubuntu Classic (Gnome) desktop. And I am pretty sure if I install and enable it in the Classic desktop, next time when I log into the Unity desktop, it'll be there, too. :(

---

### Post by zia.newversion on 2011-05-19
Still not solved.

---

### Post by mc4man on 2011-05-19
This would be best done thru a quicklist entry on yout home folder (right click on icon > chosse

The basic idea is shown here
[http://askubuntu.com/questions/35024/how-to-add-my-favorite-places-as-a-quicklist-in-my-homes-icon-in-unity](http://askubuntu.com/questions/35024/how-to-add-my-favorite-places-as-a-quicklist-in-my-homes-icon-in-unity)

Shortly there will be a gui tool available (ppa), it will edit or create new launchers with whatever quicklists you want - see screen

If you wish to do now and not clear then post back with what locations you wish in the quicklist other than Computer (if any), will give you a .desktop example to use.
(once one gets the idea this is quite simple to do - whether adding to existing icons(.desktops) or creating new ones 

(The quicklist entry for this would be - 
```
[Computer Shortcut Group]
Name=Computer
Exec=nautilus --no-desktop computer:///
TargetEnvironment=Unity
```

---

### Post by zia.newversion on 2011-05-19
Thanks a lot. I guess this problem is solved now. That almost answers it satisfactorily... Will be waiting anxiously for the GUI tool, though. :)

---

