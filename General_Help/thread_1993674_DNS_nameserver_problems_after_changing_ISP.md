---
title: "DNS nameserver problems after changing ISP"
date: 2012-06-02
forum: General Help
---

### Post by optikz on 2012-06-02
Hi All,

I'm becoming more and more frustrated with Ubuntu. :( I'm using the Precise Pangolin distro.

I changed ISP provider from Comcast to RCN. While my macbook laptop and Windows PC smoothly embraced the new ISP, my Ubuntu PC couldn't automatically detect the DNS servers.

I have internet but unable to resolve anything.

In /etc/resolv.conf:

nameserver 127.0.0.1
search cable.rcn.com

I've played with gnome-control-center network and tried to force the system to accept the DNS servers of RCN, but it seemed hopeless.

I tried a prepend domain-name-servers to Google DNS in dhclient.conf, but without hope. It still doesn't work!

Does anybody have a clue on how to solve something like this? I need to sort of reset the network settings. 

Seriously, I do not mean to offend, but sometimes I wonder how developers design these things... And we expect people to adopt Linux! (This is mostly mt frustration speaking out!)

Any help would be most appreciated. Thanks.


--optikz

---

### Post by optikz on 2012-06-02
I found that the following commands

sudo iptables -F

sudo /etc/init.d/networking restart


solves the problems for 5 minutes. After that, it can't resolve domain names anymore. Any clues on how to completely reset network settings and fooling the system that I just installed the OS?

--optikz

---

### Post by optikz on 2012-06-02
Again I managed to solve the problem:

Step 1: Disable dns-masq

sudo vim /etc/NetworkManager/NetworkManager.conf

Comment the line

[main]
...
#dns-masq


Step 2: Modify dhclient.conf

sudo vim /etc/dhcp/dhclient.conf

Uncomment the prepend line and add Google DNS servers

prepend domain-name-servers 8.8.8.8, 8.8.4.4;


Step 3: Remove resolvconf 

sudo apt-get remove resolvconf


resolvconf kept overriding the /etc/resolv.conf file. This was a mess. Who the heck designed this #$%$% system?


Anyway, this will help others solve similar issues! I'm saying frankly: I'm really unimpressed with Precise Pangolin.

--optikz

---

