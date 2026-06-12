---
title: "Setting mouse wheel scrolling speed"
date: 2011-12-07
forum: General Help
---

### Post by tamerucar on 2011-12-07
Hi All,
How do I change the scrolling speed of mouse wheel on Ubuntu 11.10?
There is no such thing under Mouse and Touchpad settings.

---

### Post by bluexrider on 2011-12-07
not a system-wide setting yet

---

### Post by inkrypted on 2011-12-07
First make sure you have the proper name of your device.
Run xinput --list --short in a terminal
then use xinput --set-prop "devicename" "command to change settings"
For example xinput --set-prop "Razer Razer DeathAdder" "Device Accel Constant Deceleration" 5 when run in a terminal Sets the constant deceleration. This is the command I believe you need.
xinput set-int-prop "device" "Evdev Wheel Emulation Inertia" 16 5
The 16 is 16 bit, and the 5 is the Inertia.  Think of it like friction.  The higher the number, the more resistance to movement.  Don't set it to zero though, because we can't divide by zero

---

### Post by inkrypted on 2011-12-07
To Make these commands persistent you may have to put them in a bash file and have that run at start up. Otherwise when you reboot you may loose the customization.

---

### Post by tamerucar on 2011-12-08
> **inkrypted said:**
> First make sure you have the proper name of your device.
Run xinput --list --short in a terminal
then use xinput --set-prop "devicename" "command to change settings"
For example xinput --set-prop "Razer Razer DeathAdder" "Device Accel Constant Deceleration" 5 when run in a terminal Sets the constant deceleration. This is the command I believe you need.
xinput set-int-prop "device" "Evdev Wheel Emulation Inertia" 16 5
The 16 is 16 bit, and the 5 is the Inertia.  Think of it like friction.  The higher the number, the more resistance to movement.  Don't set it to zero though, because we can't divide by zero

Thanks for the reply.

Changing the "Device Accel Constant Deceleration" value did affect my mouse cursor speed. But I saw no difference on wheel scrolling speed after changing "Evdev Wheel Emulation Inertia". I tried several values for Inertia within 1 to 100. But there was no change.

What can be wrong here?

---

### Post by inkrypted on 2011-12-08
If memory serves there is a program called imwheel that will allow you to change the scroll speed. I put up a link to the manpage. See if that might be what you are looking for.
[http://imwheel.sourceforge.net/imwheel.1.html](http://imwheel.sourceforge.net/imwheel.1.html)
xinput should have worked but maybe i got the command wrong I also added a link to xinput manpage.
[http://manpages.ubuntu.com/manpages/intrepid/man1/xinput.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/xinput.1.html)

---

### Post by d2btoo on 2011-12-08
[http://askubuntu.com/questions/27270/increasing-scroll-speed](http://askubuntu.com/questions/27270/increasing-scroll-speed)
[https://bugs.launchpad.net/gtk/+bug/124440](https://bugs.launchpad.net/gtk/+bug/124440)

-- In short, not possible, as stated by bluexrider.

---

### Post by tamerucar on 2011-12-08
> **inkrypted said:**
> If memory serves there is a program called imwheel that will allow you to change the scroll speed. I put up a link to the manpage. See if that might be what you are looking for.
[http://imwheel.sourceforge.net/imwheel.1.html](http://imwheel.sourceforge.net/imwheel.1.html)
xinput should have worked but maybe i got the command wrong I also added a link to xinput manpage.
[http://manpages.ubuntu.com/manpages/intrepid/man1/xinput.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/xinput.1.html)

Thanks, I'll look those.

---

### Post by bluexrider on 2011-12-08
found this from Ubuntu 

[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

its a follow up about imwheel

happy *buntu

---

