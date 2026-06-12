---
title: "strange router issue"
date: 2012-02-22
forum: General Help
---

### Post by imachavel on 2012-02-22
I am connected to the internet, connected to a dns server with the services running. I am connected through a 2wire at&t modem, not directly. I am hard wired to a d link router giving me dhcp that is hard wired to an at&t modem. I have access to the internet but cannot log in to the d link router with 192.168.0.1, when I ping 192.168.0.1 I get a reply from 74.233.5.1: destination net unreachable. My question is how do I have internet access if I am not directly hard wired to the at&t modem but to the d link, if I can't pin 192.168.0.1? If my d link router i.p. address has changed, then how do I find the new i.p. address? arp -a returns:

192.168.1.65 dynamic
192.168.1.254 dynamic
192.168.1.255 static(at&t 2wire address)
224.0.0.22 static
224.0.0.251 static
224.0.0.252 static
239.255.255.250
255.255.255.255(experimental class right?)

I don't know, netstat gives me:

well just loop back pings(127.0.0.1)

Really strange network interface adapter is working fine, can't figure the rest out. Any help would be appreciated

---

### Post by Ms. Daisy on 2012-02-23
What happens when you go to the website [http://192.168.0.1](http://192.168.0.1) ? Do you get the router log-in page?

> If my d link router i.p. address has changed, then how do I find the new i.p. address? If the above doesn't get you to the log-in page, then I recommend you Google the name and model of your router to make sure that's the correct address.  My router is a netgear, but it has the login page address written on the router box.  I suppose d-link may do the same thing.  

If you still can't log in, then I would reset the router. Again you may have to Google your specific router to find out how to do that and to find the default username & password (if those aren't written on the router box).  Then you would absolutely need to reset the username & password.

---

