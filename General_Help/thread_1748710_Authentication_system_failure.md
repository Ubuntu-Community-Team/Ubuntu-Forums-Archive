---
title: "Authentication system failure"
date: 2011-05-03
forum: General Help
---

### Post by cliftonbazaar on 2011-05-03
Every now and then (Don't know how I do it) the computer stops what it is doing and goes to a screen that looks like a log in screen, when I click on the username it says
> Error initiating conversation with Authentication system - General failure
and that's it, I can't do anything unless I reboot the computer :(

How do I allow this to enter a password and continue on with what I am doing?

---

### Post by spikoley on 2011-05-06
Check the log files for errors.  You can find them under /var/log/.  Look at the syslog and dmesg for that error message and then post the errors around it.

---

### Post by Rubi1200 on 2011-05-06
Did you make any changes recently to this file?
>  /etc/pam.d/gdm

---

