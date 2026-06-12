---
title: "Removing Battery Status Warnings"
date: 2011-09-19
forum: General Help
---

### Post by EggMasta on 2011-09-19
I am using 11.04 and this problem seems to be present in both classic ubuntu and unity modes. Ubuntu seems to have a problem with my battery, when I am on AC power I keep getting these messages: "Laptop battery critically low" or "Laptop battery discharging". And there seems to be no way of getting rid of them, my battery works fine, I am not sure why I am getting these errors or how to stop them.

Here is a screenshot (Upper right hand corner): 

[http://imgur.com/V7TxN](http://imgur.com/V7TxN)

Any help?

---

### Post by EggMasta on 2011-09-21
Any ideas at all? I will offer a handy sum of $10 to anyone who can help me solve this issue

---

### Post by patryk77 on 2011-09-21
Run gconf-editor and go into /apps/gnome-power-manager/notify. Uncheck low_power; that should do the trick.

---

