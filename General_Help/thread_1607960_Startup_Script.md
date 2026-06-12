---
title: "Startup Script"
date: 2010-10-28
forum: General Help
---

### Post by Toxcity on 2010-10-28
Hey guys! 
I am sure it has been asked a bazillion times before but I could find anything on it. :( 

Basically, I want the following command to run every startup so I don't have to run it manually. 

```
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
```

It sets up routing for my Windows machines to get Internet access. Not sure whether I need to run the following code as well..

```
sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE
```

Regardless, even if I just execute the Routing.sh file I created it doesn't work. No internet for the rest of the network. 

Any ideas? Where am I going wrong? 

Also, very quite new to Ubuntu but not to computers. :)

---

### Post by Ctorpor on 2010-10-28
> **Toxcity said:**
> Hey guys! 
I am sure it has been asked a bazillion times before but I could find anything on it. :( 

Basically, I want the following command to run every startup so I don't have to run it manually. 

```
sudo sh -c &quot;echo 1 > /proc/sys/net/ipv4/ip_forward&quot;
```It sets up routing for my Windows machines to get Internet access.

I, too, would like to know how to do this and was unable to find it. I need add the start up script through terminal because it is going to run as part of the build process for a custom distro. I tried adding the script to /etc/init.d/ but it did not run.

---

### Post by xircon on 2010-10-28
Write a script and (in Gnome) add to startup programs

```

#!/bin/bash
sudo sh -c &quot;echo 1 > /proc/sys/net/ipv4/ip_forward&quot; 

```

---

### Post by blueridgedog on 2010-10-28
Or you could put the command:

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

In an rc.local file:

[https://help.ubuntu.com/community/RcLocalHowto](https://help.ubuntu.com/community/RcLocalHowto)

---

### Post by sisco311 on 2010-10-28
> **Toxcity said:**
> Hey guys! 
I am sure it has been asked a bazillion times before but I could find anything on it. :( 

Basically, I want the following command to run every startup so I don't have to run it manually. 

```
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
```

It sets up routing for my Windows machines to get Internet access. 



Create a .conf file in /etc/sysctl.d/, i.e. /etc/sysctl.d/40-routing.conf with the following content:
```
net.ipv4.ip_forward = 1
```

> **Toxcity said:**
> 
Not sure whether I need to run the following code as well..

```
sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE
```



Not sure, check out [http://bodhizazen.net/Tutorials/iptables/#Saving_your_configuration](http://bodhizazen.net/Tutorials/iptables/#Saving_your_configuration)

---

### Post by Toxcity on 2010-10-28
Cheers guys! 
sisco311 solution worked for me. Thanks again. :)

---

