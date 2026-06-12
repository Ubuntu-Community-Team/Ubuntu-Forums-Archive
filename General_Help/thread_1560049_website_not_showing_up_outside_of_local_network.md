---
title: "website not showing up outside of local network"
date: 2010-08-24
forum: General Help
---

### Post by darkapec on 2010-08-24
Here is the setup, ubuntu 10.04 LAMP server, webmin remote gui and  shorewall. My router is the well known wrt54g with ddwrt installed on  it. I have the website working, the domain name is [www.darkapec.com]("http://www.darkapec.com/"), I can access it fine from any of the intranet computers. I can access it by typing [www.darkapec.com]("http://www.darkapec.com/")  i can access it by typing 192.168.1.125, it will even show up if i type  in my routers ip address. However if I try to access the website off my  network (with cell phone, friends computer, wifi hotspot) the website  says it timed out and cannot be displayed. And to top everything off if I  am at the hotspot and I type [www.darkapec.com:1000/]("http://www.darkapec.com:1000/")  sure enough the webmin login will show up and it works fine. I was  thinking it was a router problem at first. But I dmz port forwarded  almost every port and still the same situation. I have setup all the  ports on shorewall (i think) I have put ports 80, 8080, 22 and 10000.  There all setup for both UDP and TCP. Any ideas?? Is there permissions  that need to be changed??

Thanks

---

### Post by darkapec on 2010-08-24
Simple solution... CHARTER!!!! Charter is the problem they block port 80 on all non business accounts. The solution is to run a web server on a  non-standard port in conjunction with a port 80/web redirect from  No-IP.com. I didn't think it was a router / ubuntu problem but I had hoped someone around here could clue me into finding the answer. 

wonder if I can find a provider who will just let me do what I want... I mean I do live in America!

---

