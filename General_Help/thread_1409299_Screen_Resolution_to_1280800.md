---
title: "Screen Resolution to 1280*800"
date: 2010-02-17
forum: General Help
---

### Post by Jkwc on 2010-02-17
How can it be done I searched forums and entered:

sudo gedit /etc/X11/xorg.conf

But it comes up with a blank file? Help

---

### Post by houseworkshy on 2010-02-17
First pop sysinfo in "sudo apt-get install sysinfo".  Run it either from the terminal or from the gui link which will have been placed in Applications>System tools.  If you then use sysinfo to save a file and post the results this will help others to help you because this looks like the hardware drivers will be relevant.  It is also worth reading up on grub 2 as it doesn't work in the same way as grub legacy.

---

### Post by Jkwc on 2010-02-17
> **houseworkshy said:**
> First pop sysinfo in "sudo apt-get install sysinfo".  Run it either from the terminal or from the gui link which will have been placed in Applications>System tools.  If you then use sysinfo to save a file and post the results this will help others to help you because this looks like the hardware drivers will be relevant.  It is also worth reading up on grub 2 as it doesn't work in the same way as grub legacy.
Thanks just tried and it works!

---

### Post by houseworkshy on 2010-02-17
Good to hear that.  The changes to grub foxed a lot of people ( including me ).

---

