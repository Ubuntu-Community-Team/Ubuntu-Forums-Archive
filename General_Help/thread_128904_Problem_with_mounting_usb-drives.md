---
title: "Problem with mounting usb-drives"
date: 2006-02-12
forum: General Help
---

### Post by Jeff Eklund on 2006-02-12
Hi!
I recently did a clean install of Kubuntu 5.10 on a friends laptop and when we turn the computer on, a usb-drive shows up on the desktop, without any drives being plugged in, and it's impossible to unmount the drive. Whenever we try to mount some other usb-medium like a thumbdrive, the drive is detected but konqueror tells us that it can't recognise the filesystem nor mount it! 
What is causing this? does anyone have any ideas how to solve it?
Thanks! 

Jeff and Friend ;-)

---

### Post by Prospero2006 on 2006-02-12
When you go to System --> Storage Media, what does it show the device
as being? sda1 -- sdb1 ?

When you type umount /dev/sda1 (or whatever) What's the output?

Prospero

---

### Post by Kyle- on 2006-02-12
Hey Jeff and Friend,

Go to Adept or Synaptic and update all your packages.  A bug in KDE caused this problem and has been fixed.  Update and your drive should mount automatically.  

K-

---

### Post by Jeff Eklund on 2006-02-13
Thanks Kyle, it was fixed by updating to KDE 3.5.1. Thanks alot!

---

