---
title: "dhcpd blocking oui's but allow some mac addresses"
date: 2010-11-11
forum: General Help
---

### Post by qwerty555 on 2010-11-11
[FONT=Times New Roman][SIZE=3]I have a situation where I am attempting to block a number of oui’s from dhcp addresses but I would still like to be able to allow some mac addresses that contain the blocked oui’s.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Here is some code of what I have tried so far…[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]class "block"{ [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]match if (substring (hardware, 1, 3) = 00:1c:b3) or[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman](substring (hardware, 1, 3) = 00:1c:b4) or…[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]}[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]class “allow”{[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]match if (substring (hardware, 1, 6) = 00:1c:b3:xx:xx:xx) or…[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]}[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Then in one pool I have[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Deny members of “block”;[/SIZE][/FONT]
 
 
[FONT=Times New Roman][SIZE=3]Then in another pool I have [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Deny members of “block”;[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Allow members of “allow”;[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I am having problems because the mac address 00:1c:b3:xx:xx:xx is getting blocked from the first and second pool when I would like it to be blocked by only the first and allowed in the second. I believe this is caused because it is in both the block and allow class. Does any one know how I might be able to take only one mac address out of the block class or if there is another way this could be achieved?[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I am running dhcp3 on ubuntu[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Any ideas are appreciated,[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Thank you[/SIZE][/FONT]

---

