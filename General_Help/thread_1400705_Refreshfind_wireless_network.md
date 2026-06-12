---
title: "Refresh/find wireless network"
date: 2010-02-07
forum: General Help
---

### Post by thor187 on 2010-02-07
I recently changed from an earlier version of ubuntu to 9.10 and the wireless network does not work. It used to work in the older version. When I click on the network icon, it does not show the wireless network.

How do I search for a wireless network in ubuntu/refresh the wireless network?

---

### Post by SecretCode on 2010-02-07
When you right-click on the network manager icon, does it have a entry "Enable Wireless"?

---

### Post by rnerwein on 2010-02-07
hi
you can use iwlist
1. sudo /bin/bash
2. iwlist scan
3. ifup -a ( man ifup )

but if iwlist gives you no output then i think you have to look for a new driver. 
you changed to a newer version - 9.10 - means you also got a new kernel.
much luck
ciao

---

### Post by thor187 on 2010-02-07
Hi,

When I right click, there is no wireless, or anything, it is only showing the option for a wired network. There is a check box saying enable networking, however that is checked.

I tried the above commands, and I recieved a message saying no result turned or something.

---

### Post by SecretCode on 2010-02-07
If you go to System > Administration > Hardware Drivers, are any special drivers suggested?

---

### Post by thor187 on 2010-02-07
Had a look. There are no devices showing.

---

### Post by thor187 on 2010-02-07
When I run live cd, and go to hardware drivers it comes up with the broadcom device. But when I boot normally into Ubuntu, there is nothing in the hardware drivers. Thanks for the help so far though... :)

---

