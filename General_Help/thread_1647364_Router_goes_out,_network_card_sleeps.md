---
title: "Router goes out, network card sleeps"
date: 2010-12-17
forum: General Help
---

### Post by DunZH on 2010-12-17
Hi peeps, I really need some help here.  I am just at the edge to be honest.

Running 9.10 on the computer I am having a terrible time with.

**_Intro_**

I have a small office of 5 comps. I had a guy come in to change the router to a bigger one, to go from 4 to 8 outlets.  I was changing the service, so first we went to the new company's smaller router and then to the bigger one.

Well, my old Dell and another older box never could get reconnected after the guy pulled out the smaller one and put in the bigger one.  First migration was fine though.

I believe I have seen this problem before.  I have had several instances of weird internet outages involving single (or worse, a pair of) machines that eventually can go back online.  There are some serious bugs in NetworkManager I think which are putting these devices to sleep.[B][U]

Symptoms[/U][/B]

Symptoms I have already seen a lot around here.  Yes, I have lights where the line goes in.  The system will try to get a dhcp lease and then give up, telling me I am disconnected. That's it.  I tried to install wicd on the machine that I reinstalled (again to 9.10), but it was the same, no way to get an IP address.

I have nothing in the networkmanager.state file at all.  My nm.config.settings has a no-auto-default:00:16:82:XX:XX line.

And of course in frustration I deleted the eth0, so now I had to make a new one, and its not default.  :frown:
[U][B]

Obligatory Begging[/B][/U]

Anyway, I am really begging for some help. There is no way two machines have the same hardware problem at the same time.  Plus, this is the third time in 6 months I have had two machines with connection problems, where we were checking lines against windows machines and wondering about hardware.

I am already resigned to re-installing on the Dell and hoping it goes ok (its really old). And on the other box (a server) I even re-installed multiple times and it still won't work at all, same symptoms.  So I am worried at this point that both might be fuXXored by this bug.

Help?  #-o

---

### Post by never say never on 2010-12-17
Can you configure a static IP and get on the network?  That will confirm real quick that it is likely not a hardware issue and is most likely some sort of configuration issue.

 Have you tried connecting to a port on the router that you knows receives DHCP?  The router could be configured to have certain ports as a separate VLAN or some other strange configuration.  Do you have the ability to look at the routers configuration?  

Disconnect all other systems and check one that you are having trouble getting connected to a port on the router that you know has received a DHCP address, does that help?

I have seen systems which have IPV6 configured fail to get IPV4 addresses, might disable IPV6 (if it is enabled and you don't need / use it) and see if that helps.

Other than that can you provide more details?  Router model?  IS DHCP served by the router, or another device on the network?  Running NAT?  Looking for Internet IPs or Private IPs?  If it's internet IPs number available may be limited by the ISP.  More details about configuration and physical setup would be  a big help here.

---

### Post by never say never on 2010-12-17
Another thought.  I use Dell computers (about 80 or so) and have a few that seem to have connectivity problems when connecting to a POE device.  I have had to add NICs to these machines to resolve intermittent connectivity issues.

---

### Post by dcstar on 2010-12-17
> **DunZH said:**
> 
.......
Anyway, I am really begging for some help. There is no way two machines have the same hardware problem at the same time.  Plus, this is the third time in 6 months I have had two machines with connection problems, where we were checking lines against windows machines and wondering about hardware.
.......

Install the **ethtool** package on the problem PCs and manually set things like Flow Control to off and turn off other Auto settings like link speed.

If the particular network cards are not auto-negotiating correctly with the switch then problems like this arise.

---

### Post by DunZH on 2010-12-18
Thanks people for the support, it is really appreciated.  :D

As I said I am willing to re-install on the Dell, but I am afraid this problem will not be solved by reinstall.  As I said on the other computer reinstalling has not helped, and that is a box that I have successfully installed and used multiple times. (That situation is not urgent and its complicated by a second networking card in there, I don't want to confuse the issues any more than they are already.)

As I mentioned before I deleted eth0 eventually out of frustration.  I made a new one but it seems not to work, when I used ethtool eth1 (or eth0) it said that interface doesn't exist, and it doesn't have the MAC address in the interface info.

So that just complicates the problem.

Here is some info to help, I was tired and really unhappy when I wrote the first post:

_**ifconfig -a**_

```
dunzh283@dunzh283-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:76:b0:24:3a  
          inet6 addr: fe80::216:76ff:feb0:243a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:46 dropped:0 overruns:0 frame:46
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2862 (2.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


_**lspci**_

```
dunzh283@dunzh283-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
```


_**cat /etc/network/interfaces**_

```
dunzh283@dunzh283-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

**_NetworkManager/nm-system-settings.conf_**
```

dunzh283@dunzh283-desktop:~$ cat /etc/NetworkManager/nm-system-settings.conf
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

no-auto-default=00:16:76:b0:24:3a,

[ifupdown]
managed=true
```


The router is a 'Mercury', some off brand from China I guess.  But everything is enabled, DHCP and so on.

See anything useful here?

Thanks once again.  :KS

---

### Post by never say never on 2010-12-18
Well I think the errors on eth0 speak to a few possibilities.  Show 13 TX packets and 46 Errored RX packets.  So the question is why are they error-ed?

Have you tried this system hooked to a different port on your router?

Have you tried manually setting speed and duplex (to match and not auto detect) at both the computer and the router?

Have verified the network cable is good?

Any bent pins in any jacks?

I am thinking it is a speed / duplex issue, or bent / bad jack.

Have you tried configuring a static IP and Gateway?  Does it work then??

Wireshark might be able to give you an idea of what might be wrong.  Without seeing this in real time it looks like maybe you are sending DHCP requests and the replies are corrupted.

---

### Post by DunZH on 2010-12-19
Well, I installed windows because I just cant wait to fix this.  I will dual boot it and probably never use the windows side once the internet is fixed in ubuntu.

When I installed, I had to install the drivers for the ethernet, and it didn't work after that (you have limited connectivity...), and dhcp wouldn't give me an address.

But, when I changed the speed to 10 / duplex it works! :popcorn:
I do wonder why the other computers do not have any problems now (they are new hp boxes) but I don't really care at this point as long as I can get online at work. The pain of re-installing is nothing compared to the pain of troubleshooting.

And I wonder why the new router caused this problem, but right now I guess I don't care so much, just hope to get my comp back to a useful state!

Thanks neversaynever and dcstar, appreciate your help!

:P

Annnddd....

I reinstalled ubuntu 9.10 and had no problems, once I used ethtool to change the speed to 10 full duplex and turned auto negotiate off.  Guess the new router needed that. Apparently that was the problem the whole time...

---

