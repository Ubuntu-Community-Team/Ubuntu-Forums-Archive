---
title: "No panels!!!"
date: 2010-04-01
forum: General Help
---

### Post by Sugoi48 on 2010-04-01
I was moving a third auto-hidding panel with a few buttons to the top of my screen and my panels all froze! I lost the third panel and the other two stopped responding. No other part was directly effected, but after rebooting I got a horizontally split screen loaded with green interference patterns and no panels. Reboot again and I only have grey space where the two panels should be. How do I fix this, beyond backing-up and reinstalling? THANK YOU!

---

### Post by MooPi on 2010-04-01
Let's try Alt +F2 and 
```
gconftool --recursive-unset /apps/panel
```then
```
rm -rf ~/.gconf/apps/panel
```finally
```
pkill gnome-panel
```reboot

---

### Post by Sugoi48 on 2010-04-01
Thanks but...
the "alt-F2" thing didn't work. I now have internet access on Linux because I put a hyperlink into a word doc on my desktop. I think the problem started from the third panel messing with the top panel because I could see the 3rd until I put the pointer over it. It then went off the top of the screen, leaving grey space. The only bit of panel that seems to work is the Trash. I went through the trash and now have access to all of my folders.

---

### Post by MooPi on 2010-04-01
Well if you can access a folder let's make a script. Right click and start gedit.
```
#!/bin/bash
gnome-terminal
```
Save the file.
Right click again and make executable. 
Execute the above commands in terminal.

---

### Post by Ancanus on 2010-04-01
You guys are doing some pretty ugly hacks to get a terminal open, now. :D

Try: CTRL + ALT + F1

---

### Post by Sugoi48 on 2010-04-01
I couldn't make it executable. I tried typing both lines into terminal with no results. Thank you anyway.

---

### Post by MooPi on 2010-04-01
Can't give up that easily. I should have included that the right click should show properties. Under the second tab there is a box to check that makes it executable. 
Give it a try. Sorry I didn't include that.

---

### Post by Sugoi48 on 2010-04-01
I'm not giving up! BTW: That ctrl alt F1 thing crashed my computer! :mad:

---

### Post by NCLI on 2010-04-01
> **Sugoi48 said:**
> I couldn't make it executable. I tried typing both lines into terminal with no results. Thank you anyway.

Wait, how did you open a terminal?

If you can open a terminal, just enter the first commands he gave you.

EDIT: ctrl+alt+F1 shouldn't crash your computer, it just opens a text-only interface. To return to Gnome, press ctrl+alt+F7.

---

### Post by Sugoi48 on 2010-04-01
THANK YOU GUYS!!! Everything is back to normal! :D :D :D
You'd never get this kind of support with windows or mac!

---

### Post by NCLI on 2010-04-01
A pleasure. Please return the favor by [marking the thread as solved]("http://ubuntuforums.org/showpost.php?p=4527051&postcount=6") ;)

---

