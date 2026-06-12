---
title: "CUPS not starting at boot up.."
date: 2011-02-04
forum: General Help
---

### Post by mahela007 on 2011-02-04
Browsing through the forums, one can see that many other users have this same problem. However, many of those threads show that adding two lines to the file "/etc/network/interfaces" should solve the problem. I checked on my PC and those two lines are already there.. but CUPS still doesn't start properly on boot up...

---

### Post by anglican on 2011-02-04
> **mahela007 said:**
> Browsing through the forums, one can see that many other users have this same problem. However, many of those threads show that adding two lines to the file "/etc/network/interfaces" should solve the problem. I checked on my PC and those two lines are already there.. but CUPS still doesn't start properly on boot up...Try:
```
sudo apt-get install chkconfig
chkconfig --list | grep cups
```to see if the system should be starting it (cups uses SYSV init rather than upstart). If it isn't already set to "on" in levels 2,3,4,5 then:
```
sudo chkconfig cups on
```is probably what you need. If it is already set to "on" you could try adding a script that will force a start on every boot:
```
gksu gedit /etc/network/if-up.d/cups
```
With this content:
```
#!/bin/sh
service cups restart
```
Save the file and make it executable:
```
sudo chmod +x /etc/network/if-up.d/cups
```

H

---

