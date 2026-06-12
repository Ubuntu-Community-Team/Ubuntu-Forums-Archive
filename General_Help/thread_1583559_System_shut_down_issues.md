---
title: "System shut down issues"
date: 2010-09-28
forum: General Help
---

### Post by thundaraptor on 2010-09-28
Can someone direct me to a knowledge source that details why my system has a hard time shutting itself down?  It tends to hang a bunch and I have to give it a hard shutdown to get the power and fan to cease... I am sure that is indicative of something not good.  Help?  Thanks.  

Im running Lynx on AMD 64 build up.

---

### Post by andrewthomas on 2010-09-28
What does it say in the logs?

Does it shutdown better using 

```
sudo shutdown -h now
``` from the terminal?

---

### Post by thundaraptor on 2010-09-28
I'm not really bright enough to know what log to check.  Would that be a sys log?

---

### Post by envygeeks on 2010-09-28
edit /etc/default/grub

```

vim.tiny /etc/default/grub

```

Change: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
To: GRUB_CMDLINE_LINUX_DEFAULT=""

This will show you the old skool terminal messages as it goes down. They're also in: /var/log/messages & /var/log/dmesg

You can also change the grub config to: GRUB_CMDLINE_LINUX_DEFAULT="acpi=off"
Or you can also try this first: GRUB_CMDLINE_LINUX_DEFAULT="acpi=force"

After you get some more information from reading the logs and viewing the terminal as it goes down come back and hit us up.

---

### Post by thundaraptor on 2010-09-28
I'm looking at the /var/log/messages file.  It is quite a bunch of information I don't really understand.  Anything in particular I could focus on?

---

### Post by andrewthomas on 2010-09-28
search for this line

```
kernel: Kernel logging (proc) stopped
```look at the time and compare it to the lines just above it

are there any messages within a couple of seconds?

If so, what do they say?

---

