---
title: "Printing problem"
date: 2011-06-02
forum: General Help
---

### Post by duncan503 on 2011-06-02
Hi now this is strange guys, every time I print a page, my PC slow down so much that I have to restart it. What is wrong with that?

Ubuntu 10.04 : Printer HP laserjet 1100

Thx for the reply

---

### Post by seawolf167 on 2011-06-02
Can you take a look and see what is eating up the CPU?

I recommend using *htop*

```
sudo apt-get install htop
```then open a terminal, start htop (by typing *htop* into the terminal), print a page and see what process is using all your cpu. Then report back here and let us know what the process is.

---

### Post by duncan503 on 2011-06-02
Well there it is a screen shot of the problem. Hope this help Thanks.

---

### Post by seawolf167 on 2011-06-02
> **duncan503 said:**
> Well there it is a screen shot of the problem. Hope this help Thanks.

Sorry, but can you do this one more time, and instead of selecting a service by left-clicking, leave the window free so it floats and shows the highest CPU% at the top? That way we can see the culprit process.

---

