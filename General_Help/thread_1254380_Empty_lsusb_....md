---
title: "Empty lsusb ..."
date: 2009-08-31
forum: General Help
---

### Post by szczym on 2009-08-31
helo

i have strange problem: lsusb gives me nothing. it use to work normally, then i few time connected digital camera and now it lists notging (and gphoto can`t find any camera). I have 2 devices turned into hardy server, dmesg lists usb events when i plug in or out...

i use ubuntu 8.04.3 server.

thanx for help

---

### Post by hal10000 on 2009-08-31
Can you plug in another usb device, e.g. an usb stick, harddisk or something else, to verify wether it's  the camera or if (worst case) your whole usb subsystem is damaged?

Have you tried to reboot?

---

### Post by szczym on 2009-08-31
I did reboot and shout down many times, no change. Also tested jaunty desktop on the box - lsusb works on it fine.

---

### Post by hal10000 on 2009-08-31
Can you test the camera on another System (e.g. Windows), probably on another PC or notebook to see if it works there. If not, then maybe your camera has a hardware damage.

It's strange, because you say that it worked earlier.

---

### Post by szczym on 2009-08-31
It works on other machines, and on machine where the problem is, but on other operating system (jaunty)

---

