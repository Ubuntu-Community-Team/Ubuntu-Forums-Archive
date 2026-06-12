---
title: "Can't find installed program"
date: 2010-12-22
forum: General Help
---

### Post by pstrbrc on 2010-12-22
Toshiba Satellite laptop, Ubuntu 10.04lts
I installed qcad earlier today, using Software Center. Qcad didn't show up anywhere in the Applications dropdown menu. When I was running 9.04, it showed up in the Graphics sub-menu, but it's nowhere. Rebooted, nothing. It shows up as installed in the Synaptic Package Manager, but I went ahead and removed and installed it again, rebooting between each operation. (sigh) Still nothing. Now, I'm sure it's in here, but I can't find it. So, I have three questions:
1. How do I start it (or any program) using command line?
2. How do I find it using my Gnome gui, and put it in the applications menu
and
3. Generally, is there a guide that will explain what I'm looking at when I open my File System directory? 
[IMG]http://i129.photobucket.com/albums/p232/pstrbrc/filesys.jpg?t=1293076700[/IMG]

---

### Post by Quackers on 2010-12-22
In that file you have open, open usr then opn bin. Is qcad in there?

---

### Post by pstrbrc on 2010-12-22
Ah, good man you are! Yep, thar's a diamond shaped icon wit' little gears on it named qcad, and when I double-click it, up opens qcad! 
OK, how do I get it to the dropdown Application menu?

---

### Post by Quackers on 2010-12-22
Not sure :-)
But you can right-click on the Desktop and select "create launcher" and then enter the details and browse to the diamond file and you should then have a usable launcher. 
Maybe somebody else could offer you something better.

---

### Post by Quackers on 2010-12-22
Dodgy "submit post" error - please disregard.

---

### Post by Don Barzini on 2010-12-22
> **pstrbrc said:**
> OK, how do I get it to the dropdown Application menu?

It might be somewhere in the menu.... but possibly hidden.

Check... System > Preferences > Main Menu

Sometimes installed apps have their menu icons unchecked.

It's worth a try to look.

---

### Post by SbKhaan1 on 2010-12-23
> **pstrbrc said:**
> Ah, good man you are! Yep, thar's a diamond shaped icon wit' little gears on it named qcad, and when I double-click it, up opens qcad! 
OK, how do I get it to the dropdown Application menu?

Easy.

Right click applications>edit menu>new item>

Type in the name, click "Browse" and point it to the thing you double-clicked, add a comment if you want.

---

### Post by Quackers on 2010-12-23
> **SbKhaan1 said:**
> Easy.

Right click applications>edit menu>new item>

Type in the name, click "Browse" and point it to the thing you double-clicked, add a comment if you want.

Excellent :-) Thanks!

---

### Post by pstrbrc on 2010-12-23
> **SbKhaan1 said:**
> Easy.

Right click applications>edit menu>new item>

Type in the name, click "Browse" and point it to the thing you double-clicked, add a comment if you want.

Not in my desktop environ. Here's what worked for me:

system/preferences/main menu

This is what my window looked like
[IMG]http://i129.photobucket.com/albums/p232/pstrbrc/Mainmenu.jpg?t=1293116288[/IMG]

click on the submenu where you want the shortcut, then click New Item. Then browse the filesys/usr/bin folder, find the qcad exe, name it "qcad" (or "spot", or George", or whatever...) and there it is!!!!

---

