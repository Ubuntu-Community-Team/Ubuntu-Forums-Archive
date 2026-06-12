---
title: "VirtualBox USB Printer"
date: 2009-10-31
forum: General Help
---

### Post by vttay03 on 2009-10-31
I've just completed moving everything over to my fresh install of 9.10 from 9.04.  One of the last things I did was clone my XP virtual machine that was running inside of 9.04 to my VirtualBox setup on 9.10.  Everything went flawlessly and I was able to boot the cloned copy without missing a beat.  However, the one strange thing I've noticed is that the printer is greyed out in the USB devices menu on the bottom right when I fire up the virtual machine.  All of my other USB devices are active and can be passed through from the host OS (Ubuntu 9.10) unlike the printer.  This wasn't the case with my setup in 9.04 - I was able to use my printer inside of the XP virtual machine.  Has anyone else seen this behavior or have any suggestions?  Any help is appreciated.

---

### Post by shadow120 on 2009-11-01
when you get it from add/remove you dont get usb to get usb you have to download form the virtualbox website

---

### Post by vttay03 on 2009-11-01
Yes I know, I added the VirtualBox non-free repository so that I could get USB functionality.  Like I said in the above post, all USB devices are functional in the XP virtual machine BESIDES the printer.  For some reason this device is grayed out and I can't figure out why.

---

### Post by Kerig on 2009-11-02
I have the same issue, which really surprised me.
Interesting that lsusb command doesn't show the printer. Seems like ubuntu doesn't recognize it. However information in /var/log/messages says that printer is connected, but not to the usb port.
Strange, anyway. I've not found a solution yet.

---

### Post by vttay03 on 2009-11-02
I found the solution to this on another thread - see here:

[http://ubuntuforums.org/showthread.php?t=1299512&page=2](http://ubuntuforums.org/showthread.php?t=1299512&page=2)

Hope this helps.

---

### Post by vttay03 on 2009-11-02
I found the solution to this on another thread - see here:

[http://ubuntuforums.org/showthread.php?t=1299512&page=2](http://ubuntuforums.org/showthread.php?t=1299512&page=2)

Hope this helps.

---

