---
title: "Is it possible to associate an hidraw device and a usb device?"
date: 2011-07-20
forum: General Help
---

### Post by davidstoll on 2011-07-20
I am making a perl script that needs to run the following command on an hid device...

$data = `cat /dev/hidraw3 | head -c 7`;

However, that is hard coded, so I need to figure out which of the hid devices is the one I'm looking for.

I can run lsusb and find the usb/bus device, but I can't figure out how to use that information to determine which hid device I need to cat.

Cat-ing the hid device does not give me any kind of useful text information that I can grep (it's binary).  Some hid devices basically freeze the command prompt, so I can't even cat each to see what I get.

Any ideas how I can track down the correct hid device?

Thanks so much!

---

### Post by davidstoll on 2011-07-24
bump

---

### Post by davidstoll on 2011-08-09
nobody?  Maybe I asked the question like a newbie.  If I can clarify anything, please let me know.

Basically, I'm running a script and I need to find the device in an automated way.

---

