---
title: "help with swappiness value"
date: 2011-04-16
forum: General Help
---

### Post by apoorvmunshi on 2011-04-16
hello....i just want to change the swappiness value of my system.
now what should i use to edit the files of ubuntu? is the terminal used to edit those files? i read this link:[https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)
i know i am being silly....but plz help me..i am very very very new to linux:lolflag::lolflag:

---

### Post by Timmer1240 on 2011-04-16
[http://www.ubuntuvibes.com/2010/10/things-to-do-after-new-ubuntu-1010.html](http://www.ubuntuvibes.com/2010/10/things-to-do-after-new-ubuntu-1010.html) here it tells you what to do

---

### Post by VCoolio on 2011-04-16
Use whatever you like. Most will use terminal to edit system files, like "sudo nano /etc/sysctl.conf" (replace nano with vim if you know how that works). If you use graphical editors, use gksudo, like your link says: "gksudo gedit /etc/sysctl.conf" to use gedit. You'll need root permission to edit that file; you can enter these sudo commands in a terminal or the gksudo commands in the popup box from alt+f2.

---

### Post by DanneStrat on 2011-04-16
> **apoorvmunshi said:**
> hello....i just want to change the swappiness value of my system.
now what should i use to edit the files of ubuntu? is the terminal used to edit those files? i read this link:[https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)
i know i am being silly....but plz help me..i am very very very new to linux:lolflag::lolflag:

Hi.

Yes, you will use terminal to change swappiness

as it would be the easiest way.

You can use gedit text editor that's already included with 

ubuntu.


Begin by checking your current swappiness value

by doing this:

```
cat /proc/sys/vm/swappiness
```

It should be "60".

Now, to change swappiness, open terminal and do:

```
gksudo gedit /etc/sysctl.conf
```

This will bring up gedit with the file you want

to edit. The default value of swappiness is "60"

and the recommended value is "10".

Add this line to the end of the file:

```
vm.swappiness=10
```

Then save the file and reboot.

You can now do:

```
cat /proc/sys/vm/swappiness
```

and you will notice your new value is "10".

Good luck.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by clhsharky on 2011-04-16
apoorvmunshi


> is the terminal used to edit those files?
Use terminal to open gedit as super user.
Copy/paste 
```
gksudo gedit /etc/sysctl.conf
```
Enter password.
> now what should i use to edit the files of ubuntu?
Gedit will now allow you to edit your file.
I use 30 instead of default 60, 10 should be the minimum.
> Save the file and reboot. 


Sharky

---

### Post by apoorvmunshi on 2011-04-17
thanks to all of u. it worked!!!!:D:D looking for :popcorn::popcorn:more help from u guys....c ya

---

