---
title: "remove from open with list"
date: 2010-09-09
forum: General Help
---

### Post by Gavrail on 2010-09-09
Hi ):P And sorry for My English, it's not very god. 

That is my problem:

First i use Ubuntu 10.04 LTS with Gnome.

Wen i select file and pres right mouse button on it an select Ubuntu 10.04 LTS "Open with other Application" I see very long list and some Application their don't work.
 How i delete them?

---

### Post by Zill on 2010-09-09
Gavrail:

1)  Right-click on your file and select "Properties".
2)  Select the "Open With" tab.
3)  Click on the application you wish to remove.
4)  Click on the "Remove" button at the bottom.
5)  Repeat for all other unwanted applications.
6)  Close "Properties" window.

Note that this will change the "Open With" options for *all* files of the selected file type.

---

### Post by Gavrail on 2010-09-09
Oh no, you don't understand me

Remove from here [[IMG]http://img818.imageshack.us/img818/2361/screenshotae.png[/IMG]](http://img818.imageshack.us/i/screenshotae.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by Zill on 2010-09-09
Gavrail:  I believe the "Open with other Application" listing shows all installed applications.  I am not certain but I guess that if an application is uninstalled it will automatically be removed from this listing.

When you select the "Open With" right-click menu, you should see a subset of the available applications.  This menu can be edited to include and/or exclude whichever applications you wish.  Editing of this menu is done via the file Properties as detailed earlier where applications can be easily added or removed.

---

### Post by mc4man on 2010-09-09
you probably have wine 1.2 which has all these unimplemented or paritially implemented wine-extension.desktops (don't really get what it's all about, maybe something about integrating wine apps into gnome or similar.

Anyway I've found very little use for them here.
If you delete them it's hard to recover them later if somehow useful so for now I just move them to a save folder in Documents 

Look in ~/.local/share/applications - scroll to bottom area

Screen shows what I'm referring to.
After removing then reboot and the wine related one's will be gone.

---

### Post by Gavrail on 2010-09-09
Applications are removed 10 days ago. but they are just in list.

**mc4man** is right. Thanks man :) . It's work :guitar:

---

