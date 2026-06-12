---
title: "Cannot log on"
date: 2010-08-22
forum: General Help
---

### Post by andpal222 on 2010-08-22
Hi,

I am recently having problems with my Ubuntu 10.04 partition and i know someone from this great community can help me. Here is the situation: One day when i turned on my computer, Ubuntu 10.04 got stuck on the loading splash screen (the screen with the words ubuntu and the 4 or 5 dots). Well, all of the dots turned orange, and the startup noise played, but then the OS didn't boot anything from then. It was just stuck on that screen. I went into recovery mode and update grub but without luck. 

Please, Any help would be appreciated, i'm suffering on windows right now haha...

---

### Post by Rubi1200 on 2010-08-23
Hi,
what graphics card do you have installed and how much RAM does the system have?

Have you recently upgraded or updated anything on the system?

---

### Post by andpal222 on 2010-08-23
Its a very old computer (that's why i put ubuntu on it, windows just goes so slow on it). It has a mobile intel 915GM express chipset and 504 mb of ram.I think I did a update for my programs (sorry, forgot what that's officially called haha).

---

### Post by Rubi1200 on 2010-08-23
When you boot the computer start hitting the Shift button to bring up the GRUB menu.

Then "e" to edit the entry and look for the line which ends
```
ro quiet splash
```Remove quiet splash and put i915.modeset=1 instead so it looks like this```
 ro i915.modeset=1
```  then "Ctrl+x" to boot.

If you get in then we can talk about a more permanent solution.

With those specs. you may want to consider a 'lighter' option such as Xubuntu or Lubuntu.

---

### Post by andpal222 on 2010-08-29
OK,

I tried that and it did not work. After Ctrl+X rebooting several lines of code ran down but it stayed on one: "setting sensor limits     [OK]" for a long time and did not do anything beyond that. 

I might try xubuntu but the truth is that Ubuntu on this particular computer runs well, and meets my expectations

---

