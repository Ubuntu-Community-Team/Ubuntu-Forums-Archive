---
title: "Need Help Running Programs at Startup"
date: 2009-12-31
forum: General Help
---

### Post by FireYello on 2009-12-31
Hi 

I have installed Samba and Telnet servers on an old laptop computer running Ubuntu 8.04 and they work fine. The problem is that the server(s) only run if I log into the computer with my username/password first. 

An even bigger problem is that the WiFi connection doesn't start unless I log into the computer first as well. What I'd like to have happen is dispense with the monitor/keyboard so I can telnet in when needed, but always have WiFi and Samba start up from a reboot. 

I've looked into run levels a bit, but Ubuntu seems to do it differently from the way I learned about in books. 

I think this forum is the most appropriate since the questions are related to how to get things started - even though those things happen to be networking-related. 

Happy New Year!


FY

---

### Post by tom4everitt on 2009-12-31
If you know the commands to this, you can just add them to /etc/rc.local. 

All lines in this file will be executed at startup (as root).

---

### Post by dcstar on 2009-12-31
> **FireYello said:**
> Hi 

I have installed Samba and Telnet servers on an old laptop computer running Ubuntu 8.04 and they work fine. The problem is that the server(s) only run if I log into the computer with my username/password first. 

An even bigger problem is that the WiFi connection doesn't start unless I log into the computer first as well. What I'd like to have happen is dispense with the monitor/keyboard so I can telnet in when needed, but always have WiFi and Samba start up from a reboot. 

I've looked into run levels a bit, but Ubuntu seems to do it differently from the way I learned about in books. 

I think this forum is the most appropriate since the questions are related to how to get things started - even though those things happen to be networking-related. 


If you have the network-manager package installed then your networking will only be configured after login to the GUI (insane, isn't it?).

Install the gnome-network-admin package and use that to configure the networking (or manually edit the /etc/networks/interfaces file).

If you just want a headless server, then you should install the Ubuntu Server distro and not the standard distro.

---

