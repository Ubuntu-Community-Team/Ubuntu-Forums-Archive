---
title: "udev, hald and usbmount in 8.04 LTS"
date: 2010-04-02
forum: General Help
---

### Post by droopycom on 2010-04-02
Hi,

I have a ubuntu 8.04 LTS install where removable usb disks do not automount, and do not appear on the desktop or nautilus file browser when inserted.

I tried to track what is happening and, although this seems to be a very common situation, I could not find a solution that worked for me.

I'm very familiar with manual mounting, persomission and such. Not so much with hald, dbus and the desktop stuff.

Here are the results of my investigation:

1) My local user is in the plugdev group.

2) Local user has the "Access external storage automatically" set in the users panel.
 
3) In the "authorization" panel, "mount filesystems from removable drives" is set to "active console:Yes".

4) In gconf-editor, the "media automount" property for nautilus is set.

5) In gconf-editor, the "automount drive" property for gnome-volume-manager is set.
  => It was not set originaly, but this does not seem to change anything if its on or not.

6) pmount works fine when I do it in the console.

7) udev will plug my usb drive partition as /dev/sda1 (or others) BUT it is not set in plugdev group but the disk group.  This probably does not matter since I can use pmount with no problem.

8 ) Using lshal, I can see that the usb disk is there. Also I can see the device being added or removed when I use "lshal --monitor"

9) BUT, I cant see any Dbus event when I use dbus-monitor

10) In the "Computer" folder of Nautilus I do see a "usb device" icon, but if I try to mount it with the "mount" option of the "right-click" menu, nothing happen.

So the problem seems to be that hald does not send the proper messages to nautilus and/or the gnome-volume-manager. 

I took a look at the hal policy files (/etc/hal/fdi/...) but could not figure out what I should be looking for really. I could not find a way to debug them, or see what hal is really doing when it receives the events from udev.

Any idea what could be the problem here or how I could debug that further ?

Thanks

---

### Post by droopycom on 2010-04-02
Extra info:

If I kill the nautilus process (with just "kill $PID"), nautilus will restart automatically and mount the already plugged in usb stick.

But it will not remount it if i unplug it and replug it.

....

---

