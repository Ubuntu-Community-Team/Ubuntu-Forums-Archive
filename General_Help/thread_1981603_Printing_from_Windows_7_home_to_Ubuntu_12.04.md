---
title: "Printing from Windows 7 home to Ubuntu 12.04"
date: 2012-05-17
forum: General Help
---

### Post by jcisneros1 on 2012-05-17
I know that there is a solution out there. I am just too tired to keep looking for it.
My desktop system is running Ubuntu 12.04 and does have SAMBA installed. I have two printers installed on the machine, one through the usb and the other via the parallel port. What I want if to be able to print from my laptop which is running windows 7 home (64). How do I configure and get Windows to see the printers and access them?

Thanks.

---

### Post by florus on 2012-05-17
Have you installed the printers as network printers in Windows 7 ?

---

### Post by Morbius1 on 2012-05-17
If you are using 12.04 and attempting to reach the Linux printer from Windows using Samba you are probably out of luck. At the moment something is broken in the way samba and cups communicate with each other in 12.04: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410)

[COLOR=Blue]*The bug report is "Confirmed", "High Importance", but "Unassigned" which always makes me feel hopeful :rolleyes:*[/COLOR]

The solution is to bypass samba and connect to CUPS directly from Windows as described in post #18: [http://ubuntuforums.org/showthread.php?t=1971847](http://ubuntuforums.org/showthread.php?t=1971847)

---

