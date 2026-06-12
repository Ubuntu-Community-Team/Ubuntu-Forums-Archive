---
title: "Top bar and dock mess - Ubuntu doesn´t function"
date: 2010-12-03
forum: General Help
---

### Post by Predrag Jelic on 2010-12-03
Hey! I´m quite new with the Linux Ubuntu OS 10.10 so hope that I am going to be able to explain everything right, plus I´m using a serbian translated version, so I´m not quite sure what are the names of all the parts of the system... :)

I have two bars on top of my screen and I have also installed the application that makes Mac-like dock at the bottom of the screen. It made an ugly black square, so I have turned the graphic properties to the maximum (where one can change the desktop picture, also).

Then I have made a tragic mistake of turning on the auto-hide option of the lower bar at the top of my screen.

Now the lower bar is on top of the higher one, and it shakes... It also blocks my keyboard and I can only move my mouse over the desktop...

When I have restarted the computer, it only gaye me the docks with this ugly black square again, and only the lower bar showing, which was again shaking, and only 5-10 seconds to open the terminal or do anything with my keyboard, before it was blocked...


Also, as I have upgraded to the ubuntu 10.10, I haven´t been able to access the Ubuntu Software Center and when I get to choose the Operating System, I get the choice of three different Ubuntu systems each ending with different number (as I can remember 23, 21 and 25) and recovery mode for every one of them...


Please, help me. I am now in my University computer room and I really need my laptop to function. 

Thanks in advance! :)

---

### Post by Predrag Jelic on 2010-12-16
Anyone? ^^

---

### Post by migs73 on 2010-12-16
Use this code in terminal to set your panels back to the defaults;

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```


Mike

---

