---
title: "strange network problems - please help"
date: 2006-02-11
forum: General Help
---

### Post by nikosft on 2006-02-11
Hi everybody,

I am using ubuntu linux in my laptop. I have connected my latop in my university network. My computer was working fine until two days a go, when all of a sudden I couldn't reach ip's outside my network. I can ping my gateway but I cannot ping anyother ip address. There are two strange things

- when I go to to recovery mode I can ping everything!(including ip addresses outside my network, domain names outside my networks)
- when I switch to windows XP in the same machine I have no problems!

I uninstalled ipv6 but no results!

Here are the ouputs of the commands 
cat /etc/network/interfaces
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth0


ifconfig eth0
> eth0      Link encap:Ethernet  HWaddr 00:03:0D:2E:79:68  
          inet addr:192.16.126.180  Bcast:192.16.126.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:285210 (278.5 KiB)  TX bytes:1649 (1.6 KiB)
          Interrupt:19 Base address:0xd800 
cat /etc/resolve.conf
> search kistaip.net
nameserver 192.16.124.50
nameserver 192.16.125.100

route -n
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.16.126.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.16.126.2    0.0.0.0         UG    0      0        0 eth0

and here is also the ipconfig -all in windows
> 

 
  DNS : kistaip.net

Physical Connection

 DNS . : kistaip.net
Description . . . . . . . . . . . : SiS 900-Based PCI Fast Ethernet Adapter
  Mac Address . . . . . . . : 00-03-0D-2E-79-68
  DHCP . . . . . . . : Yes

 IP Address. . . . . . . . . . : 192.16.126.67
 Subnet mask. . . . . . . . : 255.255.255.0
 DEfault gateway . . . . . . : 192.16.126.2
 DHCP. . . . . . . . : 192.16.126.2
 DNS . . . . . . . . : 192.16.124.50
                                    192.16.125.100


---

### Post by steve.horsley on 2006-02-11
Excellent post, all the relevant info. Well, nearly all. I can't see anything wrong here, it makes me wonder if you have a firewall running. Can you try the command **sudo iptables -L**, and see what you get? If you get a message saying iptables isn't recognised, thern no firewall is running. If you get a long list of conditions, a firewall is running and we can talk about how to correct the rules. A firewall running but allowing everything to pass looks like this:
> steve@StevesPC:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


---

### Post by nikosft on 2006-02-11
Here is the output of the command
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


---

