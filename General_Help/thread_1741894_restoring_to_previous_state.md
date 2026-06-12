---
title: "restoring to previous state"
date: 2011-04-28
forum: General Help
---

### Post by p@nos on 2011-04-28
hello to ubuntu community

an hour ago, i installed the 11.04 version of ubuntu through the auto update method by clicking yes to the process....

i am a new ubuntu user(used the previous version, 10.10 i think, for only two months and was excited) and i don't know much...

i had just learned the old version, and now with the new one(11.04), the appearance is different, and the enviroment is also not the same...some applications i had previously installed, now don't work, and every graphic proccess is very slow...
i am very disappointed from the way my computer works right now and i want to return my computer to a previous state(one day ago for example), with the previous version of ubuntu which i have learned and worked much faster...


is that possible?if not i should format my disk and install the previous version from the begining losing all my files, something that i want to avoid.

---

### Post by TeoBigusGeekus on 2011-04-28
> **p@nos said:**
> hello to ubuntu community

an hour ago, i installed the 11.04 version of ubuntu through the auto update method by clicking yes to the process....

i am a new ubuntu user(used the previous version, 10.10 i think, for only two months and was excited) and i don't know much...

i had just learned the old version, and now with the new one(11.04), the appearance is different, and the enviroment is also not the same...some applications i had previously installed, now don't work, and every graphic proccess is very slow...
i am very disappointed from the way my computer works right now and i want to return my computer to a previous state(one day ago for example), with the previous version of ubuntu which i have learned and worked much faster...


is that possible?if not i should format my disk and install the previous version from the begining losing all my files, something that i want to avoid.

Try selecting Ubuntu classic from sessions when you log in and see if you can get better performance.
If that doesn't work, I'm afraid you'll have to reinstall (after creating a backup of your files of course).
Personally, I've never had any luck upgrading to a new Ubuntu release; others will tell you the opposite.
Always go for a fresh installation.

---

### Post by p@nos on 2011-04-28
thanks gia tin grigori apantisi :D

unfortunatelly i logged out and i can see no option in turning to ubuntu classic, only my account for logging in...is there any other way to return to ubuntu classic?

---

### Post by TeoBigusGeekus on 2011-04-28
After you select your account, there should be a pull down menu at the bottom of the screen called sessions. See if you have the "Ubuntu Classic" option.

---

### Post by p@nos on 2011-04-28
something happened and now there is only the desktop with icons...no tool bars...no other buttons..no shut down button...i can't even find firefox...what can i do just to return the buttons????

---

### Post by TeoBigusGeekus on 2011-04-28
Press Alt+F2 and give
```
gnome-terminal
```
Once the terminal opens, give
```
gnome-panel
```
Post us any error messages.

---

### Post by p@nos on 2011-04-28
also there are no control bars on every window i open...

i can't close, move or minimize any window...if i want to close a window i should go to file->quit

many problems for no reason i regret for updating...

---

### Post by p@nos on 2011-04-28
by pressing alt+f2 nothing happens

i found terminal through search and by writing terminal-panel, the toolbar appears like ubuntu 10.10, but only as long as i have the terminal open, if i shut terminal down, the toolbar disappears...

also there are still no window buttons

---

### Post by TeoBigusGeekus on 2011-04-28
For the window buttons, try
```
metacity --replace
```
from terminal.
Other than than, I think you should reinstall, sorry...

---

