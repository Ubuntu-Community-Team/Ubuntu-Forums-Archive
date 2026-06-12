---
title: "Network with XP"
date: 2005-02-26
forum: General Help
---

### Post by RadixLecti on 2005-02-26
Hi, I have one computer running Ubuntu and one running XP. In the Ubuntu comp, I have two lan-cards, and I was wondering how I would go about letting the laptop running XP connect to the internet via the Ubuntu comp?

Preferably a step-by-step instruction, I still feel like a Linux-noob. ;)

---

### Post by nemin on 2005-02-26
[QUOTE=RadixLecti]Hi, I have one computer running Ubuntu and one running XP. In the Ubuntu comp, I have two lan-cards, and I was wondering how I would go about letting the laptop running XP connect to the internet via the Ubuntu comp?

Preferably a step-by-step instruction, I still feel like a Linux-noob. ;)[/QUOTE]
I think this post: [http://www.ubuntuforums.org/showthread.php?t=15703](http://www.ubuntuforums.org/showthread.php?t=15703) will help you, especially the second post. Not a real step-by-step instruction, but not really complicated...

---

### Post by RadixLecti on 2005-02-26
Thanks, I've tried it, still having problems making it work.
Darn, drat and all that.

---

### Post by Jad on 2005-02-26
You have two computers,
**Computer A: **
Ubuntu with 2 Eth Cards
Eth0 Connect to your ADSL modem
Eth1 Connect to your B computer

**Computer B:** Windows XP

Computer A Steps:
1-) Computer -> system configuration -> Networking
2-) Select Eth1 properties
IP Address: 192.168.1.100
Subnet mast: 255.255.255.0
Gateway: 10.0.0.138 Assuming its your ADSL modem IP
Press Ok, Do not activate it yet.

Now Computer B Steps:
Start -> control panel -> networks
Internet protocol (TCP/IP) -> properties
Tick use the following IP address
IP Address: 192.168.1.101
Subnet mast: 255.255.255.0
Default gateway: 192.168.1.100 
Preferred DNS server: 10.0.0.138 which is your ADSL modem IP address in our example

I'm not sure but you may have to reboot WINDOWS XP couple of times to get it working preperly.

now you are done, in case it didn't work 
Try to ping A from B and B from A 
Try to ping your Modem IP address from B 
Try to stop your firewall while setting it up & troubleShooting
I had problem with setting up Firestarter after setting up the network, so I had to remove it "COMPLETE REMOVAL" then re-apt it, and it auto configured itself.

in computer A type
sudo iptables -t nat -L
sudo cat /proc/sys/net/ipv4/ip_forward (1 enabled )

---

### Post by RadixLecti on 2005-02-26
[QUOTE=Jad]You have two computers,
**Computer A: **
Ubuntu with 2 Eth Cards
Eth0 Connect to your ADSL modem
Eth1 Connect to your B computer

**Computer B:** Windows XP

Computer A Steps:
1-) Computer -> system configuration -> Networking
2-) Select Eth1 properties
IP Address: 192.168.1.100
Subnet mast: 255.255.255.0
Gateway: 10.0.0.138 Assuming its your ADSL modem IP
Press Ok, Do not activate it yet.

Now Computer B Steps:
Start -> control panel -> networks
Internet protocol (TCP/IP) -> properties
Tick use the following IP address
IP Address: 192.168.1.101
Subnet mast: 255.255.255.0
Default gateway: 192.168.1.100 
Preferred DNS server: 10.0.0.138 which is your ADSL modem IP address in our example

I'm not sure but you may have to reboot WINDOWS XP couple of times to get it working preperly.

now you are done, in case it didn't work 
Try to ping A from B and B from A 
Try to ping your Modem IP address from B 
Try to stop your firewall while setting it up & troubleShooting
I had problem with setting up Firestarter after setting up the network, so I had to remove it "COMPLETE REMOVAL" then re-apt it, and it auto configured itself.

in computer A type
sudo iptables -t nat -L
sudo cat /proc/sys/net/ipv4/ip_forward (1 enabled )[/QUOTE]
 Thanks for the thorough walkthrough.
I have a problem though. Since I'm connecting through a fibre-lan, I don't have a static IP, it changes. 
This may be noobish, but how do I work around the problem?

---

### Post by Jad on 2005-02-27
What static IP your are talking about ?
Your Internal (Network) IP address ? 192.168.1.100/1 ?
You don't need to have a static Internet IP address for Internet connecting sharing.

---

### Post by RadixLecti on 2005-02-27
Sorry, I meant the part where, in your example, you put in the ADSL modem IP (the gateway on A and preferred DNS on B).
Heh, I feel stupid. ;)

---

### Post by Jad on 2005-02-27
and now solved?

---

### Post by RadixLecti on 2005-02-27
Nope, I still don't know what to put in the gateway of A and the preferred DNS of B, since those change almost every time I start up my computer.
Dynamic DNS is the pits. 
Is there a workaround for this problem? I've checked, and my ISP doesn't provide static IP/DNS.

Oh, and I tried to put in my temporary IP (as given by whatismyip.com). That didn't work either.

---

### Post by can8dnSix on 2005-02-27
[QUOTE=RadixLecti]Nope, I still don't know what to put in the gateway of A and the preferred DNS of B, since those change almost every time I start up my computer.
Dynamic DNS is the pits. 
Is there a workaround for this problem? I've checked, and my ISP doesn't provide static IP/DNS.[/QUOTE]

I might be confused but can't you just make computer A the DNS server... to reference itself then have it reference your host? I forget how to do it, it's been awhile but you could configure /etc/resolv,conf 

I think you can add

search #hostname, whatever you use to get you internet#
nameserver 192.168.0.1
nameserver 127.1.1.1

I'm not totally positive that it works, but I remember having to do something like that, when sharing the internet with a dynamic DNS some years ago back in my college days. 

Can8dnSix

---

### Post by Jad on 2005-02-28
first, Can A ping B and B ping A ? 
in your terminal type the follow commands ( and please paste the result here)
```
route -n 
```
```
sudo iptables -t nat -L
```

---

### Post by RadixLecti on 2005-02-28
Okey, here it is:

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
213.112.126.0   0.0.0.0         255.255.255.192 U     0      0        0 eth0
192.168.1.0     0.0.0.0             255.255.255.0   U     0      0        0 eth1
0.0.0.0         213.112.126.1           0.0.0.0         UG    0      0        0 eth0




sudo iptables -t nat -L

Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by RadixLecti on 2005-03-01
[QUOTE=RadixLecti]Okey, here it is:

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
213.112.126.0   0.0.0.0         255.255.255.192 U     0      0        0 eth0
192.168.1.0     0.0.0.0             255.255.255.0   U     0      0        0 eth1
0.0.0.0         213.112.126.1           0.0.0.0         UG    0      0        0 eth0




sudo iptables -t nat -L

Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination[/QUOTE]
 *bump*

---

