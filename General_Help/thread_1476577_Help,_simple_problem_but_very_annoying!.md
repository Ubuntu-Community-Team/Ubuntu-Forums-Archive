---
title: "Help, simple problem but very annoying!"
date: 2010-05-08
forum: General Help
---

### Post by pcox on 2010-05-08
I just deleted the top panel bar with applications system preferences ect...

How do I get it back hahaha (Im serious though)

Also I added blank panels to the bottom and right hand side of screen which I do not want, how do I delete them.

Sorry for the noob response, just got back into ubuntu (latest one 10.whatever)and absolute love it, im going to uninstall win7 very soon :) (have a dual set-up now)

but yes please help, I can get to my terminal thanks to docky :)

---

### Post by TheNerdAL on 2010-05-08
Right click, add to panels and search for it right there. Sorry, I forgot what it's called.

---

### Post by pcox on 2010-05-08
thats not working sorry, im not quite sure what you mean also.

---

### Post by TheNerdAL on 2010-05-08
> **pcox said:**
> thats not working sorry, im not quite sure what you mean also.

Try this: [http://ubuntuforums.org/showthread.php?t=415570](http://ubuntuforums.org/showthread.php?t=415570)

Edit: Try what the second poster said.

---

### Post by WorMzy on 2010-05-08
To get rid of the unwanted panels, right-click on them and choose "Delete this panel".

To get your top panel back, click your bottom panel and select "New Panel".

Then right-click on the new panel and, if necessary, click properties and change the orientation to "Top".

Then right-click on the panel and click "Add to panel...", search for "Menu Bar" and drag the item onto the left of the panel.

On the right of the panel, drag "Indicator Applet Session", "Indicator Applet", "Notification Area" and "Clock". Then close the "Add to panel" window.

To get back the Firefox icon, on the main menu, click Applications -> Internet, and right click on Firefox. Click "Add this launcher to panel".

To rearrange items, hold down middle mouse button on one of them, and drag it to where you want it to be.

To lock an item, right-click it, and choose "Lock".

---

### Post by pcox on 2010-05-08
The problem im having is that the panals dont actually show up...

like this, the chrome browser is maxed out yet wont allow me to click on them.

see?

[IMG]http://imgur.com/V7B2X.png[/IMG]

---

### Post by TheNerdAL on 2010-05-08
Ah, okay. Try this link: [http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

---

### Post by WorMzy on 2010-05-08
That image suggests to me that gnome-panel has crashed. You may need to restart.

---

### Post by pcox on 2010-05-08
> **TheNerdAL said:**
> Ah, okay. Try this link: [http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

It helped a little but I do not think it is compatible with the latest version of ubuntu, it got rid of the panels on the right and bottom but did not add the main top one with application and preferences...

---

### Post by pcox on 2010-05-08
the only reason im not restarting is because im watching breaking bad and its just so good haha.

---

### Post by WorMzy on 2010-05-08
Never seen it, so I couldn't comment. :)

Try using that terminal shortcut you just made to run 'gnome-panel', do you get an error message, or do the panels reappear?

---

### Post by lidex on 2010-05-08
In a terminal="Applications->Accessories->Terminal"
```
gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by nikefalcon on 2010-05-08
Try the link that ¨TheNerdAL¨ has provided. I worked for me(long time ago, in Jaunty)

---

### Post by frenziedfemale on 2010-05-08
If I understand your problem correctly, you have one panel but you want to add the top panel back? You can right click on the panel you have available and click add panel .. yep I got the it doesn't show up .. happened to me too ... but after I clicked it I rebooted my laptop and low and behold the new panel was there .. actually .. a few new panels because I  clicked add panel more than once in frustration!!  then just remove the extra panels you may have and follow the advice already given to get it set up the way you like it. Hope it works for you!

---

### Post by Dayofswords on 2010-05-08
you can reset the panels by deleting the ~/.gconf/apps/panel folder
logout
login
should be normal and defualt as how it was when you installed (the things you installed will still be in the list)

---

### Post by binamenator on 2010-05-08
You have 10.04 the newest version right?
I do so I think I can help you.
On the screen shot you posted, there were blank parts on the right and the bottom. Those are where the panels are supposed to be. For some reason it doesn't load. When I downloaded 10.04, there were panels both on right left, and top. But the left and right panels did not load until I restarted my computer.
I think you need to shutdown your computer then reopen it. The panels should be there by then. Then just right click on the panel an click New Panel. If nothing happens, then I think you should change the orientation to top.

---

