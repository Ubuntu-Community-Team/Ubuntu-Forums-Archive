---
title: "Customising the Applications menu?"
date: 2011-02-21
forum: General Help
---

### Post by oxf on 2011-02-21
Is it possible to customise the entries in the pull down Applications menu?
Specifically I installed an application through Synaptic. Trouble it  installed several parts of the application which are all list in Applications>Sound and Video. I was wondering if I could create a new custom folder to reside either directly under Applications or a sub folder in Sound and Video.

Thanks

---

### Post by sisco311 on 2011-02-21
Yes you can use alacarte. Right click on the menu and select *Edit Menus* or run:```
alacarte
```

---

### Post by seawolf167 on 2011-02-21
Right click the Applications Menu, select Edit Menus

---

### Post by oxf on 2011-02-21
OK thanks..
That's simpler than I thought! 
How do I ensure an application is put into my custom folder when I install it from Synaptic?

---

### Post by seawolf167 on 2011-02-21
It'll be put where the developer decided to put it, you'll have to manually add any additional custom menu items (over and above the default) each time you install a new package

---

### Post by oxf on 2011-02-22
OK thanks for all the advice so far.
Uhm what am I doing wrong here? I can create a new menu or new item but it's not saved. When I close and go to Applications it's not there! I guess it's something basic that I've missed but I can't see it.

---

### Post by lykeion on 2011-02-22
Just make sure you tick the show box after creating new menu/item.

---

### Post by seawolf167 on 2011-02-22
It should automatically save any changes you make if you are using the editor correctly. You can try deleting the applications.menu item and then running alacarte (which will regen a new menu - hopefully uncorrupted)

```
cp ~/.config/menus/applications.menu ~/applications.menu.backup
rm ~/.config/menus/applications.menu
``````
alacarte
```

---

### Post by oxf on 2011-02-22
> **seawolf167 said:**
> It should automatically save any changes you make if you are using the editor correctly. You can try deleting the applications.menu item and then running alacarte (which will regen a new menu - hopefully uncorrupted)

```
cp ~/.config/menus/applications.menu ~/applications.menu.backup
rm ~/.config/menus/applications.menu
``````
alacarte
```

I don't know.. maybe there's something weird on my system.
I tried all that again including the steps above. I launch Alacarte and can create a new menu, check the box next to it to display it, but when I close the editor and pull down Applications it's not there!

---

### Post by oxf on 2011-02-23
OK does anyone have a clue why I can't save the customisation? Here's what I'm doing..

1. Open Alacarte
2. Click on Applications in the left menu to select the Applications menu
3. Select "New Menu" on upper right
4. Name that say "Misc" and click "OK"
 "Misc" now appears as a folder in the Applications menu.
5. I then check the box next to Misc under the "Show Items" column
6. Close Alacarte

"Misc" should now be visible when I pull down the Applications menu but it's not there! Maybe I'm doing something stupidly wrong, or not..

---

### Post by QLee on 2011-02-23
> **oxf said:**
> OK does anyone have a clue why I can't save the customisation? Here's what I'm doing..

1. Open Alacarte
2. Click on Applications in the left menu to select the Applications menu
3. Select "New Menu" on upper right
4. Name that say "Misc" and click "OK"
 "Misc" now appears as a folder in the Applications menu.
5. I then check the box next to Misc under the "Show Items" column
6. Close Alacarte

"Misc" should now be visible when I pull down the Applications menu but it's not there! Maybe I'm doing something stupidly wrong, or not..

Try adding an item (launcher for some program) to that new empty folder, Misc, that you have created, then see if it is displayed.

---

### Post by oxf on 2011-02-23
> **QLee said:**
> Try adding an item (launcher for some program) to that new empty folder, Misc, that you have created, then see if it is displayed.

OK.. yes it is :) That part resolved!

Thanks! and to everyone else who has contributed. Part of my problem is that I've never done this part before and the help menu is a bit lacking but I'm getting there.

So my next and hopefully final question is how do I move another program that is already installed into the Application menu into the said Misc folder?  In this case it seems to install by default into Sound And Video but I don't want it there.

I presume I have to click on New Item or something and then Browse to find it. But How do I find it? I could also click on it's properties where it installs by default and do I just copy/paste the "command"?

Thanks..

---

### Post by lykeion on 2011-02-24
> How do I move another program that is already installed into the Application menu into the said Misc folder? 
In Alacarte you can just select the item (to the right) and drag-and-drop it on your Misc folder (to the left).

---

### Post by oxf on 2011-02-24
> **lykeion said:**
> In Alacarte you can just select the item (to the right) and drag-and-drop it on your Misc folder (to the left).

Duuh I should have thought of that! Simple.
Thanks!

---

