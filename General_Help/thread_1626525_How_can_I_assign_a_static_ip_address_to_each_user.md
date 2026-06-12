---
title: "How can I assign a static ip address to each user?"
date: 2010-11-20
forum: General Help
---

### Post by vcrpcant on 2010-11-20
Hi,

How can I assign a static ip address to each user?

The reason for this is to aloud some users to surf the internet and others only some sites, using a hardware firewall to filter the ip address.

---

### Post by axept on 2010-11-20
You can assign a IP to a computer in the settings for your router/modem. Then the computer will get the same local IP everytime. You can do this for every connected item on your router/modem.

---

### Post by stefangr1 on 2010-11-20
> **vcrpcant said:**
> Hi,

How can I assign a static ip address to each user?

The reason for this is to aloud some users to surf the internet and others only some sites, using a hardware firewall to filter the ip address.

You should look this up in the manual of your router. I think that this is not possible with most routers, mut you could be lucky...

---

### Post by vcrpcant on 2010-11-20
I should have made myself clear, sorry.

What I mean is, how can I assign each user _on the same computer_ a specific ip address?

Regards

---

### Post by axept on 2010-11-20
Ohhhh... That was something else yes..

I cant help you on that one, seems tricky...

---

### Post by Austin25 on 2010-11-20
I know! You could make a script to run on login with ifconfig, then change it a bit for each user.

---

### Post by The Cog on 2010-11-20
If you right-click the network manager icon, you can choose to edit connections. In there, under ipv4 settings, you can set a static IP address. 

At the bottom of the configuration editor is a tick-box that says make this connection available to all users. If checked, the setting is saved as a system setting, the same for all users. If un-checked, the setting is stored as a custom user setting for the user who is doing the editing (not accessible to other users). So you could edit the network settings for each user individually, but of course they could always come along and change them again.


An approach that users can't interfere with might be to have a script running occasionally (under cron perhaps) that works out which user is currently logged on to the GUI (maybe who owns the gnome-panel process) and update the IP address accordingly.

Both the above assume that you are worried about one user, logged into the GUI. They don't address the idea of remote users doing things.

---

### Post by vcrpcant on 2010-11-20
Thanks guys, especially Austin25 and The Cog! 
I like the idea of the script:) can anybody please help me on it?

Regards,

---

### Post by vcrpcant on 2010-11-25
Bump

If someone could help me writing this scrip it would be great.
It's frustating knowing the answer can't apply it :o

Regards,

---

### Post by WorMzy on 2010-11-25
I've set a static IP address with dhcpcd before:

```
sudo dhcpcd -qx wlan0 #quietly shutdown dhcpcd for wlan0, if running
sudo dhcpcd wlan0 -s 192.168.0.140 #turn dhcpcd back on for wlan0, and attempt to use static IP
```

I believe that ifconfig works in a similar way:

```
sudo ifconfig wlan0 192.168.0.140
```

Note that both of these commands require sudo, so you'd need to add an alias for the command/script in sudoers if you want each user to run it without having to enter a password. Also, not all routers will allow you to declare a static IP, and will just assign you with an IP address of their choosing.

---

### Post by efflandt on 2010-11-25
Wouldn't it be easier to set up something like **squid** as a transparent proxy.  Then you could control web access on a per user basis.  Web search "squid transparent proxy".

---

### Post by trigity on 2010-11-25
> **WorMzy said:**
> I've set a static IP address with dhcpcd before:

```
sudo dhcpcd -qx wlan0 #quietly shutdown dhcpcd for wlan0, if running
sudo dhcpcd wlan0 -s 192.168.0.140 #turn dhcpcd back on for wlan0, and attempt to use static IP
```

I believe that ifconfig works in a similar way:

```
sudo ifconfig wlan0 192.168.0.140
```

Note that both of these commands require sudo, so you'd need to add an alias for the command/script in sudoers if you want each user to run it without having to enter a password. Also, not all routers will allow you to declare a static IP, and will just assign you with an IP address of their choosing.
The previous method is ok, but you can do the same from the GUI under networks. You also need to be aware that your clients must have and operate under the same subnet mask and the router as well. EX;192.168.1.0/24 at 255.255.0.0/24 and make sure to set your routing tables correctly. This is okay for a couple of clients, but when you get up around 10 to 20 clients you'll find this a daunting task, just better leave it DHCP to do the job.

---

### Post by karthick87 on 2010-11-25
Check this link for squid transparent proxy

[http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html](http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html)

---

### Post by vcrpcant on 2010-11-27
Thanks guys, especially efflandt and karthick87, I think squid transparent proxy will be very useful :D
Meanwhile, I've also stumbled upon Gnome Nanny

Regards

---

