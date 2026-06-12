---
title: "why my folder icon is different from my themes??"
date: 2009-12-12
forum: General Help
---

### Post by michael18 on 2009-12-12
i'm using the 'Human' themes...and i don't understand why my folder icon is different...and i cant change it back to normal...
when i open the home folder or any fole browser...it still the same...even i change the themes...the folder icon is still the same...

how can i change it back?

i've attach a screenshot of my folder...u guys can help a look and pls help..=(

*p.s: i juz started using LINUX Ubuntu for the 1st time...

---

### Post by coffeecat on 2009-12-12
Those are the standard gnome folder icons. But that nautilus window doesn't look right. First thing - are you running that nautilus window as root using 'gksudo nautilus'? If not, open the Appearance window as in your screenshot with the Human theme selected. Now click on the 'Customise' button and then the 'Icons' tab in the new window. Can you find the 'Humanity' icon theme? If so, select it. If not, you must have uninstalled it, and you need to open Synaptic and re-install 'humanity-icon-theme'.

---

### Post by michael18 on 2009-12-12
yea...the 'Humanity' is still there...

but even i change another type of the icon still not working...those folder icon doesn't change anyway...

---

### Post by fragos on 2009-12-12
When you run nautilus as root, the theme defined in root is used. Every user including root gets to define it's own theme and parameters for nautilus and gedit for example.

---

### Post by drewsus on 2009-12-12
Doesn't look like that folder is showing as root. 
It would say "root" and not his user name. 

Does running this in terminal help?:
```
killall nautilus && nautilus
```

---

### Post by drewsus on 2009-12-13
The code I provided about (kill and restart nautilus) only has limited results. That is, in windows my theme and icons are back to normal, but not in my panel. I also tried doing "killall gnome-panel" but it did not fix the problem. 
I am noticing I am having this issue now too. 
Just happened when I switched to dual monitor view. Has happened before. 
Changing my theme and icons to something different and then back to normal does seem to set it back... But what is causing my user to lose the theme and icons? This is also happening to my girlfriends netbook (I am using an Acer Aspire One, she is using a Dell Mini 10v).
This issue needs to be resolved!

Drew

---

### Post by MooPi on 2009-12-13
Playing a hunch, but check and see if there is a file in your home directory > .gtkrcIf so it is countering your default theme. I remember a while ago I also had this problem but for different reasons. I had switched my file manager and left a previous config in my home directory.

---

### Post by drewsus on 2009-12-13
I was so optimistic that this would be the issue, but it is not. There is no .gtkrc file in my home directory and I just did a system search for it as well (included hidden files and folders)

Any other ideas?

---

### Post by nikhil_shirgaonkar on 2009-12-13
I am also facing d same problem as the above person the icons doesn't change if i change d themes or even if i install a diff. icon package it doesn't change 2 tht also. So what can b d reason plzz help
I am using Ubuntu 9.10 Karmic Koala

---

### Post by drewsus on 2009-12-13
What confuses me is that the appearance window seems to have the proper theme/icons/fonts, but the panel, desktop and nautilus do not.

---

### Post by drewsus on 2009-12-14
Im curious, everyone having this problem, did you ever issue one or both of these commands?
```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```
Or, have you ever do the same thing using Ubuntu Tweak?

Additionally, what did you do to make this happen? Just on log in? 
?

I cannot faithfully reproduce this issue. For me, it has only really happened when enabling dualscreens. But I think it happens to my girlfriend randomly on log in. 

Finally, when it happens, does this help?
```
metacity --replace &
```

---

