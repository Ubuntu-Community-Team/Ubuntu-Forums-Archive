---
title: "LiveUSB questions (Conky/fstab/user accounts)"
date: 2009-08-07
forum: General Help
---

### Post by Steelangel on 2009-08-07
I've been playing around with installing the Ubuntu liveCD onto a USB stick so that I can have a portable OS with me. While I have gotten most of my applications working, I have bumped into some problems that the internet has failed to help me with. 

1) Conky simply stops updating. It will run for approximately 4 minutes and then stop. It doesn't throw out an error either. I have not ever had this occur with conky installed on any other box; and the .conkyrc file is a copy from another box.

2) I would like to be able to automount the hard drive /dev/sda1 to /media/drive when I boot the computer from the usb stick. One would think that adding a line to my fstab would work, but unfortuately the fstab file gets rewritten with every reboot. How do I make it persistent?

3) The automatic liveuser ubuntu seems to magically appear on my system even though I have userdel'd it, removed its user directory, scoured passwd and shadow to remove any trace of its existance. On boot, tty2, tty3, tty4, tty5, and tty6 are all logged in by this phantom liveuser. ps claims that the login processes belong to root. I would very much prefer to have a secure system, but I can't find any way to stop the autologins. 

Any input would be appreciated :)

---

