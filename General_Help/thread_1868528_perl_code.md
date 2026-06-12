---
title: "perl code"
date: 2011-10-24
forum: General Help
---

### Post by irakla7777777 on 2011-10-24
hi everyone

i have configured snmp on my cisco switch.

i get the message :

iso.3.6.1.2.1.17.7.1.2.2.1.2.4091.100.49.80.27.64.126 = INTEGER: 49


where :
4091 is a vlan
100.49.80.27.64.126 is mac address in decimical format 
INTEGER: 49  is physical port number.

i want to log this information following format:

vlan = 4091 mac-address = 64:31:50:1b:40:7e  port number = 9

i found net::mac for converting mac address dec to hex in perl and it worked.
but i can not do others .
anybody can help me ?

---

