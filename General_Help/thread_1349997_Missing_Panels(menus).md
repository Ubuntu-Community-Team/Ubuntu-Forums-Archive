---
title: "Missing Panels(menus)"
date: 2009-12-08
forum: General Help
---

### Post by joes7 on 2009-12-08
[CENTER][SIZE=6]Recover your Missing Panels!
[SIZE=1]This was tested on Xubuntu, but it should work on any Ubuntu release[/SIZE]
[/SIZE][/CENTER]

Hello everybody.You might have encountered an annoying bug which caused the menus (or panels) to dissappear. Don't worry,  if you had this bug as I did, follow these simple steps :p.

**If you wish to host more than one user on your computer...**
[best way]
[U]Create a new User Account
[/U]Yes, it is indeed possible to launch programs and stuff without the panels. Go to your desktop, right click, select "Applications", select "System" and now select "Users and Groups". Now that we have reached this point, it is time to create a new account that will replace our buggy account. [COLOR=Magenta]Don't worry, your buggy homedrive won't be removed, hence you can access your old documents any time;).[/COLOR] Now, after creating the new account, log out of your "buggy account" and log onto the new one. Tada! All set. However, the problem remains the same on your old account, so I suggest that you delete it.
And if you wish to delete the deleted user's homedrive, you can type the following command:

*THIS ONLY WORKS IF THE USER HAS BEEN DELETED*
```

sudo rm -r /home/username

```[B]If you don't want to host more than one user...
[/B]Open a new terminal by using the same method as above when opening the menu. Type
```
 xfce4-panel
```This will let us see the menu. DO NOT CLOSE the terminal yet. Now, right click and select "Quit". Make sure to mark the option "save session". Now, reboot. Voila, problem solved.



_**ALTERNATE METHOD.**_by drenzle
[quote="drenzle"]
New user here; I've found that in Xubuntu Hardy 8.04, to enable the panel menus (after they disappear), double click the file system folder icon on the desktop, double click on 'usr', double click on 'bin', look for the 'panel' icon, double click on it and the menus (taskbar) will be restored. You may also right click on the icon and create a shortcut on the desktop (just in case). As an almost, former, windows user, this graphical, simplistic method may work for other new users as well. 

"Onward Through The Fog!"
[/quote]

---

### Post by lisati on 2009-12-08
When I was using Xubuntu on a laptop that I no longer have, an alternative that let me close the terminal was this:
```
xfce-panel &
```

---

### Post by joes7 on 2009-12-08
> **lisati said:**
> When I was using Xubuntu on a laptop that I no longer have, an alternative that let me close the terminal was this:
```
xfce-panel &
```
Yes:D, but as I said before, if you have multiple users once you log on to another one and log back into your account, the problem will persist. Deleting a buggy account would be the best, I believe. You can always use the LiveCD, but that takes time.

---

### Post by drenzle on 2009-12-17
New user here; For the point & click crowd, I've found that in Xubuntu Hardy 8.04, one may graphically enable the panel taskbar/menus by double clicking the file system folder icon on the desktop, double click on 'usr', double click on 'bin', look for the 'panel' icon, double click on it and the menus (taskbar) will be restored. You may also right click on the icon and create a shortcut on the desktop (just in case). However, using the terminal is easier. Hope this helps.

"Onward Through The Fog!"

---

### Post by joes7 on 2009-12-19
> **drenzle said:**
> New user here; I've found that in Xubuntu Hardy 8.04, to enable the panel menus (after they disappear), double click the file system folder icon on the desktop, double click on 'usr', double click on 'bin', look for the 'panel' icon, double click on it and the menus (taskbar) will be restored. You may also right click on the icon and create a shortcut on the desktop (just in case). As an almost, former, windows user, this graphical, simplistic method may work for other new users as well. 

"Onward Through The Fog!"

Or, as I said, opening a terminal and writing:
```

xfce4-panel

```
Thanks for your information, I will include it on my original post,giving credit to you, obviously.

---

