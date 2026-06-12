---
title: "Reset System Time"
date: 2010-01-09
forum: General Help
---

### Post by damitch on 2010-01-09
Just made a fresh install of Karmic on a spare desktop, dual-boot with Windows XP (if that's relevant).  Strange problem:  notwithstanding that I selected the suitable time-zone for the computer, the desktop time is off by several hours.  Well, no big deal, right?

When I go to the time administration dialog, when I click that I want to change the time, it reasonably asks for a password.  When I give it, the scroll controls activate, as they sensibly should.

As soon as I leave the new hour value alone for a second or so, it resets to the earlier bad value.

I've also tried using the terminal and running
```
sudo time-admin
```

and I've also tried
```
gksu time-admin
```

Both ask for a password, but otherwise quickly reset the time controls - when changed - to the current bad value, and there seems no way to actually change the time display.

Help.  Thanks.

---

### Post by lyall on 2010-01-09
right click on the time and select Preferences

on the Clock Preferences
click on the Locations tab
click on Add and enter your Location Name:
enter your Timezone:
if it looks okay then click OK
back on the Locations tab click on the Time Settings at the bottom
change your time if it is not right and click on Set System Time
then click Close

your time should be set for you

good luck and have fun learning

---

### Post by dcstar on 2010-01-10
> **damitch said:**
> 
.........
I've also tried using the terminal and running
```
sudo time-admin
```
and I've also tried
```
gksu time-admin
```

Try:
```
sudo tzselect
```

---

### Post by Bright_View on 2010-01-10
If you get to your wits end with this problem and cannot figure out why the clock won't hold the proper time, you may want to try switching your motherboard battery with a new one.  I'm not a hardware expert, but a dead battery can mess with clock settings.  See, for example, this article:

[http://www.pcguide.com/ts/x/comp/mbsys/cmos.htm](http://www.pcguide.com/ts/x/comp/mbsys/cmos.htm)

The switching of the battery is usually very easy if you have the most common type.  Detailed instructions can be found here:

[http://www.hardwaresecrets.com/article/81](http://www.hardwaresecrets.com/article/81)

Dave.

---

### Post by damitch on 2010-01-17
> **lyall said:**
> right click on the time and select Preferences

on the Clock Preferences
click on the Locations tab
click on Add and enter your Location Name:
enter your Timezone:
if it looks okay then click OK
back on the Locations tab click on the Time Settings at the bottom
change your time if it is not right and click on Set System Time
then click Close

your time should be set for you

good luck and have fun learning

Solved it.  Many thanks.

---

