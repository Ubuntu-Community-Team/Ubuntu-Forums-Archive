---
title: "Missing Firefox icons"
date: 2009-07-08
forum: General Help
---

### Post by sirjoebob on 2009-07-08
I recently upgraded to firefox 3.5 via instructions at Mozilla's website. Only issue is that now my system won't display icons on any firefox shortcut I create. This includes gnome-do. I tried switching icon themes and no luck there. Is there any way I can force it to read the right icon for my firefox launcher?

---

### Post by NilsE on 2009-07-08
Creating a launcher does not automatically pick up the icon.  You need to edit the launcher and where you see the wrong icon on the top left click on it and find the icon you want.

---

### Post by brookie on 2009-07-08
I hope this won't happen when they put FF 3.5 in the repos. ? :()

---

### Post by pmlxuser on 2009-07-08
go to the menu editor

-> System -> Preferences -> Main Menu

-> Internet -> Firefox -> Properties -> click on the Blank Icon


you can browse and change it regards....

---

### Post by sirjoebob on 2009-07-08
> **pmlxuser said:**
> go to the menu editor

-> System -> Preferences -> Main Menu

-> Internet -> Firefox -> Properties -> click on the Blank Icon


you can browse and change it regards....

That's what I don't get, it is fine there. If I place it on my gnome-do dock, it still does not show it up. 

Also, it will not happen when Ubuntu updates as they will make sure this kind of thing is taken care of.

---

### Post by scouser73 on 2009-07-08
> **sirjoebob said:**
> I recently upgraded to firefox 3.5 via instructions at Mozilla's website. Only issue is that now my system won't display icons on any firefox shortcut I create. This includes gnome-do. I tried switching icon themes and no luck there. Is there any way I can force it to read the right icon for my firefox launcher?

Place your cursor over the Ubuntu Button, **Right Click**, select **Edit Menus**, select **Internet**, **Firefox**, **Properties**, click the small picture box in **Launcher Properties** and then browse to **/home/YOURNAME/firefox/icons/mozicon128.png**

[[IMG]http://img262.imageshack.us/img262/3830/screenshotujl.th.png[/IMG]](http://img262.imageshack.us/i/screenshotujl.png/)

---

### Post by sirjoebob on 2009-07-08
I have removed previous version of FF from my system and I do not have a ~/firefox directory. besides, I have pointed the menu shortcut to my usr/share/icons/hydroxygen firefox icon and it shows up fine in the menu but won't on the desktop or gnome-do.

---

### Post by budde on 2009-11-15
got the same issue.

did you solve it?

---

### Post by felixq78 on 2010-05-04
I just upgraded to Ubuntu 10.04 and I found the same issue, just a generic icon appeared.

---

### Post by paul-n on 2010-06-23
hi there

Scouser73 thanks for the tip to get the Icon back.

However I could only find it here :-

/usr/lib/firefox-3.6.3/icons

Not 
[B]/home/YOURNAME/firefox/icons/mozicon128.png

[/B]regards Paul

ps I am very much a noob [ 9.10 ], but am enjoying Ubuntu and the experience and will be converting some of my friends soon

---

### Post by prog101 on 2010-07-06
1. Remove icon from panel.
2. Right click on panel and click on Add to Panel
3. Click on Application Launcher
4. Click Internet
5. Click on Firefox
6. Firefox launcher should be added to panel with the right icon image.

---

