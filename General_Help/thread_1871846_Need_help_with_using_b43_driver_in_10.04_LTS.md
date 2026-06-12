---
title: "Need help with using b43 driver in 10.04 LTS"
date: 2011-10-29
forum: General Help
---

### Post by bplzip on 2011-10-29
I've been using the Broadcom STA wireless driver with a Dell XPS M1530 laptop since installing 10.04 LTS in April 2010. Recently I installed Linux Mint LMDE and found that the b43 driver works on the XPS M1530, connects faster and gives me faster download speeds in LMDE.

Running the 
~$ lspci -vvnn | grep 14e4  
command yields the following info:
In Ubuntu: Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
In LMDE: Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03).

 I followed instructions at
 help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access
to install the b43 driver, which works in LMDE.  After running 
~$ sudo apt-get install b43-fwcutter
in terminal, the b43 driver does not appear in System > Administration > Hardware/Additional Drivers.

I want to continue using Ubuntu, but sometimes the it takes several attempts to connect using the STA driver. In LMDE the b43 driver connects in just a few seconds every time. And using online bandwith speed tests, I am getting download speeds 3 to 4 times faster using the b43 driver in LMDE.

So, I'd appreciate help in getting Lucid 10.04 to use the b43 driver. Any ideas?

---

### Post by bkratz on 2011-10-29
> **bplzip said:**
> I've been using the Broadcom STA wireless driver with a Dell XPS M1530 laptop since installing 10.04 LTS in April 2010. Recently I installed Linux Mint LMDE and found that the b43 driver works on the XPS M1530, connects faster and gives me faster download speeds in LMDE.

Running the 
~$ lspci -vvnn | grep 14e4  
command yields the following info:
In Ubuntu: Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
In LMDE: Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03).

 I followed instructions at
 help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access
to install the b43 driver, which works in LMDE.  After running 
~$ sudo apt-get install b43-fwcutter
in terminal, the b43 driver does not appear in System > Administration > Hardware/Additional Drivers.

I want to continue using Ubuntu, but sometimes the it takes several attempts to connect using the STA driver. In LMDE the b43 driver connects in just a few seconds every time. And using online bandwith speed tests, I am getting download speeds 3 to 4 times faster using the b43 driver in LMDE.

So, I'd appreciate help in getting Lucid 10.04 to use the b43 driver. Any ideas?



According to
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

The b43 driver will require you to upgrade your kernel to at least version "[COLOR=Red]partially in 2.6.39+[/COLOR] "  
2.6.39 and you are probably around 2.6.32.34 or so in Lucid.

---

### Post by bplzip on 2011-10-30
> **bkratz said:**
> According to
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

The b43 driver will require you to upgrade your kernel to at least version "[COLOR=Red]partially in 2.6.39+[/COLOR] "  
2.6.39 and you are probably around 2.6.32.34 or so in Lucid.

bkratz, thanks for your reply. I saw that information about 2.6.39+, but I guess it just didn't register in my head that I might be running an older kernel than that in Lucid...my oversite.:redface: Sooooo....

I installed 11.10 on a USB flash drive, then installed the b43 driver. After deactivating the STA driver and rebooting, I was wirelessly connected immediately. So it appears that b43 was installed and activated after all. It just did not appear in **Additional Drivers**.

However, I'll be staying with LMDE at least until 12.04 LTS is released. I prefer LTS releases, so I'll give 12.04 a try when it is released.

---

