---
title: "WiFi worked in 10.10 but not in 11.04!"
date: 2011-05-17
forum: General Help
---

### Post by CoolJohnB on 2011-05-17
In my Dell Vostro 1700 Wifi worked fine with the Propriety Broadcom driver when running 10.10 Maverick, but when I upgraded to 11.04 Natty it stopped working!  On another thread it recommended downloading another driver which I did and disable the propriety driver, it still doesn't work, although when I click on the network icon in the panel wireless is grayed out and it says firmware is missing!

Any suggestions?

Thanks for any help offered.

---

### Post by dargaud on 2011-05-17
I have the same problem: 11.04 borked the wifi on one of my laptops: 4 different wifi cards hardly work anymore (plenty of tries to get a connection, doesn't stay up more than a minute). No solution found yet.

---

### Post by CoolJohnB on 2011-05-17
Looks like going back to 10.10 if there is no solution!

---

### Post by CoolJohnB on 2011-05-18
Thanks to this thread: [http://ubuntuforums.org/showthread.php?t=1756470&page=2](http://ubuntuforums.org/showthread.php?t=1756470&page=2)

which gave this solution: Here's what I did -- It worked on 11.04 but it sounds like it may work for other installs:

- I removed the STA driver from Additional Drivers
- I opened synaptic and installed b43-fwcutter then firmware-b43-installer
- Reboot

It now works fine, Thank You Ubuntu Forums, Your The Best!

---

