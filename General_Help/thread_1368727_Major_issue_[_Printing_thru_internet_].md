---
title: "Major issue [ Printing thru internet ]"
date: 2009-12-31
forum: General Help
---

### Post by savimayur on 2009-12-31
My office  ubutu system  [ Karmik 9.10 ] is working flawlessly and connected to a router which assigns local ip like 192.168.1.100. The router has a static internet address. 

Hp printer is connected to this Ubuntu System.

How can I print from my windows laptop using internet  ?  [ Say from home ]

Any help will sort out my much of problems.


Thanks in advance.

Regards

---

### Post by falconindy on 2009-12-31
Forward port 631 on the router to your office desktop's internal IP address. Add a network printer on the windows laptop and point it to:

http://<ipaddress>:631/printers/<printername>

Where ipaddress is the public IP of the router and printername is the name given to the printer in Ubuntu.

---

