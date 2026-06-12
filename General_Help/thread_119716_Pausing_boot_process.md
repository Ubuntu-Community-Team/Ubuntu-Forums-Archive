---
title: "Pausing boot process?"
date: 2006-01-20
forum: General Help
---

### Post by ajgreeny on 2006-01-20
Is there a way to pause the boot process so that I can see what an error message that comes and goes too quickly really says?

If it takes too long for the network to come up during booting, I loose the boot splash screen and go over to the scrolling text.  This is where I see a message saying something about a file is missing, something to do with freshclam I think, but it all happens so fast I can never read it.

Is there a log file that shows what the scrolling text was at boot?  If so I can just look at that and not bother to pause the system.  Incidentally, is there a way to increase the timeout period for the graphic splash screen on bootup so I don't loose it if the network is slow?

---

### Post by bernardfrancois on 2006-01-24
I think you can press the *Scroll Lock* key on your keyboard.
If you want to have log files about startup messages, I think you can find them in /var/log/messages or /var/log/dmesg (or you can use the dmesg command to see the messages from the latter file as well).

---

