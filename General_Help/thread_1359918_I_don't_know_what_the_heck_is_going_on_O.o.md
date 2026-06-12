---
title: "I don't know what the heck is going on O.o"
date: 2009-12-20
forum: General Help
---

### Post by Selvaard on 2009-12-20
Hi! This is my first thread as a member, but i have been using ubuntu for half a year. I installed it on my HP laptop, and its was just running great, i mean, no problems at all, till now.
Three weeks ago (maybe it has something to do with the installation of Karmic Koala?), when i switched on my laptop, sometimes it entered directly into terminal mode, i mean, i couldn't even login if it wasn't in terminal mode, so i just switch it off and turn it on again, and it went great. Today, it doesnt matter how many times I reboot it, it always shows the terminal mode.
I tried switching to the graphical interface with ctrl+alt+F7, and it does nothing (though i can switch between tty1,tty2,tty3,tty4,tty5,tty6) , and when i try ctrl+alt+F8, I find this: 
 
"fsck from util-linux-ng 2.16
udevd[535]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /lib/udev/rules.d/56-hpmud_support.rules:10
 
/dev/sda: clean, 261606/9601024 files, 4993087/38373252 blocks"
 
Also, i can move around all my directories, create and remove them, but i can't gedit or bash anything, it shows up this message:
"(gedit:2166): Gtk-WARNING **: cannot open display:"
 
Any ideas? :)

---

### Post by louieb on 2009-12-20
At the grub menu press **e** to edit - remove the **quiet splash** from the kernel line. Then continue to boot. (this is a temporary change  - it will only be in effect this one boot).

This will let you see whats going on and might give a better clue as to what is wrong.

---

### Post by efflandt on 2009-12-20
Apparently you are able to get to a console, but X does not appear to be working properly.  After you log into the console see what happens when you do: **startx**

Check any logs related to X in /var/log.

If you changed monitors or monitor cable type and/or removing the "quiet splash" from boot parameters works, edit /etc/usplash.conf to the "native" resolution of your display.  For DVI or HDMI having a resolution that your monitor is "capable" of is apparently not enough.

gedit works in X or gnome, but not in the console.  Try using **nano** instead which is intuative or you can get more info about it with **man nano**.  The -w switch can be useful for avoiding wordwrap for scripts and config files that should not be.  For example **sudo nano -w /etc/default/grub**

---

### Post by Selvaard on 2009-12-20
Dude, I wrote down **startx** and it started the graphical interface, thx! Anyways, I looked in the /var/log directory and i found this:

Xorg.0.log
Xorg.0.log.old
Xorg.1.log
Xorg.1.log.old
Xorg.2.log
Xorg.3.log
Xorg.failsafe.log
Xorg.failsafe.log.old

What can I do with them? because i suppose that the problem is yet there, and the **startx** thing is just a "patch", ah, I haven't changed the monitor cable or the monitor.

Also, I removed the quiet splash line from the kernel in the grub menu and it made my terminal go crazy, it changed the size of the letters and some other cool stuff that kinda shocked me.

Thanks for your help!!

---

