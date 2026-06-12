---
title: "ttl display problem"
date: 2011-06-04
forum: General Help
---

### Post by ender8282 on 2011-06-04
I am having problems with my ttl sessions.  I am running kubuntu and when I log in graphically everything is fine and the screen displays properly (1920x1080) but when I switch to a ttl session the screen isn't displaying properly.  Specifically it looks like the screen is split in half vertically with the same image being displayed on the right and left halves.  I can't make out the text but it does appear to update properly when I type something in (like username and password).  I see a similar display problem with the kubuntu splash screen at bootup and shutdown.  

I don't know if it is related but I have set up grub2 to display at 1920x1080 and that works properly.  I am running an up to date kubuntu 10.04.2 on a Thinkpad w510 with the preemptive kernel.

---

### Post by ender8282 on 2011-06-04
Never mind I found it myself.  It looks like around the same time that I set up grub to use a different resolution I also added the option vga=xxx to my grub boot command.  This was causing the problem.  After removing it the TTLs display properly but at a relatively small resolution.

---

