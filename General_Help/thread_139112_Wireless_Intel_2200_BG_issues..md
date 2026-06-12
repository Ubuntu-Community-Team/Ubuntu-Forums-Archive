---
title: "Wireless Intel 2200 BG issues."
date: 2006-03-03
forum: General Help
---

### Post by JGO on 2006-03-03
Was just posting to see if anyone else has come across an issue like this. 

I just got a new Compaq v2000 that has the Intel 2200 BG chipset in it for 802.11 b/g 

I got Ubuntu 5.1 CD's in the mail.

I installed Ubuntu and everything is working suprisingly well. However I cannot get connected to my home WAP.

The wireless chipset seems to be detected just fine, as I can go into the network configuration, activate it and it will draw up a list of access points it has detected.

The problem is that try as I might I have been unable to obtain an ip from my WAP.

I am using 128 bit WEP and do configure it by selecting my WAP from the list and typeing in the WEP key, however after aplying this setting it sits there trying to connect for several minutes then just disapears. At this point an ifconfig reveals I did not recieve an IP from the WAP.

I have checked my WAP to ensure it is not MAC filtering etc... The same machine can connect in Windows just fine. (Dual boot.)

Any help would be appreciated.

Thanks.

---

### Post by JGO on 2006-03-03
Got it figured out. After hours of messing around with Ubuntu I started looking at my router.

For whatever reason ubuntu wouldn't work with the router set to shared key. Changing it to open key resolved the issue.

Thanks.

---

### Post by LauriN on 2006-03-04
hey JGO!

i've got exactly the same problem with my intel 2200bg. where can i change the setting you described above ("changing to open key")?

thanks in advance!

---

