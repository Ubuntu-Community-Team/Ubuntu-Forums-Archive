---
title: "Network not working"
date: 2006-03-24
forum: General Help
---

### Post by chylee on 2006-03-24
Since I've update up system to the latest version of kde 3.5.1 I have been having problems with my network. I do have a duel boot machine with windows xp as the other operating system and the network works fine. On my network I do have several computers connected to a router and that is connected to the internet. When I decided to upgrade my kde to the latest version there was a couple of other packages that got upgraded as well like wine. I can not get access to internet or the computers on my network and have no IP address. Below is a list of info that I have gathered from my system. Can you help me?

```
chylee@nebuchadnezza:~$ sudo mii-tool eth0
SIOCGMIIPHY on 'eth0' failed: Invalid argument

chylee@nebuchadnezza:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:50:8D:FD:0A:CC
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:23 Base address:0xc400

chylee@nebuchadnezza:~$ lspci | grep Eth
0000:00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)

chylee@nebuchadnezza:~$ lsmod | grep mii
mii                     5248  3 via_rhine,8139too,8139cp

```
```
/etc/network/interfaces
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
```

---

### Post by Prospero2006 on 2006-03-24
Try this command:

dhcpcd eth0

Pros

---

### Post by chylee on 2006-03-24
I don't have dhcpcd installed on my system.

---

### Post by Barrakketh on 2006-03-24
Try "sudo dhclient eth0"

---

### Post by chylee on 2006-03-24
I try "sudo dhclient eth0". This is the results

```
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Listening on LPF/eth0/00:50:8d:fd:0a:cc
Sending on   LPF/eth0/00:50:8d:fd:0a:cc
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by fdoving on 2006-03-24
You should try to use eth1 instead. Looks like you have two network cards. The first module loaded chooses eth0 for it's network card. Second chooses eth1. Maybe the order the modules are loaded got mixed during a update.

You can try to add these three lines at the end of your /etc/network/interfaces :

# Second network card.
iface eth1 inet dhcp
auto eth1


Then try to restart networking: sudo /etc/init.d/networking restart


Hope this helps!

- Frode

---

### Post by chylee on 2006-03-24
Thank for you suggestion. I try it but that didn't work. What I have notice is that both my network cards are labelled eth0 & eth2 the primary card that is connected to the router is labelled eth0 and the other card is labeled  eth2 which is not connected. I checked this in window xp using 'ipconfig' and comparing mac addresses. This was not the case before I updated ubuntu. The second card was connected to eth1 I also try to use eth2 as the second network card that didn't work either. Below is the result a get when I type ifconfig -a.

```
eth0      Link encap:Ethernet  HWaddr 00:50:8D:FD:0A:CC
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:23 Base address:0xc400

eth2      Link encap:Ethernet  HWaddr 00:06:4F:16:B8:43
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xa400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:869657 (849.2 KiB)  TX bytes:869657 (849.2 KiB)
```

---

### Post by binarysleeper on 2006-03-24
I'm experiencing the same problem :-? , most notably the "Network is Down" message from dhclient. The PC is dual boot and the WinXP install gets the DHCP lease no problem, ergo no HW prob. It was working fine until I ran a full upddate today.
If anyone has any ideas I'd be most greatful.

TIA,

---

### Post by binarysleeper on 2006-03-24
chylee, on a hunch can you check your  */var/log/dpkg.log* and see whether dhcp3-common and friends were updated today (or whenever you did your last update)? This may be a dhcp related issue. 

Cheers,

---

### Post by Barrakketh on 2006-03-24
Could give us the output of  "ifup -n eth0" and "route"?

---

### Post by binarysleeper on 2006-03-24
route table is empty
ifup -n eth0 gives:

[I]run-parts /etc/network/if-pre-up.d
dhclient -pf /var/run/dhclient.eth0.pid -lf /var/run/dhclient.eth0.leases eth0
run-parts /etc/network/if-up.d[/I]

had to do an ifdown first to get it to do anything.

Cheers,

---

### Post by Barrakketh on 2006-03-24
Just something to try:
```
route add -host 255.255.255.255 dev eth0
```
Try running "dhclient eth0" after that.

---

### Post by chylee on 2006-03-24
> "Could give us the output of "ifup -n eth0" and "route"?"
Barrakketh
This is what I got.

```
chylee@nebuchadnezza:~$ ifup -n eth0
ifup: interface eth0 already configured
chylee@nebuchadnezza:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

> "chylee, on a hunch can you check your /var/log/dpkg.log and see whether dhcp3-common and friends were updated today (or whenever you did your last update)? This may be a dhcp related issue.
"
binarysleeperThis is what I found.
```
2006-03-24 00:58:39 upgrade dhcp3-client 3.0.2-1ubuntu6 3.0.2-1ubuntu7
2006-03-24 00:58:39 status half-configured dhcp3-client 3.0.2-1ubuntu6
2006-03-24 00:58:39 status unpacked dhcp3-client 3.0.2-1ubuntu6
2006-03-24 00:58:39 status half-installed dhcp3-client 3.0.2-1ubuntu6
2006-03-24 00:58:39 status half-installed dhcp3-client 3.0.2-1ubuntu6
2006-03-24 00:58:39 status unpacked dhcp3-client 3.0.2-1ubuntu7
2006-03-24 00:58:39 status unpacked dhcp3-client 3.0.2-1ubuntu7
2006-03-24 00:58:39 upgrade dhcp3-common 3.0.2-1ubuntu6 3.0.2-1ubuntu7
2006-03-24 00:58:39 status half-configured dhcp3-common 3.0.2-1ubuntu6
2006-03-24 00:58:39 status unpacked dhcp3-common 3.0.2-1ubuntu6
2006-03-24 00:58:39 status half-installed dhcp3-common 3.0.2-1ubuntu6
2006-03-24 00:58:39 status half-installed dhcp3-common 3.0.2-1ubuntu6
2006-03-24 00:58:39 status unpacked dhcp3-common 3.0.2-1ubuntu7
2006-03-24 00:58:40 status unpacked dhcp3-common 3.0.2-1ubuntu7
```

