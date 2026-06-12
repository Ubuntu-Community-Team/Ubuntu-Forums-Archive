---
title: "Make Windows key open Applications Menu"
date: 2011-05-09
forum: General Help
---

### Post by jockopablo on 2011-05-09
Someone helped me do this with Lubuntu, but I've switched to Xubuntu and the procedure is obviously different.  How can I make my Windows key open the Applications Menu in Xubuntu?

I found the keyboard shortcuts in the Settings menu but I see no option for adding a shortcut.  It only shows the existing shortcuts.

Thanks.

---

### Post by TheNerdAL on 2011-05-09
I think this has your solution: [http://lgallardo.com/en/2009/07/18/accesos-rapidos-en-xfce-4keyboard-shortcuts-in-xfce-4/](http://lgallardo.com/en/2009/07/18/accesos-rapidos-en-xfce-4keyboard-shortcuts-in-xfce-4/)

---

### Post by Toz on 2011-05-09
Please note that the command ```
xfce4-popup-menu
``` no longer exists in xfce 4.8 (Natty). If you are running Natty, the command is now```
xfdesktop --menu
```

---

### Post by jockopablo on 2011-05-10
Thanks, guys, but I don't have the option to Add a shortcut.  I can see the list of application shortcuts and if I double-click one it opens up, but I can't edit or add.

I'm running Xubuntu 11.04.

---

### Post by Toz on 2011-05-10
Go to Settings->Settings Manager, Click on Keyboard then Application Shortcuts. Do you have "Add", "Remove" and "Reset To Defaults" buttons at the bottom?

Something like this:
[http://capturedbypenguins.files.wordpress.com/2010/11/applicationshortcuts.png](http://capturedbypenguins.files.wordpress.com/2010/11/applicationshortcuts.png)

---

### Post by zbeefy on 2012-07-21
That's what it's called:

xfce4-popup-applicationsmenu 

I leave it here as a reference to myself, and others who wish to assign it to a keyboard shortcut.


Thanks.

---

### Post by zbeefy on 2012-07-21
I just don't know how to make that thing toggle. So that when you press it again, the menu disappears. Maybe some wise head could share a command we could add? :)

---

### Post by wildmanne39 on 2012-07-21
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

