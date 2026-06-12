---
title: "reenable middle mouse emulation on left+right click"
date: 2011-03-15
forum: General Help
---

### Post by chriskin on 2011-03-15
i would like a combination of left and right mouse clicks to get me the same effect as the middle mouse does. when i first used the middle mouse button this stopped happening

---

### Post by LowSky on 2011-03-15
Sorry you can't combine two mouse buttons as you ask, you can use a keyboard mouse button combo.

Read this for more info
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

---

### Post by chriskin on 2011-03-15
i know that i can combine two mouse buttons like that, it worked perfectly up until some hours ago that i first used the middle mouse button.
it has been working for more than two years now..

---

### Post by mc4man on 2011-03-15
see here for a workaround for 2 button mouse (if that's what you mean), it's in the bug description
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/710762](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/710762)

---

### Post by chriskin on 2011-03-16
thanks, it worked perfectly

---

### Post by BryanFRitt on 2011-04-06
# FYI: When my middle click started acting quirky, I searched for how to do this.

# you can use what ever editor you want for this, although the editor needs to have 'root' permissions to save

kdesudo kate /etc/X11/xorg.conf &

# insert this into the file
# I stuck this after the first 'EndSection', and it works
# I don't know if it matters where you stick it.

 Section "InputClass"
     Identifier "middle button emulation class"
     MatchIsPointer "on"
     Option "Emulate3Buttons" "on"
 EndSection

# and then logout (and log back in)

# see also
# [https://wiki.ubuntu.com/X/Quirks#2-button%20Mice](https://wiki.ubuntu.com/X/Quirks#2-button%20Mice)
# ?It lists the wrong file for this?

# [https://wiki.ubuntu.com/NattyNarwhal/TechnicalOverview](https://wiki.ubuntu.com/NattyNarwhal/TechnicalOverview)
# "The -evdev driver no longer provides middle mouse button emulation. 2-button mice that need this functionality are quite rare these days. The emulation mode causes a laggy pointer in cases where emulation is not needed, so this change improves responsiveness for all users. If you have a 2-button mouse that needs this, please see the directions for creating a 2-button mouse quirk. (710762) "

# [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/710762](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/710762)

---

