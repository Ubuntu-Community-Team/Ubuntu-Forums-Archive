---
title: "How do I get grub to boot XP in safe mode?"
date: 2006-02-18
forum: General Help
---

### Post by NiceGuy on 2006-02-18
Hi there all, 

At the moment grub shows me options for booting into ubuntu, ubuntu recovery mode, memtest and windows xp. I was wondering if anyone knows how I can get grub to boot into windows 'safe mode'.

---

### Post by hegenious on 2006-02-18
let grub boot windows xp and then immediately press F8 .
you will be offered the option to start windows in safe mode.
dunno how you could have grub do that for you.

if grub reads the nt boot.ini, perhaps you could add a line for safe mode boot in the .ini and it would then possibly be listed by grub.
perhaps I'm getting carried away though  :]]

---

### Post by Zalbor on 2006-02-18
I don't think the F8 trick works in XP. At least it doesn't work for me.
The way I know to do it (though it has nothing to do with Ubuntu :)) is, while in XP, go Start>Run and type "msconfig". Go to the boot.ini tab of that program and check the /SAFEBOOT option, then reboot into XP.
To go back to normal mode, run msconfig and uncheck the option (or choose normal boot in the first tab, unless you have reason not to).

---

### Post by hegenious on 2006-02-18
the F8 trick works allright in xp. trouble is with hitting it exactly the right moment.
hitting it repeatedly sometimes works better.
but why not add the safe mode option to the boot menu?
this site explains how to do it.
[http://www.theeldergeek.com/add_safe_mode_to_boot_menu.htm](http://www.theeldergeek.com/add_safe_mode_to_boot_menu.htm) 

however, I don't know if after that it shows the option in grub but there is a fair chance it does.

---

### Post by NiceGuy on 2006-02-18
Hey guys, thanks for all the replys. I knew that pressing F8 booted you in to safe mode (and about doing the msconfig thing) but, as some of you guessed, what I was after was a way of grub listing windows safe mode as an option. 

I've had a look at the menu.lst file in /boot/grub and I'm guessing I have to add some kind of 'kernel' or 'initrd' option inorder to boot into safe mode. Perhaps something like 'Microsoft Windows XP Professional Safe' or similar (as described on the page hegenious' post linked to).

I guess I'll just have to play.

I'll let you all know if I get lucky!

---

