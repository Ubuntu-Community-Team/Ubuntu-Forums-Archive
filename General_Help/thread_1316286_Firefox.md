---
title: "Firefox"
date: 2009-11-05
forum: General Help
---

### Post by anw0625 on 2009-11-05
Why is firefox asking me to force quite every time I close it?  Thanks!!

---

### Post by ram2500 on 2009-11-05
It is likely asking you to force quit because if you try to exit a program too many times, it may think that the process is being unresponsive. Your system might be busy (too many resources) - try killing processes that hog up memory.

---

### Post by anw0625 on 2009-11-05
like what.  It asked for some updates the other day and I did the updates and it started this.

---

### Post by alphacrucis2 on 2009-11-05
> **anw0625 said:**
> Why is firefox asking me to force quite every time I close it?  Thanks!!

I have noticed this with FF3.5 under both Jaunty and Karmic. It seems that it becomes non responsive for long enough during close down that the system thinks that it has hung up and so displays the notification. You don't actually have to click the Force Quit just click WAIT will do as the closedown FF3.5 does proceed normally.

---

### Post by lovinglinux on 2009-11-05
> **anw0625 said:**
> like what.  It asked for some updates the other day and I did the updates and it started this.

It could be some database activity performed by some extension on unload, then optimizing your databases would fix this. To do that, see the Database Optimization section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

