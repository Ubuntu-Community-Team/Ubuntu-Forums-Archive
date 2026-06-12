---
title: "Bar Buttons keep on dissapearing... :( :("
date: 2010-06-03
forum: General Help
---

### Post by elidoperezmd on 2010-06-03
Hi all...

The bar buttons for all my windows dissapeared, this has happened before and a restart will fix it. But seems that lately it has been happening with more frequency.

To be more clear there is no maximize/minimize and X buttons...to be even more clear the is no bar at all.

Check out the print screen that has no bar on the browser...

How can i solve this?

Thanks for the help/time/replies

---

### Post by elidoperezmd on 2010-06-03
please

---

### Post by elidoperezmd on 2010-06-03
please some help

---

### Post by elidoperezmd on 2010-06-03
just did it again...this time while on the session not starting a session as it ussed to happen..please help me

---

### Post by Captain Carrot on 2010-06-03
This seems to just happen. As far as I have been able to tell, there is no cure. Just logging off usually brings mine back though, I don't think you need to restart.

---

### Post by elidoperezmd on 2010-06-03
> **Captain Carrot said:**
> This seems to just happen. As far as I have been able to tell, there is no cure. Just logging off usually brings mine back though, I don't think you need to restart.

But is this a bug with a worj around? has this happened with others OS?

---

### Post by jerenept on 2010-06-03
Try opening a terminal (/usr/bin/gnome-terminal) and running the command ```
metacity 
```

---

### Post by elidoperezmd on 2010-06-03
> **jerenept said:**
> Try opening a terminal (/usr/bin/gnome-terminal) and running the command ```
metacity 
```

Nothing happened....


elidoperezmd@elidoperezmd:/usr/bin$ metacity
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

buttons still dont show

---

### Post by ks07 on 2010-06-03
Press Alt+F2 then type in the box and run: ```
metacity --replace
```.

If you want you can make a launcher on the desktop to fix this easy whenever it happens for whatever reason. Right click on your desktop, choose create launcher. In the boxes, fill in these details:
Type: Application
Name: Whatever you want to call it. E.g. 'Metacity' or 'Fix bar buttons' or ...
Command: metacity --replace
Leave comment blank, unless you want to write in it. 

Now, whenever it breaks, double clicking that launcher should fix the problem. :guitar:

---

### Post by elidoperezmd on 2010-06-03
> **ks07 said:**
> Press Alt+F2 then type in the box and run: ```
metacity --replace
```.

If you want you can make a launcher on the desktop to fix this easy whenever it happens for whatever reason. Right click on your desktop, choose create launcher. In the boxes, fill in these details:
Type: Application
Name: Whatever you want to call it. E.g. 'Metacity' or 'Fix bar buttons' or ...
Command: metacity --replace
Leave comment blank, unless you want to write in it. 

Now, whenever it breaks, double clicking that launcher should fix the problem. :guitar:


It solved the problem...And another came along... Thanks for the help i know how to kix this now...see the attached file, now the buttons are here. hot 1/4 of the screen is missing....
do you know the cause?

See attached file

---

### Post by elidoperezmd on 2010-06-03
sorry here it is

---

### Post by ks07 on 2010-06-03
I have no idea sorry, my best idea is just restarting the x server. (Easiest way is just a restart.) I'm off now, but I'll check back later and see if I can help anymore. Good luck :)

---

