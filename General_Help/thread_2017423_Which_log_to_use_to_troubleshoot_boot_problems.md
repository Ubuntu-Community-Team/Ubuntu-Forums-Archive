---
title: "Which log to use to troubleshoot boot problems"
date: 2012-07-05
forum: General Help
---

### Post by wpshooter on 2012-07-05
I just had my computer freeze on the Ubuntu 11.04 screen that has the purple background and the little 4 dots on it.

When I hit ALT-CRL-DEL to reboot the machine, it shows a bunch of text lines which I suspect will give some info as to what the problem was, but the machine reboots so fast that I have no chance to see what all of the text says.

Which LOG file(s) will give me that info so I can post so someone that is knowledgeable about these boot files records can determine what the problem(s) may be.

P.S. - I have these problems with the computer hanging during the boot process on maybe 1 out of 300 or 400 boots.

Thanks.

---

### Post by dino99 on 2012-07-05
the main log is inside your /home : .xsession-errors (ctrl+h to unhide it)
and into /var/log/

---

### Post by wpshooter on 2012-07-05
> **dino99 said:**
> the main log is inside your /home : .xsession-errors (ctrl+h to unhide it)
and into /var/log/

When I first attempted to go into .xsession-error, I could see the contents of it (although, what was in it meant nothing to me).

But now I can not (after shutting down computer to do something else and coming back home and starting the computer again) even get the .xsession-error to open, I get this attached.

There is also a .xsession-error.old.  What is that for ?

Thanks.

---

