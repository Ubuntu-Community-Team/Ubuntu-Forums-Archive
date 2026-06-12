---
title: "Problem with my netbook after a recovery mode"
date: 2010-12-27
forum: General Help
---

### Post by uzumakiz on 2010-12-27
Hello everyone!

I'm a french user of ubutu, so excuse me for my bad english.

 I think I have enough trouble with my installation. I did a recovery mode because I forgot my password and since it is a catastrophe!

 My netbook gives me the following information when he starting :

```
mount : mounting /dev on /root/dev failed : No such file or directory
mount : mounting /sys on /root/sys failed : No such file or directory 
mount : mounting /proc on /root/proc failed : No such file or directory 
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootrag.


BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initframs)
```When I try to reinstall, the usb live loads and when i want to start the installation, there is a bug, it seems that it loads but it does not start the installation (I've let a whole afternoon and installation has never launched)
Anyway I do not know how to do. If you already met this kind of problem I'm interested in your solutions.

Thank you in advance and happy holidays to all!

---

### Post by dcstar on 2010-12-27
> **uzumakiz said:**
> 
..........
When I try to reinstall, the usb live loads and when i want to start the installation, there is a bug, it seems that it loads but it does not start the installation (I've let a whole afternoon and installation has never launched)
Anyway I do not know how to do. If you already met this kind of problem I'm interested in your solutions.


It looks like there is a partial installation on your netbook which is confusing the install process.

Boot off the USB and use** gparted** to manually delete the existing Linux partition already on the netbook, then start the install process again.

Look at other posts on setting up a separate /home partiton so if you have to do future reinstalls all your existing user data will be preserved.

---

### Post by uzumakiz on 2010-12-28
Thank you for the answer, i will try to do that. I will keep you informed.

Thank you mery much !

---

### Post by uzumakiz on 2010-12-28
Thank you again ! It works ! 

I erase all and reinstall and now it good !

---

