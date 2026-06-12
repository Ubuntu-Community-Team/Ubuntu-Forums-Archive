---
title: "Login password not recognized"
date: 2010-04-01
forum: General Help
---

### Post by Sophorus on 2010-04-01
I installed Ubuntu 9.1 (new install on a Dell Precision 340) a few weeks ago and I'm quite happy with it. However, today I was unable to login (after start up), presumably because the password could not be recognized.  To work around this I logged in under another username (who doesn't have admin privileges), opened user settings (System>Administration>Users and Groups), changed my password, rebooted, logged in with my new password, and proceeded to change my password back to what it was.  This was the second time I had to do this. I'm sure that this was not due to an error in typing in the password, but I have no clue what could have caused this.  

Any help on how to troubleshoot this issue would be greatly appreciated.

:)

---

### Post by Sophorus on 2010-04-01
This morning I checked the user.log file and discovered that there seems to be a problem with bonobo

Apr  1 07:48:08 DellPrecision340 bonobo-activation-server: could not associate with desktop session: Failed to connect to socket /tmp/dbus-crfJEcinpA: Connection refused

It also indicates that there is a stale PID file.

---

### Post by Martje_001 on 2010-04-01
Can you login using a TTY? Please press ctrl + alt + F2 to get to a TTY.

You can get back to the GUI by pressing crtl + alt + F8 (or F7, I'm not entirely sure).

---

### Post by Sophorus on 2010-04-01
Yes I can login using TTY. But how to I get back into my gnome desktop?

---

### Post by Martje_001 on 2010-04-01
Press crtl + alt + F5/F6/F7/F8/F9/F10 (one of those).

The fact that you can login on a TTY means it must be a problem with the gnome-desktop like you suspected.

When the problem shows up again, login to a TTY and run:
```
sudo rm /var/log/*.gz
sudo tar -pczf ~/logs.tar.gz /var/log
```
The first command clean old logs and the second command archives all the logs to a .tar.gz (located in your home-folder).

Please post the tar.gz. with the logs here :).

---

