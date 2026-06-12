---
title: "MTU issues with microsoft"
date: 2006-04-05
forum: General Help
---

### Post by twiggy on 2006-04-05
ok so this seems a bit of an odd situation.  i have a netgear modem DG632 which works fine with the internet apart form not being able to connect to hotmail.com and other windows sites.  before i connected this i was using a wireless modem router from netgear which worked and still works fine with everything.

after a lot of searching, help from others i found a way of getting the modem to work in router mode.  i had to change the MTU in the router to 1500 to get hotmail to work.  the problem raises again when i put it into modem mode, there is no way of controlling the modem mode from the router.

so to get the ubuntu server to be able to connect to hotmail.com i changed eth1's mtu using ifconfig eth1 mtu 1400. (eth1 is the external interface).  now i can see it from the server but not from any of the computers connected through it.

eth1 is the external connection
eth0 is the internal connectoin

eth0 is connected to the wireless router with which the computers connect to.

any ideas or advice plz 

thx

Jon

---

### Post by rabidphage on 2006-04-05
everyones got issues with microsoft:mrgreen:

---

### Post by dcstar on 2006-04-05
[QUOTE=twiggy]ok so this seems a bit of an odd situation.  i have a netgear modem DG632 which works fine with the internet apart form not being able to connect to hotmail.com and other windows sites.  before i connected this i was using a wireless modem router from netgear which worked and still works fine with everything.

after a lot of searching, help from others i found a way of getting the modem to work in router mode.  i had to change the MTU in the router to 1500 to get hotmail to work.  the problem raises again when i put it into modem mode, there is no way of controlling the modem mode from the router.

so to get the ubuntu server to be able to connect to hotmail.com i changed eth1's mtu using ifconfig eth1 mtu 1400. (eth1 is the external interface).  now i can see it from the server but not from any of the computers connected through it.

eth1 is the external connection
eth0 is the internal connectoin

eth0 is connected to the wireless router with which the computers connect to.

any ideas or advice plz 

thx

Jon[/QUOTE]

Change the mtu of the other interface.

---

