---
title: "iPhone Not Mounting In Ubuntu"
date: 2010-06-28
forum: General Help
---

### Post by tekkidd on 2010-06-28
Hi, I have an iPhone 3G running 3.1.2 and i am having an issue where the iPhone is not mounting. On one computer it manages to mount but does not show any music in Rhythmbox  and i am unable to add any music. On my other computer the thing just flat does not mount. This is what lsusb gives me: 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:000b Microsoft Corp. Natural Keyboard Elite
Bus 002 Device 002: ID 045e:00f6 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 011: ID 05ac:1292 Apple, Inc. iPhone 3G**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The thing used to mount just fine but does not any more

---

### Post by Yarui on 2010-06-28
Can iPods ever be accessed through rhythm box?  I didn't think they could.  I tried testing with my old iPod nano and it's not showing up at all, but it's currently on 'very low battery' so maybe it will show up after it has charged a bit.  Is your iPhone just charging from the USB but not showing up as an attached device in the OS?

EDIT:  After charging a few minutes my iPod did show up and mounts in rhythm box, I never knew that rhythm box could do that.  I suppose I just never thought to try.

---

### Post by aysiu on 2010-06-28
Are you, in fact, using Ubuntu 9.04 (Jaunty Jackalope), as your profile indicates?

If so, I don't believe iPhones *are* supposed to mount.

You'll need to manually install [libimobiledevice](http://www.libimobiledevice.org/), which is included in Ubuntu 10.04 by default.

---

### Post by tekkidd on 2010-06-29
Sorry, apperently fuse became uninstalled for some reason and i just needed to reinstall it

---

