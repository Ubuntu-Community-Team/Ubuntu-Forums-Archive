---
title: "No DSL in Ubuntu 8.04?????"
date: 2009-07-11
forum: General Help
---

### Post by rocket16 on 2009-07-11
Hello to all. I recently installed Ubuntu 8.04, But am finding no way to set up DSL Connection with my external Modem to the Internet. When I right-click the Network Manager, it has the option of only Edit Wireless Connection, but no "Edit Connections" like Ubuntu 9.04. The modem is fine with Windows XP, Vista, Ubuntu 9.04 and Puppy Linux. So, what should I do? I need to download ATI driver for Ubuntu 8.04, and am in a trouble.

---

### Post by kixome on 2009-07-11
actually open network manager in system>administration>network
is wired connection listed? If not 8.04 may not have your network driver.

---

### Post by rocket16 on 2009-07-11
Yes, the Wired Connection is listed. What do I do?

---

### Post by kixome on 2009-07-11
unlock and select it, then click properties, and set it to roaming mode. alternately if you have to set a static ip, and gateway then enter your info in there.

---

### Post by kixome on 2009-07-11
if that doest work open a terminal and post the results of "ifconfig" without the quotes

---

### Post by 3rdalbum on 2009-07-11
I suggested Ubuntu 8.10; it has a recent copy of Network Manager and it also has 3D support for the ATI cards. Assuming you need 3D.

---

