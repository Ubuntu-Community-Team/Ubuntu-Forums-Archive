---
title: "Touchscreen Faytech with Ubuntu 10.04"
date: 2010-08-13
forum: General Help
---

### Post by MadMax-Linux on 2010-08-13
Hello,

since Ubuntu 9.04 I try to get my USB-Touchscreen from Faytch running...

With some changes in the setup.sh of the drivers that can be downloaded from faytech.de I finally got it running under 9.04.

Changes I made were blacklist path and since no xorg.conf exists anymore I started with a 8.04 Live-CD and copied the xorg.conf from there...
...not nice but worked. :-)

Now with 10.04 new drivers are available but (still only for 8.04).

Did the same hack with the xorg.conf (blacklist path was already updated).

So the driver and touch stuff works

BUT

even without any driver whenever I hit the touch screen (anywhere / even in the middle) I always get a mouse click in the top left corner...

and that keeps on even after installing the driver...

So without driver I get a click in the upper left corner and with driver installed and calibrated I get a click where I have my finger on the screen (that is what I want) AND a click in the upper left corner (THAT IS WHAT I NOT WANT).

I think Ubuntu recognizes the touchscreen as a kind of "unspezified" input device and does a click whenever a touch-event occurs...

How can I deactivate that behavior without disabling all the USB??

---

### Post by MadMax-Linux on 2010-08-19
Finally after again a long long search through the net I found a solution (at least works for me).

With no driver installed xinput -list shows me a eGalax Inc. Touch so this was the device that made the unwanted click in the upper left corner.

After disabling that device xinput -set-prop "eGalax Inc. Touch" "Enabled=0" no click! :-)

After installing the driver an reboot I had two egalax touch.

One named eGalax Inc. Touch and the second just named something like egalax ...

And again I had the unwanted click.

After deactivating again the "wrong" input device everything works just fine!

So I just put the deactivating of the "wrong" device in the startup and since then everything is fine!!

---

### Post by tomcraft2003 on 2010-10-20
[SIZE=3][FONT=Times New Roman]Hello,[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]i have bought an 8 inch faytech screen and tried to use it with ubuntu netbook edition (10.10.) It does not work. Could you help me? If possible please write the necessary steps to use the faytech screen with ubuntu. I was not able to install the drivers (message X Window is necessary). I am a greenhorn in using linux….[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Regards tom[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

### Post by tomcraft2003 on 2010-10-20
[SIZE=3][FONT=Times New Roman]Sorry: I forgot the screen works well, the problem is the touch function…..[/FONT][/SIZE]

---

### Post by MadMax-Linux on 2010-10-28
Hi Tom,

download the newes drivers from e.g. [www.faytech.de](www.faytech.de) for Linux.

Should be a version when you open the setup.sh in an editor you should find something like "blacklistpath" check if one of the paths mentioned there is available on your system.
(should be commented in the setup.sh something like "blacklist path for Ubuntu xxx" then you've the right staring point)

For the "problem" with the missing x-org.conf -> setup stops with error
I booted into a Live-CD with Ubuntu 8.04 (one of the last versions that generates a x-org.conf file) and copied that one to the place where the setup searches for.

Again open setup.sh with an editor and look what search-paths are given. Choose one (cannot tell right now which one I used) and copy the x-org.conf from the Live-Boot with 8.04 there...

Another way maybe to look on the internet and find a "minimal" x-org.conf file that does not include special HW stuff (to not get in conflict with your really used HW)...

When you got the setup through don't forget to deactivate the "unused" touch device like I described...

Maybe  you do the "xinput -list" before installing the driver to find out if Ubuntu already "installed" a touch so you can disable that one!!
Otherwise you might run into the problem like me: always had a "click" in the upper left corner...

Good luck!

If you have any further questions just feel free to contact me...

---

