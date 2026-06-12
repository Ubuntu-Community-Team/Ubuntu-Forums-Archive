---
title: "ssh port 22: no route to host"
date: 2011-10-25
forum: General Help
---

### Post by JaySeeJC on 2011-10-25
Can't ssh to my local machine via it's public IP address. I have set up my router to forward traffic on port 22 to my desktop and still can't access it via it's public IP. I CAN ssh using localhost and my local IP. Not sure what output you need, feel free to tell me. :)

> ssh -Xvvv [email]root@my.IP.goes.here[/email]
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to my.IP.goes.here [my.IP.goes.here] port 22.
debug1: connect to address my.IP.goes.here port 22: No route to host
ssh: connect to host my.IP.goes.here port 22: No route to host

NOTE: I do not have access to another computer at this time, and so cannot test if this is a problem locally or not. If you want to test I can send you my public IP via pm

---

### Post by JaySeeJC on 2011-10-25
Looking around, I found people giving the output of the following...

```
jon@jon-OptiPlex-GX520:~$ sudo !!
sudo iptables -L -v --line-numbers
[sudo] password for jon: 
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
num   pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
num   pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
num   pkts bytes target     prot opt in     out     source               destination         

```

---

### Post by Vgui on 2011-10-25
Looks like you don't have any rules setup for iptables, so that may be blocking it. Also your router could be blocking that port, so I'd check there too. Also it may seem obvious but double check that sshd is even running. "ps -ef | grep sshd" should return the service if it's running.

To open a port in iptables I've long used:

```
iptables -I INPUT -i eth0 -p tcp --dport 22 -j ACCEPT
```

Where "eth0" is your device (found via 'ifconfig') and --dport is the port you want.

As a side note I highly recommend moving ssh to a non-standard port. I bumped it up to port 28 and the number of anonymous dictionary attacks dropped from several hundred a month to zero. Also you might want to look into public key authentication for further security.

---

### Post by JaySeeJC on 2011-10-25
> **Vgui said:**
> 
As a side note I highly recommend moving ssh to a non-standard port. I bumped it up to port 28 and the number of anonymous dictionary attacks dropped from several hundred a month to zero. Also you might want to look into public key authentication for further security.

Thanks! I will move ssh to a different port once I get it working.

My router is set up to let through port 22, so that's not a problem.

As for you suggestion of running "iptables -I INPUT -i eth0 -p tcp --dport 22 -j ACCEPT" I add a -v flag to it and get the following:


```
sudo iptables -v -I INPUT -i wlan0 -p tcp --dport 22 -j ACCEPT
ACCEPT  tcp opt -- in wlan0 out *  0.0.0.0/0  -> 0.0.0.0/0  tcp dpt:22
```

Also i still get the exact same error from ssh about route not found.

---

### Post by Vgui on 2011-10-25
You could try using Nmap ([http://nmap.org/](http://nmap.org/)) to port scan your own machine and see if port 22 is open, since if it is then the problem likely lies elsewhere.

You could always try SSHing from the local machine to itself. It sounds silly but it might help show you if there is a configuration problem.

Also try looking near the end of /var/log/messages as it should log a bit about SSH.

---

### Post by JaySeeJC on 2011-10-25
i can ssh to myself using both my local fixed IP 192.168.0.11 and localhost. 

as for nmap, here are the results for my public IP (it is shared with others)

```
                                          
jon@jon-OptiPlex-GX520:~$ nmap -A -T4 my.IP.address.here

Starting Nmap 5.21 ( http://nmap.org ) at 2011-10-25 21:35 EDT
Nmap scan report for CPE001372c7bc22-CM001bd7ad40b2.cpe.net.cable.rogers.com (my.IP.address.here)
Host is up (0.088s latency).
Not shown: 997 closed ports
PORT   STATE    SERVICE    VERSION
22/tcp filtered ssh
53/tcp open     tcpwrapped
80/tcp filtered http

Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 3.38 second

```

---

### Post by JaySeeJC on 2011-10-26
OK, still haven't resolved the issue... can anyone help?

---

### Post by e79 on 2011-10-26
I might be mistaken as I'm not a pro when it comes to configure iptables from the command line but:

Is it possible you omitted the 'PREROUTING' rule before the 'FORWARD' rule ? A bit like:

```
${IPTABLES} -t nat -A PREROUTING -p $fw_inproto -i $fw_iface -d $fw_inaddr --dport $fw_inport -j DNAT --to $fw_outaddr:$fw_outport
``````
${IPTABLES} -A FORWARD -p $fw_inproto -i $fw_iface -d $fw_outaddr --dport $fw_outport -j ACCEPT
```

---

### Post by papibe on 2011-10-26
Hi JaySeeJC.

By any chance are you trying to access your public IP from inside your own LAN? If so, that won't work.

The ability to connect to a machine from your local network using its public name, or IP, is called **NAT loopback** (read about it [here]("http://opensimulator.org/wiki/NAT_Loopback_Routers")). Unfortunately most consumer routers don't support it.

The easiest way to test your setup is to go to a Internet cafe, public library, or even better, a friend's house. Another alternative is to use your pnone/tablet 3G connection (not WiFi).

Does that helps,
Regards.

---

