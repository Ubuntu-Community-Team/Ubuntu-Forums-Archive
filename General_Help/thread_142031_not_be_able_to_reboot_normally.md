---
title: "not be able to reboot normally"
date: 2006-03-09
forum: General Help
---

### Post by youbaji on 2006-03-09
hello,
Every time when I execute "reboot" or "init 6", my ubuntu5.10 outputs the following lines on the screen:
===========================
* Switching to runlevel: 6
* Sending processes the TERM signal
Give root password for maintenance
type (Control-D) to continue:
===========================
I typed C-d, but still have the output:
------------
type (Control-D) to continue:
------------
so, I have to input root password and then quit root.  Now, ubuntu began to reboot.

Someone told me that the sentence:"Give root....." comes from "sulogin".  But I couldn't find any script in "/etc/rc6.d" ever execute the command "sulogin".
What should I do to let ubuntu skipping the annoying "type password..." and directly reboot my computer?
Any advice?

Thank you!

---

### Post by lamego on 2006-03-09
Have you tried "shutdown -ry now" ? Thats the standard reboot command for a unix/linux system...

---

### Post by youbaji on 2006-03-09
Exactly the same result. :(

---

### Post by youbaji on 2006-03-10
finally I found it!
 in file: /etc/inittab:
++++++++++++++++
#l5:5:wait:/etc/init.d/rc 5
#l6:6:wait:/etc/init.d/rc 6  <====here, if I remove the "#", everything works fine!
# Normally not reached, but fallthrough in case of emergency.
z6:6:respawn:/sbin/sulogin  <=======that's where sulogin is called
++++++++++++++++

:mrgreen:

---

