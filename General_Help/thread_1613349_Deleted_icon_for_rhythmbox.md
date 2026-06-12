---
title: "Deleted icon for rhythmbox"
date: 2010-11-04
forum: General Help
---

### Post by ihavenoidea on 2010-11-04
I accidentally deleted the icon for rhythmbox on the menu bar thing at the top of my screen and now rhythmbox wont open. How do i get this back, ive tried reinstalling rhythmbox.

---

### Post by wojox on 2010-11-04
When you reinstall an app, you have to go into your /home directory and delete the config files. Do a search in /home and remove everything rhythmbox.

---

### Post by Enigmapond on 2010-11-04
Applications/Sound & Video and right-click on Rhythmbox and add launcher to panel...

---

### Post by korn101 on 2010-11-04
If I understand the question right:

Right Click the menu, click "Edit Menus"

It should open up a little dialog. On the right will be the list of menu items, Go down to "Sound & Video", then tick the box next to Rhythm Box. If it is ticked, then Un-tick it. Close, then repeat the previous, and tick it again.

Should work, (if i understood the question 100%)

If else, then just describe it a little better.

Hope I helped :)

---

### Post by wojox on 2010-11-04
> **Enigmapond said:**
> Applications/Sound & Video and right-click on Rhythmbox and add launcher to panel...

Even better. :)

---

### Post by ihavenoidea on 2010-11-04
Im not trying to add a launcher to the panel, or the menu, they are both there. when i click on these launchers nothing happens, i think because i deleted the icon to the right of the panel, how do i get this icon back. I also cant figure out how to search and i dont see any config files in my home directory.

---

### Post by korn101 on 2010-11-05
I'm still not completely understanding...

But if you need the directory of the executable, it's usually in the /usr/bin folder.

Just hit Ctrl+H to show hidden files, and you should see it there as "rhythmbox"

Good Luck,
Jaime.

---

### Post by ihavenoidea on 2010-11-05
Nope I do not need the executable, that works, its just when i click on the executable nothing happens. actually if i restart then i can open rhythmbox, but if i close it i cant open it again. And when i shut down it says rhythmbox is not responding. And i know how to see hidden files but rhtyhmbox just isnt anywhere. Perhaps those files are what i deleted?

---

### Post by thinkpol on 2010-11-06
I have the exact same problem.  I'm pretty sure it's because I deleted the top panel and tried to move its contents to the bottom panel.  I thought it was the "Notification Area" that would add it back but it's not.  I've tried just about everything.

---

### Post by Frogs Hair on 2010-11-06
Rythmbox shows up under indicator applet from the add to panel menu.

---

### Post by ki4jgt on 2010-11-06
The best way would've been to reset gnome by going to home folder
showing hidden files and deleting .gconf .gconfd .gnome2 and .gnome2_private. That's what I always do when I mess up the desktop. Although now that you have delete the application itself, I don't know if it will work.

---

### Post by ki4jgt on 2010-11-06
This will reset every thing gnome has desktop background, the bars, the wifi passwords and your empathy accounts. It will be as though you have installed the desktop from fresh. Your apps will all still be on your computer, but anything to do with the background or the two bars will be reset.

---

### Post by thinkpol on 2010-11-06
Thanks Frogs Hair.  That fixed it for me.  I had it all along but didn't realize it was the speaker icon.  I thought that was just a volume control.

---

