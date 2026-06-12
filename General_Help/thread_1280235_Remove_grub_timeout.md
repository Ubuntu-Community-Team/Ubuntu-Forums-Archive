---
title: "Remove grub timeout"
date: 2009-10-01
forum: General Help
---

### Post by MaaaTtY on 2009-10-01
Hey i would like to know how to safely remove the grub timeout, which is set to 10 seconds by default.  i saw somewhere someone else had tried setting it to "0" which i was inclined to do but this really just sets it to 0 seconds and doesnt give you a chance to choose.  should i just delete the "timeout" line completely?

---

### Post by undecim on 2009-10-01
Open /boot/grub/menu.lst as root (alt+f2, then type "gksu gedit /boot/grub/menu.lst")

Find the line "timeout    10" and change it to "timeout    0"

Save the file, and you're done

---

### Post by mechro on 2009-10-01
If you're looking to have an unlimited timeout then I understand Grub prefers you to hash out the line rather than set it to 0.

i.e. in grub/menu.lst

change...

timeout *x*

to read...

# timeout *x*

---

### Post by sopadeajo on 2009-10-01
You can download Startup Manager and mark: use timeout in bootloader menu.
If you unmark it then the time will not be 0 seconds but rather infinite seconds.It waits till you press enter key.

---

### Post by wilee-nilee on 2009-10-01
> **sopadeajo said:**
> You can download Startup Manager and mark: use timeout in bootloader menu.
If you unmark it then the time will not be 0 seconds but rather infinite seconds.It waits till you press enter key.

 Startup manager is a great tool.

---

### Post by sopadeajo on 2009-10-01
> **wilee-nilee said:**
> Startup manager is a great tool.

Not so great, but anyway i still do not know a different way to act on boot menu

---

### Post by wilee-nilee on 2009-10-02
> **sopadeajo said:**
> Not so great, but anyway i still do not know a different way to act on boot menu

 I like startup manager mainly due to it will rewrite the grub menu if you have a dualboot for the default startup, but hey we all have our own likes. I believe that the grub menu itself can be modified for the wait time.

---

### Post by Minsky on 2009-10-02
Changing the Timeout value to -1 worked for me.

---

### Post by MaaaTtY on 2009-10-02
thanks everyone, works great!

---

