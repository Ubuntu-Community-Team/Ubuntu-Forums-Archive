---
title: "Loosing Display"
date: 2010-04-30
forum: General Help
---

### Post by krodrigue on 2010-04-30
Quick question,
 

 After about 30Min my display goes blank even after I set the power options to never, the problem here is I can't get back into the gui without restarting the computer.
 

 I running Ubuntu 10.4 with a Nvidia 7800_OC any advice?

---

### Post by kill4killin on 2010-04-30
Make sure you have the proper drivers installed for your card.
Go to System > Preferences > Screensaver and make sure that both boxes at the bottom are unchecked, both "Active Screensaver..." and "Lock screen..."

See if it still does it after confirming those things.

If it happens again, instead of rebooting, press "Ctrl - Alt - F1" and see if it will goes to TTY1 or if it does not respond. If it goes to TTY1, type
```
sudo service gdm restart
``` and see what happens.

---

### Post by krodrigue on 2010-04-30
Thank you, I will give that a try.  I used the Hardware Drivers program to set the Nvidia Driver so I am guessing that's correct.

---

