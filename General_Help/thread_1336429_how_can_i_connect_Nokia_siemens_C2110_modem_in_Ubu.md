---
title: "how can i connect Nokia siemens C2110 modem in Ubuntu?"
date: 2009-11-24
forum: General Help
---

### Post by abeyrv on 2009-11-24
[B][SIZE=2][COLOR=Blue]Hi all...
I am new to linux & this forum.this is my 1st post. 
       Recently i installed ubuntu in my system (along with windows XP). The problem is that in ubuntu i am not able to access internet. while there is no problem in windows. My LAN is not working so i am using USB connector for connecting this C2110 modem to my system. For that i installed driver in windows. Is that necessary to install its driver in ubuntu too. Then how can i install that in ubuntu.?
While turning on the modem, it will automatically connects the s/m to net (indicating it by glowing all led lights on the modem).So the service providers didnt give any Username & Password.I search many on this forum but i didnt see any post regarding this USB connection.
How can i connect by USB modem to ubuntu. Please help to achieve this. I cant explore or stduy linux without internet.
Note : 
1) This modem provides both facility for usb or LAN connetion but i am using usb connection
2) No username / password:-s
3) excepting a basically described reply, as i told earlier am new to linux.
Expecting valuable replies n suggestions...

Regards...
ARV:confused:[/COLOR][/SIZE][/B]

---

### Post by Vysakh P on 2010-01-07
May be you should try to connect your mdem using LAN port. I've read in many posts people complaining about modems not working when connected using USB port.

If you've done that try 'sudo pppoeconf' in a terminal window. Give username and password in appropriate fields and leave the ones you don't know.

---

