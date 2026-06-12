---
title: "Virtual Machine problem: DNS not working?"
date: 2011-06-08
forum: General Help
---

### Post by AnimaStone on 2011-06-08
Hello all,

I'm having a problem with my Ubuntu VMs. In school, we had to set up a firewall (2 network adapters: 1 NAT and 1 on vmnet5), a server (1 network adapter: vmnet 5) and a client (1 network adapter: vmnet5). The firewall has access to the internet and the server has to go through the firewall to access the internet. The client connects to the server and can then go on the internet via the firewall.

I decided to recreate the setup by repeating the steps at home. However, vmnet5 does not seem to work properly on my PC at home (my server complains about there not being a dhcp network), so I used the 'host-only' option in the vm's settings.

I do have a problem now: I can PING from my server to my firewall and the other way around, and I can PING to IP addresses but not to, for example 'google.be' (which works on my firewall but not on my server!). I don't really know how to fix this. It wouldn't be much of a problem, but 'apt-get update' and 'apt-get install program' do not work either (and I need this to install 'bind9' and 'dhcp3' for my excercises for school).

**Here is what I do:**

*The username to my virtual machines are always "student".*

I first created the firewall. I created a shellscript to start up my firewall:
```
vim /home/student/start-firewall.sh
#!/bin/bash
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```And I change the access to start-firewall.sh with 'chmod 766 start-firewall.sh'

Next, I set up a static IP-address for my firewall:
```
sudo vim /etc/network/interfaces
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
        address 172.16.1.1
        netmask 255.255.255.0
```I then go to my server and set up a static IP address and a standard gateway:
```
sudo vim /etc/network/interfaces
auto eth0
iface eth0 inet static
        address 172.16.1.2
        netmask 255.255.255.0
        gateway 172.16.1.1
```I then do the following on both my server and firewall:
```
sudo /etc/init.d/networking restart
```When I PING from my firewall to either 172.16.1.2 or google.be, it works. When I PING from my server to 172.16.1.1 it works, but a PING to google.be does not work.

I have no clue really why they let us use vmnet5 (they never explained, I asked the teacher but he doesn't know either, so I'm quite stuck here!). I also asked him about the host-only problem but he didn't know either.

Thank you in advance! :)

---

### Post by collisionystm on 2011-06-08
So you have 2 network adapters on your firewall? You need to find the IP of eth0. 

I am sure if you do a traceroute, you will see the traffic is going out eth0

sudo apt-get install traceroute

traceroute google.com

try adding this line to your iptables

iptables -A POSTROUTING -j SNAT --to-source ETH0IPADDRESS

---

