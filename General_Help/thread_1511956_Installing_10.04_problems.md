---
title: "Installing 10.04 problems"
date: 2010-06-17
forum: General Help
---

### Post by nemiux on 2010-06-17
I've got the iso file ```
ubuntu-10.04-desktop-i386.iso
``` And I used Unetbootin to write it to flash, and from there, I tried to install it into an empty partition. Everything was all right, when on the last step while installing I've got the message that /cdrom is busy and the setup wasn't able to unmount it, I got choises to either go back or continue. First I've tried to unmount it by writing ```
sudo umount /cdrom
``` But it just notified that /cdrom is busy, and when I clicked continue, I got back to the step 6, where I have to enter my username, password computer name etc.
How could I install it? Maybe I should use something else, not unebootin? If yes what?

Thank you

---

### Post by WinterRain on 2010-06-17
Why not use ubuntu's built in Startup Disk Creator? It's in system>administration.

---

### Post by K.J. on 2010-06-17
I actually just used unetbootin to install Lucid on my netbook.  It should work find.  I would try re-making the boot media or re-downloading the ISO. Also, you can run a verify on the boot media from the boot menu.

---

