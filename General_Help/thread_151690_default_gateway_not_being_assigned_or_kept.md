---
title: "default gateway not being assigned or kept"
date: 2006-03-28
forum: General Help
---

### Post by twiggy on 2006-03-28
Hey all,

this is my first time here so sorry if i do anything wrong or say something similarly.

My problem is this;

I have an unbuntu box with two network cards.  One of which has a netgear ADSL modem attached.  This connection successfully gets an IP address etc for the WAN connection.

The second card is a on a class C home network, i.e. 192.168.0.1.For some reason a default route out to the first network card is not being set, if I set it usingroute add default gw xxx.xxx.xxx.xxx where the IP address is the address of the external connection then I can get a connection just fine.However route then forgets this default gateway (quickly), I've looked in the syslog and found that the DHCP client is probably causing this to happen.

If I connect the modem to a Windoze box it works just fine.

My questions are these;

1. Should ubuntu be setting the default gateway route by itself?  If so why do you think it isn't?

2. In the Gnome configuration for network there is an option to set a specific interface as a gateway, when I set this, it seems to forget by the time I re-load the applet and doesn't solve the problem.  Is it possible to set this manually in a configuration file so that eth1 is the default gateway?

3. How can I make this all work the way it should?

Thanks,

Twiggy

---

### Post by hajk on 2006-03-28
It should be possible to set up both interfaces with the System -> Administration -> Networking tool under Properties. And, as you've already seen, the default route can be chosen in the first window of the tool. Any settings are then written to the /etc/network/interfaces file, you may have to do some clean-up there. Can you show what this file looks like now?

---

### Post by twiggy on 2006-03-28
hey hajk,

thx for the help in advance.  excluding the comments here's whats in /etc/network/interfaces:

[PHP]auto lo
iface lo inet loopback

mapping hotplug
        script grep
        map eth1

iface eth1 inet dhcp

auto eth1

iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0

auto eth0[/PHP]

hope this helps,

fanks again :)

---

### Post by hajk on 2006-03-28
OK, also the outputs of "sudo route -n"  and "sudo ifconfig" would be useful.

---

### Post by twiggy on 2006-03-28
sorry for slow reply having to swap wires around to do stuff then post the results :P

curiously ifconfig eth1 up and the same with down does not reset the network card i have to go into gnome and use the deativate and activate command.

anyway, here is the output from them both:

[PHP]root@betty:/home/jon# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
86.133.167.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
root@betty:/home/jon# ping google.com
ping: unknown host google.com
root@betty:/home/jon# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:C7:0D:EF:C5
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:c7ff:fe0d:efc5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4967 (4.8 KiB)  TX bytes:11851 (11.5 KiB)
          Interrupt:21 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr 00:08:54:3B:F9:26
          inet addr:86.133.167.XXX  Bcast:86.133.167.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe3b:f926/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6800 (6.6 KiB)  TX bytes:5398 (5.2 KiB)
          Interrupt:19 Base address:0x4400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9035 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9035 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:547890 (535.0 KiB)  TX bytes:547890 (535.0 KiB)[/PHP]

Twiggy

---

### Post by hajk on 2006-03-28
There should indeed be a default line like
0.0.0.0      86.133.167.xxx       ...     eth1
in the output of route -n, where 86.133.167.xxx is the IP of your ADSL device.
And "sudo route add gw 86.133.167.xxx " doesn't do it? Have you prefixed with "sudo"?

All I can suggest is to go into the Gnome network manager, first deactivate both interfaces, then in Properties select DHCP again for eth1 and activate it (you can then select eth1 as gateway). This should bring up the default in the output of
"sudo route". 

Then you can also select the eth0 interface, in Properties select static and the IP 192.168.0.2 and as gateway the other machine on this LAN, then activate it.
I've done something similar with a printer being on a different LAN from my DSL router, with a dedicated route to the printer, and having DHCP take care of the default route to the router.

---

### Post by twiggy on 2006-03-28
ok so i had a go,

with the sudo route add gw xx.xx.xx.xx i get the following error:

gw: Host name lookup failure :(

this is the results i get from only having eth1 active.. i run route once waited around 30 secs and ran it again and one of the routes disappeared.  i am not sure whats happening here really

root@betty:/home/jon# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
root@betty:/home/jon# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
86.133.10.0     *               255.255.255.0   U     0      0        0 eth1
root@betty:/home/jon#

i hope this makes more sense to you than it does to me :(

p.s.. sorry for the bad formatting on the routing table

---

### Post by hajk on 2006-03-28
I'm confused now as well, one moment eth1 is on your 192.x.x.x LAN, the next on the 86.y.y.y WAN...

I would disregard eth0 for now, and focus on getting the eth1 interface going as default route to the internet. You may have to take out the "eth0 auto" line in /etc/network/interfaces" to prevent it from running interference.

Not being able to get a host name lookup is a DNS problem, but your ADSL device should take care of that. Are you running a firewall, like FireStarter, on the eth1 interface? That would cause DNS problems, unless port 53 UDP/TCP (nameserver service) is open...

---

### Post by twiggy on 2006-03-28
ok so we have some progess here,

i commented out "auto eth0"

restarted the network by "/etc/init.d/networking restart"

did the routing and still didnt have the gateway information.

but when i did the following command it got it and dns lookups worked, firefox worked, telnet ssh etc all worked.. and it didnt drop that gateway.. but when i restarted networking again it looses the gateway... anyway the command i used was:

"route add default gw xx.xxx.xxx.xx"

so a couple of questions really i think:

1.. what would happen when my ip changes?

2.. how do i get it to keep this gateway? i do admit this is gonna be running as a server (when she eventually works) so it will be on most the time, but it does not seem a good solution to have to add the gateway each time ip changes or server is rebooted.

oh and THX for the help :)

Twiggy

---

### Post by twiggy on 2006-03-28
ok so i tried running dhclient when the gateway was added and the ip was renewed but gateway was lost.

so from what i can see is i need a way of preminately binding a default gateway to a device (eth1) rather than an ip address.  any ideas pwease.

thx

Twiggy

---

### Post by twiggy on 2006-03-29
/bump... hoping some one maybe able to answer the question here, hajk has been very helpful and we have had progress, i can keep a gateway, but i have to manually add it with the ip address.

thx 

Twiggy

---