---

### Post by binarysleeper on 2006-03-24
Right, sorted!
Uninstalled dhcp3-client and dhcp3-common
set up manual IP config by editing /etc/network/interfaces commenting out 
*iface eth0 inet dhcp*
and replacing it with:
[I]iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx[/I]
rebooted (just to make sure, maybe uneccessary)
Fired up Adept, ran the fetch updates
Re-installed dhcp3-client and dhcp3-common.
Used GUI to switch back to DHCP

All working now, and hopefully it will stay that way.

Thanks to all who tried to help.

---

### Post by chylee on 2006-03-25
Yes that sorted the problem. Let me thank all who help me fix this problem. specially binarysleeper who came up with the solution. I did have a little problem which I did solved. I thought I'll let you know. 

After I created the static connection, I rebooted the system as was instructed. The internet was back and I could also access the other computers on the network. I installed the dhcp3-client and dhcp3-common and used the GUI (which was the control center) to reestablished the dhcp for eth0 then I rebooted. To fined that there was no internet connection, no network access. Back to square one. But it turns out that when using the GUI it created in '/etc/network/interfaces' 
```
iface eth0 inet dhcp
auto eth0
```
which is what I wanted, and also wrote
```
iface eth2 inet 
```
which led to the network not working the second time around. All I did was to commented out that line and now it's working fine.

Just thought I'll let you know.

---

### Post by binarysleeper on 2006-03-25
Glad you got it working Chylee. I can't help wondering how many other people had this problem, or if it was just us.

Cheers,

---

### Post by QwUo173Hy on 2006-03-25
[QUOTE=binarysleeper]Glad you got it working Chylee. I can't help wondering how many other people had this problem, or if it was just us.

Cheers,[/QUOTE]
Ive had this problem for days since upgrading. And I'm sure many others do too, but they dont have an internet connection to find help! I'll try the advice here now. This will leave me with a static connection. But if I reinstall dhcp3, surely I will be back to square one?

Regards,
Jarlath

<edit> I've just tried the advice but it didnt work for me. I have a wireless network card, so I am using wlan0, which is the name of the interface. In place of the xxx.xxx.xxx.xxx above I have inserted the actual IPs for those fields as reported by my router. Is there anything else I'm doing wrong?

I uninstalled dhcp3-client. I have the old dhcp-client but adept wont let me install it, even though its on the kubuntu CD and doesnt require an internet connection.
</edit>

---

### Post by binarysleeper on 2006-03-25
Hi Jarlath, I suspect my original install of dhcp3.* was flawed in some way, and the re-install sorted it out.
When you say you've replaced the values with the ones as reported by your router, I'm assuming you have something like this:
[I]address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1
[/I]
obviously with values appropriate to your network. If this then works you can run fetch updates in adept and then re-install dhcp3 et al.
If this doesn't work you can probably install the ones off the CD but I think you have to edit your adept sources so only the CD is enabled and then run fetch updates, and then you can re-install dhcp3 from the CD. This is guesswork on my part, so if anyone knows different please say so.

You also mention you a using Wireless LAN so you may need to set something else to make sure you associate with your Wireless Access Point. I'm not familiar with setting up wlan manually, but I bet if you search the forums there is a thread telling you how to do it.

Good luck and let us know how you get on.

---

### Post by QwUo173Hy on 2006-03-26
Thanks Binarysleeper. I dragged the .deb from the CD to the desktop and right clicked on it (kde) and choose to install it. (This didn't work from the CD for some reason). Then I simply ran `dhclient wlan0` and I was good to go.

I was dreading having to wipe my almost perfect installation - thanks a lot!

Jarlath

<edit>I should mention that I am using the dhcp-client from the install CD (breezy) and I will not update this time. I think thats what caused my problem.</edit>

---

### Post by linux_owns on 2006-03-29
I have the exact same problem. Same everything, and as far as i can tell i think the issue is in the ipv6. when i go into firefox and about:ipconfig  then i click true on network.dns.disableipv6.. my firefox works. However no other program such as gaim can get onto the internet sill.  I followed the direction in editing the /etc/modprob.d/aliases and turning of ipv6 but still no go.
if you figure this out, alot of us have this issue.
thanks,

---

### Post by binarysleeper on 2006-04-01
[quote=linux_owns]I have the exact same problem. Same everything, and as far as i can tell i think the issue is in the ipv6. when i go into firefox and about:ipconfig  then i click true on network.dns.disableipv6.. my firefox works. However no other program such as gaim can get onto the internet sill.  I followed the direction in editing the /etc/modprob.d/aliases and turning of ipv6 but still no go.
if you figure this out, alot of us have this issue.
thanks,[/quote]

A few questions:

1. How did you install Firefox?

2. Have you tried basic diagnosis with ICMP utiliities?
If not try```
ping www.google.com
``` and see if you get a reply.

3. How are your network settings confgured? Statically or via DHCP (automatically). Can you post the contents of your /etc/network/interfaces

That's enough to get started with.

Cheers,

---

