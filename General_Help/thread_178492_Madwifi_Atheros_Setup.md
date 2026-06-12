---
title: "Madwifi Atheros Setup"
date: 2006-05-17
forum: General Help
---

### Post by adrianarath on 2006-05-17
I have a TOSHIBA Satellite A35 S159 notebook, with an Atheros 5001X+ wireless card.  Initially, with the Ubuntu fresh install drivers, the card could be read and scan networds but could not connect to a WEP secured network.  In fact, it would read two instances of the same WEP network, one that appeared not encrypted, and the regular one.  So, I searched for drivers for the card and found madwifi.  I installed madwifi following a couple of HOWTO's found on the forum and the card seemed to be working alright from the terminal.  The Networking tool in the system did not work properly; when I ran wlanconfig ath0 list scan the networks would be scanned properly.  However, when I connected and pinged google; I got the unknown host error messege.  I also ran   

wlanconfig ath0 create wlandev wifi0 wlanmode sta

and got 

wlanconfig: ioctl: Input/output error

However, when I ran

iwconfig ath0 key restricted
iwpriv ath0 authmode 2
dhclient ath0

and was able to connect to the WEP encrypted.  The problem is, I have to run that each time I want to connect or restart the OS; and sometimes I lose the conection.  Is there a way to fix the error messages and/or be able to conect to the wireless through the network manager on start up?  Im a linux newbie, so any help appreciated.

---

### Post by bryanpaluch on 2006-05-18
I have a very similar problem. I can connect to my home network no problem. Its using wep encryption 64 bit hex. When I go to my college campus (drexel uni) I pick up many ap's with only around an 1/8 of them say encrypted. I get that from running iwlist scanning. If I use network-manager my schools wireless comes up as unencrypted, but I know for sure that is. I can connect no problem in windows. I also was able to connect to it before kernal upgrade 22. I'm figuring it has to do with madwifi-ng drivers not working so well. I've got an atheros card.

---

### Post by adrianarath on 2006-05-18
Yeah, I installed the ng madwifi; and I gave up on the network manager.  I just use the terminal now, and it works; I just have to reset the dhcp settings each time I restart. Dont know about the previous kernels; Im new.

---

