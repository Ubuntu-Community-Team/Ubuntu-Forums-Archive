---
title: "How to keep networking connected if router reboots?"
date: 2012-01-13
forum: General Help
---

### Post by tbharber on 2012-01-13
I have a Ubuntu server running 11.04. The system works perfectly except for when the power goes out. When the power goes out/back on the computer, modem/router will restart but the problem is because the Ubuntu box reboots faster than the router/modem, it does not start networking upon boot like normal. When this happens I have to login and run a "sudo /etc/init.d/networking restart" to get it working. 

Does anyone have a solution (other than a UPS) so if my router is not up upon boot Ubuntu will do this itself when the router does come back online?

Thanks!!!!

---

### Post by bluexrider on 2012-01-13
Sounds like you need a script to have the network 'sleep' for a while upon restarting.

Found this for you [http://www.linuxquestions.org/questions/linux-newbie-8/delay-in-shell-script-or-alias-233426/](http://www.linuxquestions.org/questions/linux-newbie-8/delay-in-shell-script-or-alias-233426/)

Might give you some direction

---

### Post by tbharber on 2012-01-14
That looks like one solution but it will not work in the case where the router reboots, but not the server.  Im looking for a solution where maybe something will keep an eye out to see if the network connection drops it will just pick it back up.  Any other thoughts?

---

### Post by holycow131415 on 2012-01-14
Get a battery back up and plug them both in it.

---

### Post by duke.tim on 2012-01-14
You could always assign the server a static ip.

You would need to tell the router that the servers 
```
mac address = static ip address
```

steps would include

#1 set server mac address = equal to static address in router
#2 set server static ip
#3 set the servers default gateway to your router address
#4 set network subnet(also known as netmask) address 
(for a 192.168.1.0 network the subnet generally would be 255.255.255.0)
#5 set dns

Here is a website that will show the steps/commands to set it up.

[http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)

More info on network configuration
[https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html)

---

