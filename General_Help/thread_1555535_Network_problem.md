---
title: "Network problem"
date: 2010-08-18
forum: General Help
---

### Post by luckyking8 on 2010-08-18
i am not able to use Net of Ubuntu.... some one can tell me how can i use it.... its required Manually configuration..... which i dont know... please help me):P

---

### Post by efflandt on 2010-08-18
What kind of network connection, wired (ethernet), wireless, dial up, DSL (pppoe), mobile data?

It may help get a better answer if you post the output of **sudo lspci -v** related to it (or **sudo lsusb -v** if USB, or **sudo lshw**).

To keep pasted text formatted, put code tags around it by highlighting it and clicking on the **#** symbol at the top of the Message window.

It is easiest to install/activate a wireless driver if you have a temporary wired connection by going to System > Administration > Hardware Drivers (or whatever that is in your native language).

Otherwise if you have no networking at all, you may need to insert an Ubuntu install CD for your version and add that as a repository in Synaptic (by checking the box to add the CD).  Then try to use System > Administration > Hardware Drivers.

---

