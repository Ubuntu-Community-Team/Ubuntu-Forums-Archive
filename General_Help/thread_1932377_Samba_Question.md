---
title: "Samba Question"
date: 2012-02-27
forum: General Help
---

### Post by i3design on 2012-02-27
Hi,

I had Samba successfully installed on my Ubuntu 11.10 server. I installed samba as an option when I installed Ubuntu, and then altered my settings by right clicking on the folder and using the share option. I actually had this working successfully, and mapped the two drives to my windows PC. 

The other day I had to restart my server and unfortunately I can no longer access the harddrives. I believe the message states it can no longer locate the drives, invalid address or similar error on my windows PC.

After checking on my server, I can see that the harddrives were mounted, and when rightclicking the drives are still set to “share”. On top of this there is a valid internet connection and it is still on the same network.

So…what gives?! How can I start to diagnose why these drives arnt being shared over the network.

James

---

### Post by wyliecoyoteuk on 2012-02-27
Did the server get a new IP address when you rebooted it?
Might take a while to refresh the DNS.
Try pinging the name from the Windows box, and compare the response to the IP address of the server..

---

