---
title: "Time applet reverts to Central time upon restart"
date: 2010-01-01
forum: General Help
---

### Post by newagelink on 2010-01-01
I go to college in middle TN (central standard time), and went home to eastern TN (eastern standard time).

The time on the desktop bar appears screwed up: I can set the time, but upon restart it goes to CST; there is no way for me to change timezone -- perhaps the applet has changed after some update I installed. I recall their being a way to change Timezone -- perhaps it was through Adjust Date & Time -- but now that menu option opens a window titled "Time Settings" that only allows me to change the time itself.

How do I reinstall the time applet? Have I clearly described the error I'm getting? Any help you can give me would be greatly appreciated.

---

### Post by gordintoronto on 2010-01-01
If you click on the date, there's a popup which includes "locations."  Have you tried this route?

---

### Post by dcstar on 2010-01-01
> **newagelink said:**
> I go to college in middle TN (central standard time), and went home to eastern TN (eastern standard time).

The time on the desktop bar appears screwed up: I can set the time, but upon restart it goes to CST; there is no way for me to change timezone -- perhaps the applet has changed after some update I installed. I recall their being a way to change Timezone -- perhaps it was through Adjust Date & Time -- but now that menu option opens a window titled "Time Settings" that only allows me to change the time itself.

How do I reinstall the time applet? Have I clearly described the error I'm getting? Any help you can give me would be greatly appreciated.

There are multiple timezone settings on an install, the base system timezone and user based timezones.

This will allow you to set the base system timezone:
```
sudo tzselect
```

---

### Post by Throbbing Gristle on 2010-01-01
I wanted to fix mine but the choices greatly confused me. I used the command 
and got lost from there?
sudo tzselect

---

### Post by newagelink on 2010-01-01
> **gordintoronto said:**
> If you click on the date, there's a popup which includes "locations."  Have you tried this route?Right click on time -> Preferences opens "Clock Preferences" window. I click the 'Locations' tab, and add my location, removing the lattitude and longitude (since I think I screwed it up when entering it -- where can I read the proper formatting for the input?). We'll see what happens upon restart.

(Note: I get the error -- of the time reverting back an hour -- also when resuming from Suspend.)

---

### Post by dcstar on 2010-01-01
> **Throbbing Gristle said:**
> I wanted to fix mine but the choices greatly confused me. I used the command 
and got lost from there?
sudo tzselect

So you don't know where you are?

---

### Post by Throbbing Gristle on 2010-01-01
Mountain time zone Denver Colorado USA did not see that choice in there got lost fast!_******_

---

