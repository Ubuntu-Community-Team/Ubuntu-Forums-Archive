---
title: "Anyone for heavens sake help me --Broadband connection"
date: 2006-05-01
forum: General Help
---

### Post by Maccabee on 2006-05-01
Hi,
   Im a linux fan,and im trying to configure internet in my PC for over one year.First tried it with an internal modem then shifted to a USB,then finally
a pppoe connection and that too dont seems to work.
 My modem huawei MT841 is connected to a Realtek's Network card,and when i try to setup connection in Ubuntu using sudo pppoeconf it first lists two ethernet devices eth1 and eth2 and scans both then it complains IT COULDNT FIND ANY ACCESS CONCENTRATOR .what the hell is this concentrator???
Is my network card not working???
Can anyone Help me please???????????????????:( :( :( :(

---

### Post by az on 2006-05-01
[QUOTE=Maccabee]Hi,
 
Is my network card not working???
:([/QUOTE]


That could be one reason.  Are you sure it was working?  Are you using the correct cable (crossover, versus patch cable?)

---

### Post by duality on 2006-05-01
try "sudo dhclient eth1" or "sudo dhclient eth0" or whatever your interfaces card is named, if you get an ip there then it working

gl

---

### Post by immanueln2005 on 2007-07-27
Hi guys.... Even i had the same problem for 2 weeks, but this simple change made it right...

Just go to network > Wired Connection > static connection > 

Type in your ip address, subnet mask and gateway address...

Go back and set your DNS address....

Voila... you are done...

---

