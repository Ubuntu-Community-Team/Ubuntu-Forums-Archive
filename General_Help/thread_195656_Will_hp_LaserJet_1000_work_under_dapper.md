---
title: "Will hp LaserJet 1000 work under dapper?"
date: 2006-06-13
forum: General Help
---

### Post by 3str on 2006-06-13
I knew that hp LaserJet 1000 has some anonying thing to get it work. I've followed the HOW-TOs to get to run under breezy. Will it work under dapper too?

---

### Post by The Mekon on 2006-06-13
I can't see why not.  There are Laserjet 1000 drivers include in my Dapper istallation.

---

### Post by paulmilliken on 2006-06-13
[QUOTE=The Mekon]I can't see why not.  There are Laserjet 1000 drivers include in my Dapper istallation.[/QUOTE]

I was not able to get my HP laserjet 1000 to work under Dapper.  However, it does work in previous versions of Ubuntu by following the instructions in [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/).  Hopefully someone will be able to resolve this issue soon as I had hoped Dapper would have improved hardware support over Breezy...

Paul

---

### Post by 3str on 2006-06-14
Yes, this is what I truely mean. LaserJet 1000 needs an upload of driver image to it at every boot. In breezy, there is a hot-plug script to this automatically. But in dapper, hot-plug is replaced with udev. So maybe we need a new udev script to help us.

---

### Post by paulmilliken on 2006-06-19
I have got my hp laserjet 1000 to work under Dapper.  I have written a howto but it hasn't been posted yet.  When the howto is posted it will look like this:

The HP laserjet 1000 printer does not work "out of the box" with Dapper Drake at the time of writing. Furthermore, the instructions on [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/), which work under Hoary and Warty, do not work without some modification. This Howto describes the required modifications.

1. Follow the instructions on [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) to download the firmware and drivers for your printer and to install the drivers.
2. As root, edit the file /etc/cups/printers.conf and find the line starting with "DeviceURI". Now edit this line such that it reads:
"DeviceURI file:///dev/usb/lp0"
3. Now restart cups by typing: "sudo /etc/init.d/cupsys restart" at the command line. (Thanks to the posters at [https://launchpad.net/distros/ubuntu...sys/+bug/43824](https://launchpad.net/distros/ubuntu...sys/+bug/43824) for steps 2 and 3).
4. Now try printing a page

There is a link on [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) where you can donate money to the author of the driver. If you are able, I'm sure he/she will appreciate it.

---

