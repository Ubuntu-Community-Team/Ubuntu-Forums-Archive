---
title: "VMWare to VirtualBox Networking Question"
date: 2010-11-01
forum: General Help
---

### Post by Radioman991 on 2010-11-01
Hello:

I have a VMWare XP VM that I need to get going in VBox.  The machine boots and works, but I have no networking.   This machine has installed apps that I need to use, so starting from scratch is not an option.   How can I get networking working again on this machine inside VBox?   Any suggestions appreciated.

Radioman

---

### Post by Wayne_V on 2010-11-01
I would start by checking the virtual machine settings in Virtual Box to make sure a NIC exists and is enabled.

---

### Post by Radioman991 on 2010-11-01
Thanks for the idea   I looked and it appears to be there and enabled.  In the XP VM device manager, it looks like there is no driver for the NIC.   Every time I have attempted to move to VBox, I have had this issue.  I usually just give up, but this is an issue for the apps installed on this machine.

I'll double check again, but it seems like the driver the virtual XP "sees" is incorrect.

-pk

---

### Post by Wayne_V on 2010-11-01
Ah ... Windows ;(

Make sure the Virtual Box Guest Addins are installed and if it still doesn't recognize the NIC try deleting all network hardware and let Windows re-scan.

[http://www.virtualbox.org/manual/ch04.html#additions-windows](http://www.virtualbox.org/manual/ch04.html#additions-windows)

---

