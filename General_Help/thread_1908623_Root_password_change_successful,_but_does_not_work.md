---
title: "Root password change successful, but does not work"
date: 2012-01-13
forum: General Help
---

### Post by thunderbird985 on 2012-01-13
Hello,


Here's my current situation.  I have installed Backtrack 5 R1 (which is essentially Ubuntu 10.04 with lots of preloaded packages) onto a 16 GB flash drive, and everything words fine until I change the root password.  I have the Gnome 64-bit edition.  

The default root/toor combination works, and I'm able to load the desktop using startx.  When I log on as root and enter ```
 passwd
```, I am able to change the root password.   I then proceed to restart and login, and the just-changed password does not work.  I will update later today the exact message I am receiving, but I believe it's just an incorrect login attempt.  Please don't suggest I am entering the wrong password..If I can't remember a password 5 minutes later then I shouldn't even be using BT. :D
I am not at my computer now, but the only idea I have now is to make another user account and attempt to change the root password while on another account.  I have checked the /etc/passwd file and the shadow file - Everything looks normal, so I am baffled as to why I am running into such a seemingly-simple error.  Thanks!

---

### Post by marshmallow1304 on 2012-01-14
When you say you've installed Backtrack on the flash drive, have you actually [installed]("http://www.backtrack-linux.org/tutorials/backtrack-hard-drive-install/") it and not just made a [live USB]("http://www.backtrack-linux.org/tutorials/usb-live-install/")?  Live environments made in the latter manner are not persistent across reboots.

However, newer versions of UNetbootin can create persistence files for Ubuntu Live USBs.  I don't know if this will work for Backtrack, but it might since it's based on Ubuntu.

---

