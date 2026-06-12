---
title: "ssh commands execute locally instead of on the remote computer"
date: 2010-07-12
forum: General Help
---

### Post by ldt on 2010-07-12
I can ssh to the remote computer OK, but the commands execute on the local machine, not the remote machine as they should. After much frustration I did the following hoping to clear the problem.
 I turned off all machines on my LAN, the hub and the router. I then rebooted everything in the reverse sequence - cable modem, router, hub, and then the computers. 

Then I reinstalled ssh on both machines.

sudo apt-get purge openssh-server openssh-client
sudo apt-get install openssh-server openssh-client

sshd in now running and port 22 shows on both machines. However the problem persists.


 Lets' call the two machines L for local and R for remote.

from L

ssh R (OK)
ls       (NOT OK – shows the home directory of L not R)


 But if I reverse the order.
 from R

ssh L (OK)
ls      (OK – shows home directory of L)


 It works in one direction but not the other. I'm not sure whether the problem is with the local openssh-client of the remote openssh-server.

---

### Post by ajgreeny on 2010-07-12
If you are currently using the computer names, try their IP addresses instead.

I can't see why your system is doing what it is but this seems worth trying.  You can get the IP addresses of each machine with ifconfig in terminal; mine is 192.168.0.2, as shown below.
```
username@ubuntu1004:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:d8:65:f0:2d  
         [COLOR=Red] inet addr:192.168.0.2[/COLOR]  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe65:f02d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63616 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33595310 (33.5 MB)  TX bytes:13935007 (13.9 MB)
          Interrupt:22 Base address:0xe000
```

---

### Post by ldt on 2010-07-12
Thank you, thank you. This problem has be driving me nuts for about a week. The problem is not exactly the one you suggested but close enough. I had actually tried using ip addresses instead of names but always got the same wrong result. However your suggested command “ifconfig” was the key. The history of this problem was that all had been working fine for about a year until last week we had a thunderstorm which knocked out our Internet service for a couple of days. When it came back on I had this problem. I have three computers behind a hub. Previously their ip addresses were:
 

 192.168.1.102
 192.168.1.103
 192.168.1.104
 

 Now they are  
 192.168.1.101
 192.168.1.102
 192.168.1.103
 

 I updated the /etc/hosts files and all is back to normal.
 

 This experience reminds me of an article I read in last month's “Communications of the ACM” ([http://cacm.acm.org/magazines/2010/6](http://cacm.acm.org/magazines/2010/6)). There is an article titled “The Chaos of the Internet as an External Brain”. He comments that success in AI is now coming from an unexpected source – the chaos of the Internet. I think this is the kind of experience he is talking about.
 

 Thanks again.

---

### Post by bodhi.zazen on 2010-07-12
Consider setting a static IP on your servers, should be able to do this either on the router or on the servers.

As an alternate you could configure a dns server, dnsmasq is very easy to configure and will also do dhcp.

---

### Post by ldt on 2010-07-12
I'm really a network novice I'm just trying to maintain a central version control repository at the moment and I'm new at that. But I love getting expert tips like this. I likely will want to take it to the next level in the future.

Thanks.

---

### Post by bodhi.zazen on 2010-07-12
dnsmask users your hosts file , so it is very simple (easier then maintaining a hosts file on each client).

You can set a static IP with networkmanager.

If you need assistance with either, just ask.

---

