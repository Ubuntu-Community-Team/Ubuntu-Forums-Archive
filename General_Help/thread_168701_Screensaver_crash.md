---
title: "Screensaver crash"
date: 2006-05-01
forum: General Help
---

### Post by ampop on 2006-05-01
Some times my screensaver crashes and I must switch off my PC.
Any solution for this problem, thanks.

---

### Post by Zorro on 2006-05-01
I have a similar issue.. What video card you using? and Drivers?


Im about to try a reinstall and see if it still does it.. :(

---

### Post by ampop on 2006-05-01
[QUOTE=Zorro]I have a similar issue.. What video card you using? and Drivers?


Im about to try a reinstall and see if it still does it.. :([/QUOTE]

The video card it's a SIS (silicon integrated system), it's a PCI/AGP VGA Display.
About the driver. I dont't know because I didn't install any driver, it's installed by default.
I'm using a notebook.
Thanks.

---

### Post by ender42 on 2007-09-26
I *HAD* a similiar issue here, fixed now.

Did you guys swap out to xscreensaver?  The default gnome screensaver is buggy.

[http://ubuntuforums.org/showpost.php?p=2989368&postcount=3](http://ubuntuforums.org/showpost.php?p=2989368&postcount=3)

But, I still have an issue with it (just a lot less issues).  Typically my web-browser crashes a lot, right now I'm reduced to using Galeon...  Anyways, I got thru the lock-screen, just in time to see galeon crash.  Then my screensaver quit working.

I tried clicking on the panel-screen icon on the top tool bar (the standard way to start it).  No dice.

I tried the activate screensaver from that icon, no luck.

I tried letting it time out (3 hours and no screensaver), so that's not working.

I'd thought I'd tried running it from the command-line (you can't run as root, by default - insecure), but obviously I had not:

user@machine: ~$ xscreensaver
xscreensaver-demo: 10:09:39: error closing "/home/user/.xscreensaver": No space left on device
xscreensaver-demo: too early for dialog?
xscreensaver-demo: 10:09:43: error closing "/home/user/.xscreensaver": No space left on device
xscreensaver-demo: 10:10:00: error closing "/home/user/.xscreensaver": No space left on device


Checked, and sure enough my home was chock-full.

Cleaned out a little space, and it was working from the panel icon.  My issue is solved :D

Half-solved.  The panel icon only works while I've got xscreensaver running in terminal.  I wonder if I background it, and then kill the terminal associated with it, if it'll still work....

---

