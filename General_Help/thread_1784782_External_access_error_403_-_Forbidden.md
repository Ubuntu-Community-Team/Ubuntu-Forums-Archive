---
title: "External access error 403 - Forbidden"
date: 2011-06-17
forum: General Help
---

### Post by travelbones on 2011-06-17
[COLOR=#0068cf]We[/COLOR] host SugarCRM software on an Ubuntu box. We log into it from inside the local network by using a simple Class C address of 192.168.1.101/sugar and it logs to the login screen via a web browser. If I do not type the local address and use the external WAN address from INSIDE the network, xx.xx.xxx.xx/sugar, it still gets forewarded to the login screen. I have popped the appropriate port 80 through the firewall and the route to forward all incomming web requests to the Ubuntu box. BUT........if I actually try and type the WAN address from outside the local nwetwork and directly connect through the Web, typing the incomming WAN such as xx.xx.xxx.xx/sugar, I get the 403 Forbided denial page that showd the apache2 version and the Ubuntu OS version. So, I know it is hitting the box, I just done know what line in what file is stopping the external request. I tried looking at the apache2.conf file but have has no luck. I even tried to comment out the lines referring to the .ht File(s) and no luck. All I do after changing the .conf file is do a terminal restart every time to the apache2.
 
IF anyone can help me with this issue I would be SOOO greatful. I have talked to several UNIX guru's and I get brushed off every time. I know I am not as ssavvy as most of the people in the forum, but I need to learn.

---

