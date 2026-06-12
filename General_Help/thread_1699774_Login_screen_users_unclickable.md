---
title: "Login screen users unclickable"
date: 2011-03-04
forum: General Help
---

### Post by Grozzy on 2011-03-04
Gday!
I'm running Ubuntu 10.10 and I did login automatically before, but then I did get a lot of trouble with keyrings etc. so I decided to disable automatically login. When I did that and restarted I got the login screen with my username listed. Now when I try to click on my username I hear a "bop" sound and nothing happens. I'm stuck at the login screen and I can't do anything, well, I can login using the terminal but when I try to start X I still get the login screen.

I hope this is a easy fix and I'm glad for help!

---

### Post by asdir on 2011-03-04
Maybe I'm thinking too simple here, but have you tried choosing your account by simply pressing enter (and if it's the wrong account using the cursor-keys)?

---

### Post by Grozzy on 2011-03-04
Yes I've tried that, it moves a little and plays the "bop" sound, then everything is the same. I managed to log in by editing  "/etc/init/tty1.conf" and adding this line to the end:
exec /bin/login -f USERNAME < /dev/tty1 > /dev/tty1 2>&1
Then when I rebooted it automatically logged me in and I could start the gui by typing startx, but I still need to unlock a lot of keyrings and I can't start gdmsettings (Login Screen application, where I messed up stuff in the first place).

I need to figure out how I can enable auto login from terminal.

---

### Post by Grozzy on 2011-03-04
I managed to solve it by removing "@include common-pamkeyring" from the file /etc/pam.d/gdm.
Now when I reboot I can click on my user and it works!

---

