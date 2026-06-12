---
title: "ubuntu crashes after system resume or shortly afterwards"
date: 2011-08-11
forum: General Help
---

### Post by princeofnam on 2011-08-11
Since installing ubuntu on my hp g7-1070us laptop I've noticed that it will inconsistently crash after I suspend it or shortly afterwards.  I can't even ctrl+alt+f1 into a different terminal to reboot.  Does anyone know how I can diagnose my problem or have a guess as to what it could be?

---

### Post by Toz on 2011-08-11
How often is "inconsistent"?

After a crash, when you resume control of the system, post back the contents of **/var/log/pm-suspend.log** and **/var/log/syslog**.

And also, open a terminal window, type in the following commands and post back the results:
[code]
cat /var/log/dmesg | grep "PM:"
cat /var/log/dmesg.0 | grep "PM:"
/code]

---

### Post by princeofnam on 2011-08-19
i don't know why but the forum won't be paste the code here.  Something about there being too many photos embedded despite me only pasting text.  Can I email it to you somehow?

---

### Post by Toz on 2011-08-19
Try this:
Click on the reply icon then on "Go Advanced". When in advanced mode, click on the "#" button to display code tags. Paste the results inside those code tags.

---

