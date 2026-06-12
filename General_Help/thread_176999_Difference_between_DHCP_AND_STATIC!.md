---
title: "Difference between DHCP AND STATIC!"
date: 2006-05-15
forum: General Help
---

### Post by Gonzakpo on 2006-05-15
Hello everybody....

Well...i just reinstalled kubuntu because some problems........

the importante here is that the first time i installed it kubuntu didn't recognize my ethernet card but now it did! ..very rare .....but it's working now soooo ...it doesn't matter...

Th question is: ...when it's installing it configures the conection as DHCP ....but my ISP give me and static ip ....sooooo.....should i change it to static? ....
it's working very well now .....i really don't know what to do......(last time i installed kubuntu i configured it as static and it gave me a lot of problems!) ......

i'm connected thru a cable conection using a modem the company gave me....(it's a MOTOROLA SB5100) 

WELL....IT'S A VERY SIMPLE QUESTION, I HOPE ANYONE CAN ANSWER ME...

thanks

---

### Post by Gomek on 2006-05-15
No router?

Whether or not, DHCP will pick up whatever address is thrown at it.  You'll be fine leaving it at DHCP.  Static configuration is more for those that have their own home network and want to have their computers keep the same IP addresses from their routers.

---

### Post by bluenova on 2006-05-15
You ip is still assigned by dhcp, it'll just never change.

---

### Post by jrb114 on 2006-05-15
Hi there,

My own inclination would be to leave as is if it's working fine. 

If you want to be sure, note down your settings, e.g. IP address, DNS servers, and try rebooting. If you restart (and you're still on DHCP) and it still worksm then it's probably going to be fine. If not, then you can at least try the settings your ISP gave you, or the settings you had earlier (if you're quick enough).

All in all, I'd stick though.

J

---

### Post by meng on 2006-05-15
#1: If something works, don't f-, er, mess with with it. Ever.
#2: Are you confusing local IP addresses with public ones? Perhaps you mean your local IPs are allocated by DHCP, while the public IP is static. This is, of course, fine!

---

### Post by jleino on 2006-05-15
[QUOTE=Gonzakpo]Hello everybody....

Well...i just reinstalled kubuntu because some problems........

the importante here is that the first time i installed it kubuntu didn't recognize my ethernet card but now it did! ..very rare .....but it's working now soooo ...it doesn't matter...

Th question is: ...when it's installing it configures the conection as DHCP ....but my ISP give me and static ip ....sooooo.....should i change it to static? ....
it's working very well now .....i really don't know what to do......(last time i installed kubuntu i configured it as static and it gave me a lot of problems!) ......

i'm connected thru a cable conection using a modem the company gave me....(it's a MOTOROLA SB5100) 

WELL....IT'S A VERY SIMPLE QUESTION, I HOPE ANYONE CAN ANSWER ME...

thanks[/QUOTE]
If you ISP gave you a static IP I think you should use it? However this is
somewhat rare, typically one needs to pay extra for that service. Apparently
there is also DHCP available if you got everything working. If you are not
planning to set up a server I think there is not that much use for static IP.
I would suggest you to check again with your ISP that you really need to
use static IP.

If yes, when configuring it you must also set the default gateway,
netmask and possibly DNS servers. Otherwise some trouble is expected...

-- Juha

---

### Post by Slim Odds on 2006-05-15
If your ISP provides a DHCP server, you should use it. It allows your machine to get **ALL** of the networking information it needs (like gateway address, DNS address(es), etc.).

Otherwise, you have to specify these all yourself (which is what you should do if that's the way they told you to do it, otherwise use DHCP).

---

### Post by Gonzakpo on 2006-05-15
HOW MANY ANSWERS!! I WASN'T EXPECTING THIS :D :D :D 

Well, i'll try to leave like that because it's working very well (today i downloaded a lot of programs without problem :) )

Maybe tomorrow i'll call me ISP if there's any problem of using it.....i hope not...

Well, that's all! thank you guys for helping me! ....
Good bye......!

---

