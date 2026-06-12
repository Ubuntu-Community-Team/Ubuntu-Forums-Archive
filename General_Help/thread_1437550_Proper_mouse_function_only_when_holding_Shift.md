---
title: "Proper mouse function only when holding Shift"
date: 2010-03-24
forum: General Help
---

### Post by jkoss on 2010-03-24
Hello,

I just installed Ubuntu 10 as a dual boot with Windows 7. I was using it for a couple of hours (and really liking it) when all of the sudden the Ubuntu Software Center stopped responding and I was unable to click anything.

After logging out of my account I noticed I had proper mouse function. I restarted the system and noticed the same thing happening when I logged into my account.

Basically what has happened is that I have to hold the Shift key down in order to press application buttons, like "OK" and "Cancel".

If I click on a link in firefox nothing happens. I need to hold shift and left click to follow the link, which of course opens the link in a new window.

If I try to right click on the desktop nothing happens unless I hold shift.

I looked through the mouse and keyboard settings and did not notice anything odd.

Does anyone know how or why this could have happened? Or better yet, how to fix it?

Thank you,

jk

---

### Post by jkoss on 2010-03-24
There must have been a keyboard shortcut I pressed to change this. I logged into another account and everything was fine.

I logged out, dropped to the terminal and ran the command:

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

as described here:
[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

It certainly wasn't the ideal way to fix this problem since I had to reconfigure my settings, but it did work. 

If anyone could tell me how to perhaps restore only keyboard/mouse settings that would be very helpful.

Thanks,

jk

---

### Post by jkoss on 2010-03-25
Just wanted to keep this up to date. I'll let it get buried now.

Here was my exact issue:
[https://bugs.launchpad.net/ubuntu/+source/sugar/+bug/479179](https://bugs.launchpad.net/ubuntu/+source/sugar/+bug/479179)

---

