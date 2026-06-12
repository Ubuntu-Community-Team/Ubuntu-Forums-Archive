---
title: "Hipporemote not connecting to ubuntu 10.10"
date: 2010-12-12
forum: General Help
---

### Post by Michael577 on 2010-12-12
I recently got an app called Hipporemote and I'm trying to get it connected to my computer. Now I know that the VNC connection isn't good with security, but when you spend about 3 bucks on this software, you want it to work. Anyway, the Hipporemote sees my computer, but when I try to connect to it it keeps on saying that it doesn't have a VNC server installed, which it is by the way.  So what is the problem? Can anyone tell me how You installed or got this app working in ubuntu 10.10?

---

### Post by redspider on 2011-01-26
A)
same problem.    steps to fix 
  ##notations
  ##disabling "ufw" fixed the problem. (terminal)

     1)   'su ufw (tab key)'  disable i think was the ARGS.
  ## afterwards hippo v1.2 works but now no firewall. 
    
     2)   'su ufw enable' 
  ## remote still works
     3)   'ufw status'
  ## should show list of rules 
     4)   exit hippo application on "i"device 
     5)   restart hippo application. 
  ## doesn't connect anymore. 

B)
proposed problem

     1)  'ufw' is blocking hippo port access.

proposed solution 
  ##allow the port thats being blocked.
     1)  'su ufw allow 5900' 
  ## allow connections through port 5900.

results
     1) hippo still "unable to connect..." 



C) 
conclusion 
hippo is being stopped by program ufw.
find the right port and hippo should work.
if access is necessary use vnc program such as 'issh' or jadu*1 with port rule allow 5900.



D)
hippo version 1.2
ubuntu version 10.10



E)
*1 jadoo jaido jaduu jaado (spelt funny)

---

### Post by redspider on 2011-01-26
Update 1
after rebooting it hippo works on saved connections.
will try with newer versions.


ufw comes with default instillation 

so...
terminal 
su or sudo
_'ufw allow 5900'_
and it should work, after a reboot.

version 3.XX works.


search tags    ubuntu remote mouse hipporemote iphone itouch ipod vnc ufw

---

