---
title: "Freezing at random"
date: 2009-10-03
forum: General Help
---

### Post by h_howee on 2009-10-03
My laptop has been freezing a lot since I've installed Ubuntu, requiring a hard shut down each time. It seems to only happen when I have an ethernet cord plugged in and when it freezes, the caps lock light blinks. It also froze once without the ethernet cord in and the caps lock light not blinking, but that was probably caused by something else.

I'm using the 64-bit Ubuntu 9.04
HP HDX-16 laptop

Any help would be greatly appreciated.

---

### Post by dummy910 on 2009-10-03
1st thing i would do is boot that machine(no network cable plugged into your nic) into Ubuntu **Recovery Mode** from your Grub loader, and then copy-paste the following into a terminal once you get to a desktop.
```
gnome-system-log
```
Check your logs to see what could be causing the crash.

Make sure all your software-drivers are up to date as well. 

Keep us posted.

---

### Post by h_howee on 2009-10-03
I considered looking through the log, but there are so many of them and I don't know which one I can find the problem in. I was hoping to get an answer for that at the very least so that I can Google.
This is a little off topic, but if someone can tell me which log contains messages related to the keyboard on boot-up, that could be helpful too since I have [another problem]("http://ubuntuforums.org/showthread.php?t=1248103") that I still haven't solved.

How do I check if my drivers are up to date? I'm sure my graphics driver is the latest one, but I don't know where to find the rest.

---

