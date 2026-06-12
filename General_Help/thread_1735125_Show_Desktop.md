---
title: "Show Desktop"
date: 2011-04-20
forum: General Help
---

### Post by stevenmelgar on 2011-04-20
I done gone and effed up... This problem is completely my fault....
Okay. So I'm still new to Ubuntu and I wanted to play with it and do all these cool things I've seen. I tried doing the animated desktop background and failed at that, but that's not the problem. I had to deactivate some function in Nautilus to even attempt this. Trouble is, now I can't turn it back on. I want to be able to right click on my desktop again but don't know what to do. 
If you have any ideas, I'd love the help. And if you could write it so that a fool like me can understand it, that would be nifty.

---

### Post by etopsirhc on 2011-04-20
if you did what i think u also lost all of the shortcuts on your desktop , so if its that heres what to do 

hit alt+f2 then type in sudo gconf-editor
type in ur pass of course . in the program that pops up , go in apps>nautilus>preferences 
then look in the side bar for show_desktop and make sure its checked

---

### Post by stinkeye on 2011-04-21
> **etopsirhc said:**
> if you did what i think u also lost all of the shortcuts on your desktop , so if its that heres what to do 

hit alt+f2 then type in sudo gconf-editor
type in ur pass of course . in the program that pops up , go in apps>nautilus>preferences 
then look in the side bar for show_desktop and make sure its checked

Why are you running gconf-editor as root?

alt+f2 and run
```
gconf-editor /apps/nautilus/preferences/show_desktop

```

---

### Post by etopsirhc on 2011-04-21
idk, i tend to run everything as root unless i know otherwise XP

---

### Post by stinkeye on 2011-04-21
It's more secure and less chance of stuffing something up 
to do it the other way around.

---

### Post by Krytarik on 2011-04-21
> **stinkeye said:**
> It's more secure and less chance of stuffing something up 
to do it the other way around.
Plus you *really* change the settings of the user, not those of root.

---

### Post by yetiman64 on 2011-04-21
> **stinkeye said:**
> It's more secure and less chance of stuffing something up 
to do it the other way around.

++++1,   @ etopsirhc, please read this link [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
scroll down to the Basics section, Windows mindset and Ubuntu mindset sections for the info you need to see.

> Limit root access **(Do not log in or run programs as root)**. Ubuntu  accomplishes this by locking the root account and the use of sudo.  I have emphasized the important bit with bolded text.

Your advice seems OK except for the use of sudo. Roots settings shown with your command are different to the users settings and the situation can become quite confusing for the person you are attempting to help in this case.

@ OP try etopsirhc's post but **WITHOUT** the use of sudo in the command. Should work OK.

---

### Post by stevenmelgar on 2011-04-21
Fixed! Thanks!!! :)

---

