---
title: "Unable to recognize my domain address (Ubuntu 9.10 on Windwos 7 using VirtualBox)"
date: 2010-02-16
forum: General Help
---

### Post by programming.name on 2010-02-16
Hi, FIrst of all, I have been using Ubuntu 9.10 Desktop Edition as server on my desktop for almost 2 months with no problem and 
 
I am also using my laptop which I usually use. While I am running my own server, I found that it is too expesive to turn on the 
 
desktop all day long. So I decided to give up the desktop and I installed Ubuntu 9.10 on my laptop(Windows 7 x86 already installed) using 
 
Virtual Box instead. After installing Ubuntu 9.10 Desktop Edition using Virtualbox, I installed and configured Lamp server. But a problem occured. 
 
It seems ubuntu won't recognize my domain address and external IP. I first thought the lamp-server installation went wrong, so 
 
I typed [http://127.0.0.1](http://127.0.0.1) in Firefox to check whether the apache server is installed correctly and that worked fine.
 
But the thing is that the internal network ip address in Windows 7 and Ubuntu(VirtualBox) are different. The command "ipconfig /all" shows the
 
internal network ip address is 192.168.0.5 in Windows 7(4 computers being connected to a router which is not significant), but it appears to be 
 
10.0.2.15 in Ubuntu(virtual Box window). So I tested again with [http://10.0.2.15](http://10.0.2.15), this one worked fine as well. And as always, I DID portforward to 
 
my externel IP in the router setup page, and the command ping to my domain responded normally. 
 
The thing is that the command "ipconfig /all" shows the internal network ip address is 192.168.0.5 in Windows 7(4 computers being connected to
 
a router which is not significant), but it appears to be 10.0.2.15 in Ubuntu(virtual Box window). 
 
What else do I need to do? 
 
Thanks

---

### Post by bluefrog on 2010-02-16
the simplest for you is to use bridge mode for the virtualbox network card. not NAT

---

