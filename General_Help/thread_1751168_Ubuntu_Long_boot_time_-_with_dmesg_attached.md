---
title: "Ubuntu Long boot time - with dmesg attached"
date: 2011-05-06
forum: General Help
---

### Post by spaik on 2011-05-06
Hello all

I have installed ubuntu 11.04 fresh install and everything is working just fine except when i boot into ubuntu from grub ( i have also windows 7 installed) it takes like 2 to 5 minutes to boot. it shows a blank purple screen with no activity from the laptop and sometimes a black screen with blanking underscore. i really need a fix because come on Ubuntu is all about being fast :D 

here is dmesg [http://pastebin.com/8Sci1WYk](http://pastebin.com/8Sci1WYk)

please help me :)

thanks in advance.

UPDATE--------------------------------

Its now Fixed by disabling Legacy USB Support and its working as it should be.
---------------------------------------------UBDATE

---

### Post by ajgreeny on 2011-05-06
Are you using a btrfs file system?  There is mention of it in your dmesg, but for all I know, it may always be there, even when no btrfs exists on the machine.

More useful next time you boot is to hit "E" at the grub menu on the line you normally boot, then using cursor keys scroll to the line that ends "quiet splash" and delete those two words.

Now use Ctrl+X to boot with a full text output, instead of plymouth splash screen.  Look to see what is showing when the delay or slow down occurs, and then come back again, and ask if anyone knows what is going on, and how to stop it happening..

---

### Post by Toz on 2011-05-06
```
pci 0000:00:13.5: EHCI: BIOS handoff failed (BIOS bug?) 01010001
```

appears to be your problem. Buggy bios?

Have a look at: [http://ubuntuforums.org/showthread.php?p=10015667](http://ubuntuforums.org/showthread.php?p=10015667)

Suggested is to try disabling "Legacy USB Support" in Bios, if possible.

---

### Post by spaik on 2011-05-07
i will try disable Legacy usb Support and see what happens.

---

### Post by spaik on 2011-05-08
ok that did the trick :) after disabling Legacy its now working normally :) thanks a lot for the help :)

---

### Post by Lamukra on 2011-09-15
I had problem with login and boot time also, reason was in xorg.conf file configuration
Problem was coming from synaptics touchpad, where the special .conf file was created to make a scrolling work.

Below is outtake from launchpad bug report my comment, how I made scrolling work
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543)

> It was annoying to be without scrolling, so created a file with name psmouse.conf in:

/etc/modprobe.d

with text inside:

options psmouse proto=imps

Saved and run through commands:

```
sudo modprobe -r psmouse
sudo modprobe psmouse
```

After this my ALPS is detected as ImPS/2 Generic Wheel Mouse, but scrolling is working

After making this, I totally forgot about xorg.conf, that I had a Section InputDevice with assigning a driver to my touchpad, what was creating and error, because after making scrolling to work my touchpad was recognized as imPS2 mouse, but not as Synaptics Touchpad... so it was causing the long LOGIN time and partly a boot time

X was trying to find Synaptics Touchpad but there was imPS assigned Physically, so this so to speak searching time made an interface to stuck...

Solution

Simply comment out Section InputDevice and InputeDevice in Server Layout in xorg.conf

It solved the problem in my case, hope it will help someone

---

