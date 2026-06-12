---
title: "Wireless Issue????"
date: 2010-04-25
forum: General Help
---

### Post by suryaccnamcse on 2010-04-25
I have recently installed Ubuntu 10.04 RC, previously I was using Ubuntu 9.10 and windows 7 as a dual boot.In windows 7 the wireless used to work perfectly. In Ubuntu I am having some problems initially connecting, even sometimes detecting my SSID, but once the SSID is detected it usually connects and works without any issues till I reboot the computer. 
I have tried the backports but that does not work.  I will change the channel of the router and and check if it makes some difference. I was wondering if someone else has faced such issue?

---

### Post by mmalone21 on 2010-04-25
I have not had any wireless issues in 10.04 RC.

---

### Post by suryaccnamcse on 2010-04-25
from lspci -v 
my wireless network card is intel pro/wireless 3945ABG rev 02 which is supported by Ubuntu.
Does someone has some other idea which I can try?

---

### Post by suryaccnamcse on 2010-04-25
I changed the channel on the router to 6 and rebooted the computer again the same issue, the computer connected after some 4-5 minutes of trying to connect to the SSID, I had to give the WEP password 2 times. 
Is there any way we can install the drivers for the network card again, I think the drivers were not installed properly. I tried installing the network drives with the command
sudo apt-get install network driver   but this did not work. 
any other ideas?

---

### Post by suryaccnamcse on 2010-04-26
I downgraded to 9.10 and the internet connects perfectly, Lucid may have some issues to be resolved before the 29th.

---

