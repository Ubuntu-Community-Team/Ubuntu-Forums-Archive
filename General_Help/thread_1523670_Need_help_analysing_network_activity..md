---
title: "Need help analysing network activity."
date: 2010-07-04
forum: General Help
---

### Post by revered on 2010-07-04
I did a "netstat -a" and I saw this:

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
udp        0      0 *:mdns                  *:*                                
udp        0      0 *:49021                 *:*       
```

Does someone knows what the heck could that be? I am running ubuntu 10.04 lts. I installed ufw and set it with "ufw default deny", shouldn't that close all the ports? Please help me make sense of that netstat -a.

---

### Post by Rubi1200 on 2010-07-04
From the terminal run this:

```
sudo lsof -i -n -P
```

Post the results back here so we can take a look.

In the meantime, you should definitely be reading:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Especially the section on firewalls, configuration etc.

---

### Post by revered on 2010-07-04
Here we go:

```
COMMAND    PID    USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
avahi-dae  746   avahi   13u  IPv4   3964      0t0  UDP *:5353
avahi-dae  746   avahi   14u  IPv4   3965      0t0  UDP *:49021
transmiss 3133 myuser   12u  IPv4  23938      0t0  TCP *:51413 (LISTEN)
transmiss 3133 myuser   13u  IPv4  23941      0t0  UDP *:51413
transmiss 3133 myuser   14u  IPv6  23940      0t0  TCP *:51413 (LISTEN)
transmiss 3133 myuser   20u  IPv4  23948      0t0  UDP xxx.xxx.103.75:1262->xxx.xxx.64.64:5351
transmiss 3133 myuser   60u  IPv4  32055      0t0  TCP xxx.xxx.103.75:5376->xxx.xxx.34.142:21673 (ESTABLISHED)
transmiss 3133 myuser   97u  IPv4  32084      0t0  TCP xxx.xxx.103.75:3177->xxx.xxx.54.214:47568 (ESTABLISHED)
transmiss 3133 myuser  248u  IPv4  32433      0t0  TCP xxx.xxx.103.75:2695->xxx.xxx.127.111:60657 (ESTABLISHED)
firefox-b 4425 myuser   27u  IPv4  41633      0t0  TCP xxx.xxx.132.2:3835->xxx.xxx.47.113:80 (ESTABLISHED)
firefox-b 4425 myuser   44u  IPv4  41708      0t0  TCP xxx.xxx.132.2:5772->xxx.xxx.7.37:80 (ESTABLISHED)

```

It's avahi, but I have no idea why its running, I read it can be used for Rhythmbox, which I use sometimes, but avahi is running all the time. Also my network is made of my main pc and virtual machines, I never connect the laptop or other computers. So why do i need avahi? Is it safe to uninstall?

---

### Post by Rubi1200 on 2010-07-04
> **revered said:**
> Here we go:

```
COMMAND    PID    USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
avahi-dae  746   avahi   13u  IPv4   3964      0t0  UDP *:5353
avahi-dae  746   avahi   14u  IPv4   3965      0t0  UDP *:49021

```It's avahi, but I have no idea why its running, I read it can be used for Rhythmbox, which I use sometimes, but avahi is running all the time. Also my network is made of my main pc and virtual machines, I never connect the laptop or other computers. So why do i need avahi? Is it safe to uninstall?

As far as I am aware, avahi-daemon is set to run by default.

There is a nifty little utility available in Synaptic called chkconfig which shows you which services are running as well as the runlevels. You can also use it to start/stop services. Run this to see which services are running:

```
chkconfig --list
```This link has more information as well as a list of services that may be disabled:

[http://www.cyberciti.biz/faq/linux-default-services-which-are-enabled-at-boot/](http://www.cyberciti.biz/faq/linux-default-services-which-are-enabled-at-boot/)

---

### Post by revered on 2010-07-04
avahi shows "off" for all runlevels. Could it being run by:  /etc/network/if-down.d/avahi-autoipd /etc/network/if-post-down.d/avahi-daemon /etc/network/if-up.d/avahi-autoipd /etc/network/if-up.d/avahi-daemon  ?  btw, I cant modify services with chkconfig name on/off, it shows me "script you are attempting to invoke has been converted to an Upstart" for everything, I had to use update-rc.d to enable ufw.

---

### Post by Rubi1200 on 2010-07-04
My apologies! You are right, Upstart controls init.

The way to go, I believe, is  /etc/init.d/"name of service" start/stop etc.

---

