---
title: "Screen resolution - keeps reverting to 640X480"
date: 2010-02-10
forum: General Help
---

### Post by willtcomm on 2010-02-10
Hi,

I am test driving Ubuntu 9.04 (Desktop) - the screen resolution always pops up as 800 x 600   - Preference Display tells me there is a different graphics driver (which I have installed) and set to 1280 X 800  which then works till I re-boot.  I changed it in NVIDIA X Server Settings.  When I try to save to X configuration I get a message  "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'."  - which I presume is because I am not in superuser mode -  how do I set up a superuser account (is this even possible?) or is there a nioce simple way for a real newbie to fix this?

Rgds, 

WC.

---

### Post by shriramrs31 on 2010-02-10
in ubuntu, it is not allowed by default to boot into graphical system with the root account. The username you created during install is the root account, you just have to open your programs with sudo(for console apps) / gksudo (for GUI apps) to gain superuser privileges.

---

### Post by shriramrs31 on 2010-02-10
sorry, should have been a little more specific.

try "gksudo nvidia-settings" from console. Hope this helps.

---

### Post by willtcomm on 2010-02-10
Looked promising till I re-booted, ie it did not come up with the error message , and it has changed the xorg.conf file in /etc/x11   but still 800 x 600......

Addenda

At the point where it was saying "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?  - I had been typing yes, I tried NO and then used the 'normal'  settings screen and changed it there, re-booted and it seems now working. Many thanks for the help.

WC

---

