---
title: "Very strange problem"
date: 2011-06-10
forum: General Help
---

### Post by membrano on 2011-06-10
Hi friends,
I use Ubuntu 10.04 LTE in my HP Pavilion tx2000.

My daugther (18 months) sat in front of my laptop and started to touch the keyboard and trackpad, for 2 minutes or so. When I saw her she stopped, but it was too late: keyboard isn't working, the trackpad doesn't work either. The displayed window didn't change, Firefox was still working. The touchscreen works.

I could only reboot my laptop by pressing for 5 secs the power button.

When I got the login screen I could click my user and enter my password, but once my session opened, the problem reappeared. I connected a USB mouse and it worked, but I couldn't unfold system menus: they highlight but they don't show any option (!?)

Now I'm writing from root user, and it all works fine. It looks like some user configuration is gone. For example, xorg.conf is missing, but I'm not sure that's the problem. I do not know how to restore the file either.

Any suggestions?

Thank you!!!

----------------------

I closed root session and opened a session with my user, without rebooting, and the problem is solved!

---

### Post by monkotronic on 2011-06-10
since god alone knows the magical input of your child; i cant tell you what is missing.  if it were me, i would set up a new user account and move into it from my old one.  only copy over your own files and not the systems (except for ones you might know you want).  the other option is to create the new account, change everything in it to be owned by your old account using the chown command and then copy them to your broken account directory and replace all of the old system files.

quirky, but only what i could think of.

---

### Post by linuxinstalledfromhdd on 2011-06-10
> **membrano said:**
> Hi friends,
I use Ubuntu 10.04 LTE in my HP Pavilion tx2000.

My daugther (18 months) sat in front of my laptop and started to touch the keyboard and trackpad, for 2 minutes or so. When I saw her she stopped, but it was too late: keyboard isn't working, the trackpad doesn't work either. The displayed window didn't change, Firefox was still working. The touchscreen works.

I could only reboot my laptop by pressing for 5 secs the power button.

When I got the login screen I could click my user and enter my password, but once my session opened, the problem reappeared. I connected a USB mouse and it worked, but I couldn't unfold system menus: they highlight but they don't show any option (!?)

Now I'm writing from root user, and it all works fine. It looks like some user configuration is gone. For example, xorg.conf is missing, but I'm not sure that's the problem. I do not know how to restore the file either.

Any suggestions?

Thank you!!!

----------------------

I closed root session and opened a session with my user, without rebooting, and the problem is solved!

Create a new user. Google it to learn how. That should reset your settings for the new user created..

If that doesn't work you may need to reinstall:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

