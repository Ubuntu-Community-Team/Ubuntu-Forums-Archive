---
title: "Help with garbled text"
date: 2006-06-09
forum: General Help
---

### Post by yesindeed on 2006-06-09
When I first installed dapper, I tried to get the digital ouput from my vidoe card to my monitor to work, but I could not. Now I only have the analogue port connected. However, when I try to do ctrl-alt-function to switch to a terminal, the screen becomes garbeled, and my machine locks up. I am using the nvidia graphics drivers (the accelerated ones). 

As I am much more of a terminal man than a gui person, this troubles me greatly. 

Also, when I do a ctrl-alt-backspace to go stop X, the same thing happens. It seems that it just cannot view a blank terminal. 

Thanks in advance for any help you may provide.

---

### Post by mlind on 2006-06-09
You are using nvidia proprietary drivers (official ones) right?

Can you find anything releated to garbled screen / lockup by viewing
/var/log/Xorg.0.log (or other Xorg.x.log files).

There are few switches to try with propietary nvidia drivers, like *RenderAccell off*
(which is now enabled by default).

---

### Post by yesindeed on 2006-06-09
I think its the prop. ones. Its the ones that ubuntu easy automatically installs. I'll check out those logs and siwtches too.

---

