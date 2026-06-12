---
title: "hookup to tv, monitor turns off on login/logout"
date: 2011-10-23
forum: General Help
---

### Post by SE7EN-LOCSTA on 2011-10-23
ubuntu 11.10 x64 - acer aspire 5734z

i hooked my laptop up to someones tv for movie viewing, and now when i log in or out, the monitor's backlight shuts off - no longer hooked up to tv. i have looked in monitor settings, and it shows only the main monitor is hooked up, so its not an issue with that. 

i have a laptop that is affected by the backlight issue anyways, so i run 'acpi_os= ' from grub, and 'setpci -s 00:02.0 F4.B=00' from /etc/rc.local to make the backlight come on during bootup. i have a hotkey setup to run the setpci command after i login, which works, but when i log back out, it turns the backlight off again, making me unable to switch between users/gnome3-unity. 

the other thing this harms is that a second user without admin privileges is unable to run the command to return screen brightness at all, so basically noone else can use the computer. i had already tried previously to edit the sudoers file to give other users ability to run the command, but it doesnt stick. it would work until logout, then something would happen, i was locked out from running any sudo/gksudo command at all, requiring me to live cd and restore the sudoers default file, checked it twice with same results.


anyways, anybody know of a way to get my monitor back the way it was before i hooked it up to a tv?   

-if it matters at all, i set the dual monitor setup to 'mirror'. before i did that, monitor showed workspace 1, tv showed workspace 2. after switching to mirror, monitor backlight switched off and tv worked fine.

---

### Post by SE7EN-LOCSTA on 2011-10-24
i tried to find the xorg.conf file, to maybe reset it or something, but i  do not seem to have one, i seen somewhere you have to make it yourself,  which is probably out of my range of linux knowledge. i also tried to  reinstall xorg from synaptic, but it didnt have any effect. any  suggestions?

---

### Post by SE7EN-LOCSTA on 2011-10-26
OK, how about a way to access the dual monitor settings without actually having a 2nd monitor attached? maybe if i could take it off of 'mirror' it might fix it, but i dont have anything to hook it to now...

---

