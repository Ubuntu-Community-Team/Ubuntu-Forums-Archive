---
title: "Unable to install from USB"
date: 2011-04-19
forum: General Help
---

### Post by dago1 on 2011-04-19
BIOS wont boot linux from a USB drive. I made a bootable USB of x32 10.04 using a x64 9.04 system, not once but several times.

[IMG]http://i.imgur.com/gBxs0.png[/IMG]


[IMG]http://i.imgur.com/12Kll.jpg[/IMG]

I reboot my computer press delete to go to BIOS settings and select the first boot device to be either of the several USB options.

The BIOS will simply not boot from USB and instead will boot from hard drive as usual.

I have a GA-P35-DS3L motherboard.

---

### Post by dago1 on 2011-04-19
Here is what the install USB stick looks like after I open it.


[IMG]http://i.imgur.com/Gw1VW.png[/IMG]

---

### Post by dago1 on 2011-04-19
Ok I managed to get it to boot from USB by completely disabling the hard drive as a boot option but now the process is stuck. After the splash screen with the keyboard and guy inside a circle, the process halts. It keeps displaying the ubuntu logo on and on and on. if I press esc the screen turns black and the following text appears.

/init: line7: can't open/dev/sr0: No medium found 
/init: line7: can't open/dev/sr0: No medium found 
stdin: error 0

I press esc again and the screen goes back to the ubuntu logo with the blinking dots. After pressing esc one more time the black screen looks like this 


/init: line7: can't open/dev/sr0: No medium found 
/init: line7: can't open/dev/sr0: No medium found 
stdin: error 0

/init: line7: can't open/dev/sr0: No medium found 
/init: line7: can't open/dev/sr0: No medium found 
stdin: error 0

I keep on pressing esc and:

/init: line7: can't open/dev/sr0: No medium found 
/init: line7: can't open/dev/sr0: No medium found 
stdin: error 0

/init: line7: can't open/dev/sr0: No medium found 
/init: line7: can't open/dev/sr0: No medium found 
stdin: error 0

/init: line7: can't open/dev/sr0: No medium found 
/init: line7: can't open/dev/sr0: No medium found 
stdin: error 0

/init: line7: can't open/dev/sr0: No medium found 
/init: line7: can't open/dev/sr0: No medium found 
stdin: error 0

/init: line7: can't open/dev/sr0: No medium found 
/init: line7: can't open/dev/sr0: No medium found 
stdin: error 0


alternating between the ubuntu logo screen with the blinking dots and the black screen with the error messages.

---

### Post by C.S.Cameron on 2011-04-19
GA-P35-DS3L looks fairly modern, have you tried booting your flash drive on another computer?

The persistence looks small, 128, once casper-rw is filled the drive will not boot.

In BIOS it should be selected as first hard drive.

Check the MD5SUM of the iso, sometimes everything looks ok but is actually a bad install.

Try another flash drive, some don't work as good as others.

---

