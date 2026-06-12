---
title: "Ubuntu 12.04 New Install Doesn't &quot;Shut Down&quot;"
date: 2012-09-24
forum: General Help
---

### Post by craig10x on 2012-09-24
Hi!  I just recently installed ubuntu 12.04.1 (64 bit)
and it is running fine except for one rather annoying problem...

If i hit the "Shut Down" button it simply restarts instead of actually shutting down, and the only way i can actually shut down is to do a forced shut down with my computer's power button (this is on AC power by the way)...

Any suggestions and ideas would be appreciated...any easy way to correct this?  Is this a common bug with this?

Thanks ;)

---

### Post by craig10x on 2012-09-24
No one here ever experienced this problem?

---

### Post by daslinkard on 2012-09-24
Try this first...

```
1. sudo gedit /etc/default/grub
```
```
  2. Find the line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 
``````
3. Change this to: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
```
```
  4. Save the file and close the file.  5. Finally, in terminal: sudo update-grub

```

Let me know if this solves this for you....

---

### Post by craig10x on 2012-09-26
Thanks for the suggestion...appreciate the help...

I haven't tried it yet (was trying some other things that didn't work) but i was just wondering, if i try this, it wouldn't have any permanent effect on my computer's bios settings, would it?  

Does this only affect my ubuntu install?  What is this supposed to do?
And, it wouldn't change the power management settings would it?
(just wondering...guess i am the "cautious type" lol)...

---

### Post by daslinkard on 2012-09-26
This is going to affect the grub and is not going to affect the bios....in essence it is telling your hardware how to respond.

---

