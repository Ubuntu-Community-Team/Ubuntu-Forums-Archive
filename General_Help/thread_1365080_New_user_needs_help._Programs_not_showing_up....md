---
title: "New user needs help. Programs not showing up..."
date: 2009-12-26
forum: General Help
---

### Post by Anonymous D on 2009-12-26
Hello all. Ive been using Ubuntu for about a month now, and I like it so far. But Im having a problem finding programs I install with the terminal. 
Like just now I went through the terminal, and sintalled Gnome partition editor, and went through everything, and its nowhere to be found. Ive installed numerous programs and I cant find any of them. They just dont show up anywhere except for in the add/remove programs window. 
So its there something Im just not doing  right?  
Thanks guys.

---

### Post by Dayofswords on 2009-12-26
are you doing *apt-get install* way or the manual compiling and stuff?

---

### Post by Anonymous D on 2009-12-26
Im using the apt-get install method.

---

### Post by howefield on 2009-12-26
> **Anonymous D said:**
> Like just now I went through the terminal, and sintalled Gnome partition editor, and went through everything, and its nowhere to be found.

If it is GParted you installed, it should be found in System > Administration > GParted, if not there try logging out and back in.

If that still doesn't show the application in the menu, try opening from terminal (Applications > Accessories > Terminal) by typing

```
gksudo gparted
```

If you get an error, post back here.

---

### Post by Anonymous D on 2009-12-26
It wasnt in the menus anywhere, even after logging out, but going through the terminal opened it. But is there anyway I could get them to show up in the regular menus? That seems like a major PITA to have to remember a command for every program I want to use.

---

### Post by taurus on 2009-12-26
I believe it's called Gnome Partition Editor in System -> Administration.  It's not gparted in the menu.

---

### Post by Anonymous D on 2009-12-26
Its showing up now, but I still have all those other programs Ive DLed and have never been able to find.

---

### Post by taurus on 2009-12-26
Wanna share a few names of those apps?  Not every program has an icon in the menu.

---

### Post by howefield on 2009-12-26
> **taurus said:**
> I believe it's called Gnome Partition Editor in System -> Administration.  It's not gparted in the menu.

If I remember correctly it was, until Karmic, it now shows up as GParted. At least on my system.

---

### Post by Anonymous D on 2009-12-26
Brasero Disc Burner is the main one that I would like to be able to use. I see it listed in the Add/Remove list. Besides that, I beleive its mainly just little games I went to add that never showed up. Probably a media player and .gif viewer too, but I dont remeber the names of those.

---

### Post by Anonymous D on 2009-12-26
> **howefield said:**
> If I remember correctly it was, until Karmic, it now shows up as GParted. At least on my system.


Shows up as Partition Editor on mine.

---

### Post by taurus on 2009-12-26
For Brasero Disc Burner, look in Applications -> Sound & Video.  I thought it installed as a default with Gnome (at least on my machine because I've never installed it by hand).

---

### Post by Anonymous D on 2009-12-26
> **taurus said:**
> For Brasero Disc Burner, look in Applications -> Sound & Video.  I thought it installed as a default with Gnome (at least on my machine because I've never installed it by hand).


Thanks. I think clicking them in add/remove is making them show up or something, it wasnt there before, but its there now. 

You guys have any recommendations for programs for burning DVDs and CDs that may be better than Brasero?

EDIT: That might actually be the one that was installed by default. I remember trying to install something else but couldnt find it. Cant remember the name.

---

### Post by taurus on 2009-12-26
I use k3b mostly for my burning.  Even thought it's KDE app but it should run just fine in Gnome environment.

---

### Post by Anonymous D on 2009-12-26
How would I go about installing that?

---

### Post by taurus on 2009-12-26
```
sudo apt-get update
sudo apt-get install k3b
```
Or look for k3b in System -> Administration -> Synaptic.

---

### Post by Anonymous D on 2009-12-26
> **taurus said:**
> ```
sudo apt-get update
sudo apt-get install k3b
```Or look for k3b in System -> Administration -> Synaptic.
Thanks. Its showing up in the menu too BTW. 

Thanks guys.

---

### Post by 3rdalbum on 2009-12-26
If a program is command-line only, or if it's a daemon (for instance, some sort of server software), it won't be in the menu. You can find out how to run it by using the screencast I linked to in my signature.

---

