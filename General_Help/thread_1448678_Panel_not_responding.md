---
title: "Panel not responding"
date: 2010-04-06
forum: General Help
---

### Post by Organicpete on 2010-04-06
Hi Guys,
First attempt at ubuntu was looking great until the panels went grey and reported 'panels not responding'
I read it may be due to weather applet .
Read I should open a terminal using Ctrl-Alt-F1 and type $ killall gnome-panel.
No idea what a terminal is but I get what looks like a dos screen asking for username and password.
When I type password nothing appears so I get no further.

I can still load ubuntu and get a right click box but no idea after that.
Any clues please ?
thanks
Pete

I should add that the desktop looks great and I love the way the panels are user configurable :)

---

### Post by wojox on 2010-04-06
Go to Places > Home Folder.
Press Ctrl+H to show hidden files.
Look for .gconf and right click and rename .gconfOriginal.
Log out and back in.

---

### Post by Organicpete on 2010-04-06
Thanks wojox I'll give it a go !
Pete

---

### Post by Organicpete on 2010-04-06
No joy there, I don't think I am going to the right place :(

I get to the desktop with its grey panel...
Only thing I can do is right click and get box.
Choose create launcher and there is browse button.
Choose that and found Places then Home.
But that just opens the folders in it.
How do I do Ctrl H ?

thanks 
Pete

---

### Post by Organicpete on 2010-04-07
ok got to a file window called "choose a file"
Found .gconf . in right panel . right click only brings up 'show hidden folders' and 'show size' 
Found I could drag .gconf to the left panel 'places' where I can rename it.

name in right panel stays the same.

can only cancel or enter.

No sign of 'logout'...
reboot and no change.

desktop is just the background with grey panel.

Maybe I should uninstall system and reinstall?
sigh
thanks
Pete

---

### Post by Organicpete on 2010-04-07
Trying a re-install :D

Pete

---

### Post by Organicpete on 2010-04-07
> **Organicpete said:**
> Trying a re-install :D

Pete

Well that worked :)
3 strikes... 1 down
Pete

---

### Post by gadolinio on 2010-04-07
> **Organicpete said:**
> Hi Guys,
First attempt at ubuntu was looking great until the panels went grey and reported 'panels not responding'
I read it may be due to weather applet .
Read I should open a terminal using Ctrl-Alt-F1 and type $ killall gnome-panel.
No idea what a terminal is but I get what looks like a dos screen asking for username and password.
When I type password nothing appears so I get no further.

I can still load ubuntu and get a right click box but no idea after that.
Any clues please ?
thanks
Pete

I should add that the desktop looks great and I love the way the panels are user configurable :)

That DOS-like program is the terminal. When it asks you for your password, it doesn't show anything while you type. But it does recieve your input. You just type normally and then press enter; it will take your password and go on.

---

### Post by Organicpete on 2010-04-07
Ah local knowledge !
Thanks very much :)
Pete

---

### Post by Organicpete on 2010-04-07
While we are at it, any idea how I can get the panel to show the firefox pages open.
When I minimize a page, no further trace of it is seen :)
thanks!
Pete

---

### Post by Talys on 2010-04-07
Make sure the window list is added to your panel.  Right click on the panel and select "Add to Panel...".  Scroll down to the bottom of the dialog, click on "Window List", and click the "Add" button.

---

### Post by Organicpete on 2010-04-07
Never mind I found it thanks :)
[http://ubuntuforums.org/showthread.php?t=1126936](http://ubuntuforums.org/showthread.php?t=1126936)

Pete

---

