---
title: "ath0 not found after iwconfig command even i have got broadcom wireless card"
date: 2011-08-20
forum: General Help
---

### Post by muhammed irshad on 2011-08-20
I have installed SATA driver recently...Even if i can use wifi but i could'nt find any ath0 interface in ifconfig or iwconfig commands....My wifi is taking place through eth1 interface why it happens.....The reason for asking this in order to use aircrack for wep key it says that the injection process only applicable for Athelon interfaces but mine is eth1...I was just trying aircrack-ng...Help me please......

---

### Post by bkratz on 2011-08-20
> **muhammed irshad said:**
> I have installed SATA driver recently...Even if i can use wifi but i could'nt find any ath0 interface in ifconfig or iwconfig commands....My wifi is taking place through eth1 interface why it happens.....The reason for asking this in order to use aircrack for wep key it says that the injection process only applicable for Athelon interfaces but mine is eth1...I was just trying aircrack-ng...Help me please......

The wireless can be named ath0, wlan0, eth1 maybe others (forgot ra0!). This is determined by the card that you have, not by your selection as least I know of no way.

---

### Post by muhammed irshad on 2011-08-20
K....I got you..The thing is with my driver, Sata driver uses eth1 as the interface...But i need to install b43 driver...My wireless card is of type Broadcom bcm4315 so i need to install a firmware called firmware installer or something...But after doing all i can use the b43 driver and i can get the wifi...But problem is i could'nt activate the  driver via the ubuntu additional drivers application....b43 is seen there but it could'nt be activated though....While trying to activate an error of the following appears

SystemError: installArchives() failed.....

Can any1 help me out ....Please ...

---