### Post by nikosft on 2006-02-11
I am desparated. I have tried anything but nothing seems to work. Why everything is working properly in recovery mode and not in normal mode? Is there something like system restore in windows?(Although I am quite sure I didn't made anything wrong, the last thing I made was installin Acrobat Reader).

How can i see the programmes that are running in start up, maybe by deactivating one by one, to find the problem.

---

### Post by dcstar on 2006-02-11
Ok, When you use Win-XP, you are using DHCP and you get one IP address.

When you use "normal" Ubuntu, you seem to be using a different IP address (probably the Ubuntu box kept an "old" IP address from a previous connection thinking it didn't need to ask for a new one, but in Recovery Mode it doesn't remember this old setting and does get the correct address).

Your network card Ethernet Address has probably been registered in the **other** network equipment on your subnet under the Windows DHCP IP address, when you use the Ubuntu address the return packets are sent to the (now incorrect) DHCP address.

One solution may be to wait until the other equipment "times out" the ARP entries for the DHCP IP (which will probably go wrong again if you boot up XP), or just force the release and renew of the Ubuntu DHCP with "**sudo dhclient**".

If this works, you may want to put the dhclient command in a startup script to run it on every boot.


PS: I just discovered that running dhclient will overwrite Static IP settings when it gets a DHCP lease - cool!

---

### Post by nikosft on 2006-02-11
I am using DCHP in "normal" ubuntu also. I also tried to obtain a new ip address using in termin dhclient3 with success. But the problem remains. Moreover I can ping the internal network, incuding gateway, so I don't think the ARP cache is the problem.

---

### Post by dcstar on 2006-02-11
[QUOTE=nikosft]I am using DCHP in "normal" ubuntu also. I also tried to obtain a new ip address using in termin dhclient3 with success. But the problem remains. Moreover I can ping the internal network, incuding gateway, so I don't think the ARP cache is the problem.[/QUOTE]
Did you get a new IP address?

The only other thing I can think of is that if you **don't** get a new IP address, some other security device in the network is blocking the old IP address from external access because it believes the lease has expired.

Do a traceroute to an external site and post the results.

PS - I re-wrote my first reply (a few times), it may be more relevant now.......

---

### Post by nikosft on 2006-02-12
Partial fixed.
When I log on in "normal" Ubuntu and change the address manually, it seems to work. When I run "sudo dhclient" the ip address change -but only if I run it once, if try to run it twice, the secod time the address remain the same-but for a strange reason, the problem appears again. It seems also when I am using "sudo dhclient" I am getinng the same 3-4 ip addresses which seems to be banned- as you mentioned above. Moreover whenever I change the ip address (either manually or using dhcp) for a strange reason, I cannot shutdown my pc. When I press shutdown it freezes! When I have the problem traceroute reach only the gateway and then nothing. Finally if run dhclient3 in recovery mode, again I am taking one of those banned addresses. No I am wondering:
-Why in recovery mode initially my machine has a valid address and not in normal mode?
-Why dhclient keeps giving me the same addresses and when I try to run it again it doesn't change the address
-Is it coincidence that whenever I change my ip address manually -in normal mode- I cannot shutdown my pc?

Note also that I was working in the same network without problems fot two weeks now. This problem really appeared out of nowhere

---

### Post by nikosft on 2006-02-12
I uninstall dhclient3 and I reinstalled it and it works,at least for the first reboot :). I do not dare to reboot again until I finish my job!

---

### Post by Peter76 on 2006-02-12
Another solution is to set your dns server to your gateway address. this works for me a lot of times

---

### Post by nikosft on 2006-02-12
I reboot and again the same problems
Peter neither your solution soved the problem
Is it a dhclient bug???

---

### Post by Peter76 on 2006-02-12
I don't think it's a dhclient bug, because you are assigned an ip address and you can ping your internal network..... What's the output of your pings; does it say unknown host, or just keeps quiet?

---

### Post by nikosft on 2006-02-12
it keeps quiet. I am wondering why the dhclient is giving me all the time the same addresses. Is there anything like address cache or somethng similar?What is the lease-file?(In there it is written the address that it gives me most of the time)

---

### Post by nikosft on 2006-02-12
I am quite convinced that it concerns dhclient. For a strange reason it keeps assigning one address. If I assign manually an address to my computer which is valid, after some minutes, dhclient will change it -automatically- to the old bad one. The ony way to work is to assign an address manually and kill the dhclient. any suggestion?

---

### Post by nikosft on 2006-02-12
Here is my conclusion. Everytime dhclient runs it picks the last address it was assigned. It thinks that it is valid, but it is not, this happened due to a network configuration I guess. How can I make dhclient to not perform that step and requesting a fresh new address?

---

### Post by nikosft on 2006-02-13
I am striving by myself and I am desperated for help!Please somebody help me.

I monitored with ethereal the traffic when I am executing dhclient3. I noticed that when my pc requests a new address, it also "proposes" the old one it had. For a strange reason the dhcp server acknownledge it.How can I make dhclient not proposing any address?

I remind you also that in windows xp I have no problem. Neither -expect a few times- in recovery mode.

Fianlly when I kill dhclient and then i restart it I cannot shutdown my pc.

Please say something!!!!!

---

### Post by nikosft on 2006-02-15
Is there at least any official supprot?I am willing to pay, this problem has lead me to great trouble.

---

### Post by nikosft on 2006-02-23
I uninstall dhclient3 and I installed dhcpcd and now no problems! Now my questions are

- How can I make dhcpcd starts on start-up?
- If I don't uninstall dhclient3 how can I prevent it from starting on startup?

---

