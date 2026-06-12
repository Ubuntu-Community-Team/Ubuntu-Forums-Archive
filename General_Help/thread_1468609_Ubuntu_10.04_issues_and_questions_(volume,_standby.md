---
title: "Ubuntu 10.04 issues and questions (volume, standby, cpu)"
date: 2010-05-01
forum: General Help
---

### Post by gophergun on 2010-05-01
I recently upgraded to UNE 10.04 x86, and I'm having a couple issues. To start, my volume applet is now gone, the volume hotkeys on my laptop won't work, and I can't figure out how to add the applet back, since the move/lock to panel options on existing applets are now grayed out. Also, when the laptop goes to sleep automatically, instead of entering standby like it used to, it seems to go into hibernate (at least, I have to boot up the laptop and choose the OS again). Finally, and this is a rather low priority at the moment considering my previous issues, but I was wondering if there was a way to automatically set the CPU governor from ondemand to performance whenever the laptop is plugged in, and vice versa.

---

### Post by P4man on 2010-05-01
> **gophergun said:**
> I recently upgraded to UNE 10.04 x86, and I'm having a couple issues. To start, my volume applet is now gone, [quote[

Right click panel, add to, indicator applet. It comes bundled with the evolution applet which you probably wanted to remove.

> the volume hotkeys on my laptop won't work,

See if the buttons are detected. open a terminal, run 
```
xev
```

press the volume buttons. Does it register them? Also, what laptop is this?

[QUOTE]
 and I can't figure out how to add the applet back, since the move/lock to panel options on existing applets are now grayed out. 

I dont understand.

> 
Also, when the laptop goes to sleep automatically, instead of entering standby like it used to, it seems to go into hibernate (at least, I have to boot up the laptop and choose the OS again).

Can you confirm suspend mode works? is the option available in the shutdown menu?

 > Finally, and this is a rather low priority at the moment considering my previous issues, but I was wondering if there was a way to automatically set the CPU governor from ondemand to performance whenever the laptop is plugged in, and vice versa.

probably, but I have no clue how lol.

---

### Post by gophergun on 2010-05-01
> **P4man said:**
> [QUOTE=gophergun;9212035]I recently upgraded to UNE 10.04 x86, and I'm having a couple issues. To start, my volume applet is now gone, [quote[

Right click panel, add to, indicator applet. It comes bundled with the evolution applet which you probably wanted to remove.



See if the buttons are detected. open a terminal, run 
```
xev
```

press the volume buttons. Does it register them? Also, what laptop is this?



I dont understand.



Can you confirm suspend mode works? is the option available in the shutdown menu?

 

probably, but I have no clue how lol.
On UNR 9.10, the only way to free up a place to right click add to panel IIRC was to move one of the existing applets to the left. On UNE 10.04, though, they seem to be permanently locked to the panel, making it impossible to add applets as far as I can tell. You can see the bug here: [https://bugs.launchpad.net/window-picker-applet/+bug/248324](https://bugs.launchpad.net/window-picker-applet/+bug/248324)

The window xev pulls up seems to show no change regardless of any keys I hit, much less Fn+F11/12 (volume down/up). It is an Asus Eee PC 1000HE.

Suspend mode works perfectly when run from the shutdown menu.

---

### Post by linuxman94 on 2010-05-01
> **gophergun said:**
> The window xev pulls up seems to show no change regardless of any keys I hit, much less Fn+F11/12 (volume down/up). It is an Asus Eee PC 1000HE.

When you run xev the output is shown in the terminal.

---

### Post by gophergun on 2010-05-01
> **linuxman94 said:**
> When you run xev the output is shown in the terminal.
Right, still no new output, even for the clearly working brightness hotkeys.

---

### Post by P4man on 2010-05-01
> **gophergun said:**
> 
On UNR 9.10, the only way to free up a place to right click add to panel IIRC was to move one of the existing applets to the left. On UNE 10.04, though, they seem to be permanently locked to the panel, making it impossible to add applets as far as I can tell. You can see the bug here: [https://bugs.launchpad.net/window-picker-applet/+bug/248324](https://bugs.launchpad.net/window-picker-applet/+bug/248324)

Ah. well, i wasnt aware the panels worked that differently on UNR. Perhaps you can start a normal gnome session from the login menu and reconfigure the panels, and it will stick in UNR?

> The window xev pulls up seems to show no change regardless of any keys I hit, much less Fn+F11/12 (volume down/up). It is an Asus Eee PC 1000HE.

You have to make the little white box the active window to catch mouse and key input.

> Suspend mode works perfectly when run from the shutdown menu.

Then try gconf-editor and browse to 
/apps/gnome-power-manager/actions/sleep_type_ac
and
/apps/gnome-power-manager/actions/sleep_type_battery

Look at the bottom for your options and what those keys do

---

### Post by gophergun on 2010-05-01
> **P4man said:**
> Ah. well, i wasnt aware the panels worked that differently on UNR. Perhaps you can start a normal gnome session from the login menu and reconfigure the panels, and it will stick in UNR?



You have to make the little white box the active window to catch mouse and key input.



Then try gconf-editor and browse to 
/apps/gnome-power-manager/actions/sleep_type_ac
and
/apps/gnome-power-manager/actions/sleep_type_battery

Look at the bottom for your options and what those keys do
I'd tried that, the changes only stick for standard GNOME, not UNR, unfortunately. Also, terminal or white box active, I can't seem to get it to show any change when I hit any keys or mouse buttons, hotkey or not. I'm sure I'm doing something wrong, I just can't figure out what. :p However, the gconf edit worked like a charm. One issue down, one to go?

(Thanks for the patience, by the way.)

---

### Post by P4man on 2010-05-01
Never seen xev not work. But anyway, there is a bug report open for you machine here:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/558628](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/558628)

i suggest you subscribe to it.

cant help with NBR thing im afraid, as ive not used it for longer than 2 minutes :)

---

### Post by anjilslaire on 2010-05-15
To get the volume icon back in Netbook 10.4:
```

sudo apt-get install  indicator-sound

```

---

