---
title: "Frozen login screen and or non working trackball, touchpad 11.04"
date: 2012-04-22
forum: General Help
---

### Post by surfcast23 on 2012-04-22
I just up graded to 11.04 from 10.10. When I go to log in I get a message regarding the mouse being captured. I click capture and try to log in, but I cannot move the pointer in the Ubuntu environment. Once I un-capture the mouse it works fine in the windows environment.I am unsure if the problem is with the mouse/touchpad being captured or if Ubuntu is freezing. I am at a loss as to how to diagnose the problem and any help would be appreciated. BTW I have read threads with similar problems, but I have not been able to log in and modify the setting since the upgrade.

Ubuntu 11.04 running as a virtual machine in VirtualBox 4.1.12 on a windows xp host Lenovo Thinkpad T60.

---

### Post by surfcast23 on 2012-04-23
Bump

---

### Post by surfcast23 on 2012-04-24
I have read about command line fixes in recovery mode. When I go to recovery mode I am given several options. I have tried run in failsafe graphic mode with no response. Should I run in NetRoot?
I have also tried this with no luck

Here's the fix:

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.nopnp"
2. Run: sudo update-grub
3. Reboot.

---

### Post by surfcast23 on 2012-04-24
Also tried 
[http://blog.kasunbg.org/2010/05/fix-for-ubuntu-lucid-touchpad-not.html](http://blog.kasunbg.org/2010/05/fix-for-ubuntu-lucid-touchpad-not.html)
 
and again nothing.

I also get this error on boot up

[SIZE=3]could not write bytes: Broken pipe[/SIZE]

---

### Post by surfcast23 on 2012-04-25
No one has any ideas????

---

### Post by surfcast23 on 2012-05-09
bump

---

