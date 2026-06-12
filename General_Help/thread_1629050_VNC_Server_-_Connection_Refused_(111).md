---
title: "VNC Server - Connection Refused (111)"
date: 2010-11-23
forum: General Help
---

### Post by gs17 on 2010-11-23
Hi all,

Most of my problems so far have been solved by browsing the forums. However, I am stuck at this one issue with VNC.

I am trying to connect to my desktop from my laptop. However, after enabling all the options for remote desktop on VINO, I get an error when I try to connect to my desktop.
```
VNC Viewer Free Edition 4.1.1 for X - built Apr  9 2010 18:41:55
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Tue Nov 23 16:31:53 2010
 main:        unable to connect to host: Connection refused (111)

```

These are the things I have already tried:

1. Connecting using vncviewer from my desktop to itself(localhost)     - WORKS
2. Connecting from my laptop to my laptop (localhost)   - WORKS
3. Connecting from my desktop to my laptop           - WORKS
4. Connecting from my laptop to desktop  -  FAILS!!
5. Ping from my laptop to desktop        - WORKS

I then tried with vnc4server (which I like better than vino), but had the same error.

These are the things I configured:

1. Blacklisted ipv6 on my desktop - as I read somewhere.

2. nc -zv to check port from my laptop
```

xxxx@xxxx-Ubuntu:~$ nc -zv <desktop_ip> 5900
nc: connect to <desktop_ip> port 5900 (tcp) failed: Connection refused

```

3. nc -zv on my desktop (localhost) is successful - as is the vncviewer connection. 



I think the settings of VNC are fine, but there is some problem in my laptop connecting to the desktop (though it pings fine). Both laptop and desktop are in the same network.

Any suggestions would be great. I have the same problem with both VINO and VNC4SERVER

Thanks,
GS

---

### Post by tredegar on 2010-11-23
> 1. Connecting using vncviewer from my desktop to itself(localhost) - WORKS
So it is runnimg and working. Good.
> 2. Connecting from my laptop to my laptop (localhost) - WORKS
So it is running and working. Good.
> 3. Connecting from my desktop to my laptop - WORKS
Also good.
> 4. Connecting from my laptop to desktop - FAILS!!
Bad.
> 5. Ping from my laptop to desktop - WORKS
So ping works. This means the network is connected but something else is not allowing the connection.

"Connection refused" generally means you have mis-configured your firewall, **ssh** options, or similar.

The place to start looking is on your desktop because that is the PC that is "refusing connections". If your PCs are on your LAN, then they should trust themselves (after all, you administer them).

I put my firewall on my ROUTER, which is my connection to the big, bad internet. Behind my router, my LAN is open to itself. 

I think you have a firewall (Eg **iptables**) running on your desktop that is refusing connections. Look there first. Maybe open some ports, or disable the firewall if you are confident you are filtering connections "upstream".

On your desktop, **iptables --list** (as root) might help you work out what is broken.

---

### Post by gs17 on 2010-11-23
> **tredegar said:**
> 
On your desktop, **iptables --list** (as root) might help you work out what is broken.

Thanks for your reply!

I did not install any firewall, so I am guessing iptables is a firewall installed by default with Ubuntu. This is the output of my iptables --list: (I guess this is fine)
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination      

```

This is in my office, but I have made fresh install of Ubuntu 10.10 on both my PC and laptop. The tricky part is that I can remote login into my laptop from PC but not vice-versa. 

I am not great at networks, but my guess is that this is some config problem related to ports. Netcat command suggests the same thing. Is there anything else I can check/change?

Thanks!

---

### Post by gs17 on 2010-11-23
I want to add that I installed open-ssh server on this desktop. Again, it accepts connections (on port 22) from localhost, but not from my laptop. 

From my laptop, it gives me a "Connection Refused" error even with SSH.

Also, I am able to smoothly SSH from the desktop to laptop. So there is something wrong in the settings of my desktop. I also disabled the firewall ("ufw disable"), but the same result. So I am guessing firewall is not the problem.

Any help will be great, as I have spent too much time on this by now, but have gotten no result so far.

---

### Post by tredegar on 2010-11-25
Apologies for the slow reply, but I have been very busy with "real life".

You seem to be looking at the right things:

From your post above, your firewall isn't doing anything (because there are no rules listed). This is OK.
Please confirm that this was the output from your desktop, not your laptop, as it seems your desktop is the one that is refusing connections.

I am going to be pedantic, and boring, but I am confused: You refer to "office", "PC", "Laptop" and "Desktop". Some of these are perhaps the same machines. I do not know. Some people have "office" at home (in the same building, and connected to the same router, and on the same LAN), for other people "office" is 12,000km away, but although it is still "office" to them, the internet routing, and firewalling is more complicated.

Are your PCs all on the same LAN, or are they at different locations? If at different locations and  your "Desktop / Office" is accessed over the internet, you should look at the firewall that is *probably* running on your modem/router at the location your "Desktop" is placed. This may be the source of "Connection Refused".

Most modern modem / routers are now configured by default to run a firewall (a "good thing" for those running win) that, by defaut, refuses incoming connections. You may need to open port(s) 5900-x on your modem / router at your "desktop" PC location and forward them to the same ports on the LAN IP of your (office?) "desktop / PC". See your "Office" modem / router's documentation for how to do this.

Hope this helps. If not, come back with ALL the boring, but necessary, details of your network setup, and I'll do my best to help you further.

---

