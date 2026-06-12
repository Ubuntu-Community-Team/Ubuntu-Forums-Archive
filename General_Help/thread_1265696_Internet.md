---
title: "Internet"
date: 2009-09-13
forum: General Help
---

### Post by HalfCrackedTech on 2009-09-13
OK well I have Installed Ubuntu 9.0.4 on my box and now I am having troubles with the internet.  Everything was fine yesterday and this morning but now I had to log into Vista *shivers* just to get an answer.  


If anyone has any tips or tricks to help me I would love it.

---

### Post by Iowan on 2009-09-13
Is machine getting IP address? (**ifconfig -a**)?

---

### Post by HalfCrackedTech on 2009-09-13
Yes it has one in the task bar where the wired connection is,  it says that it is connected to the internet but when I go to Firefox I have no connection I keep getting Server not found error.

Any help?

---

### Post by Iowan on 2009-09-13
**route -n** should have the address of yoyr router/modem as default gateway.

---

### Post by HalfCrackedTech on 2009-09-13
I am still having this issue and need this resolved soon!! can anyone please help me out?

---

### Post by tgalati4 on 2009-09-13
Reboot the router while in Ubuntu.

Post the output of:

route -n

---

### Post by HalfCrackedTech on 2009-09-13
I fixed the problem.  

Thank you all for the help.

The issue was with a wrapper app that I installed that was bad.

---

