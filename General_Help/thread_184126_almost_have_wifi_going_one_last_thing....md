---
title: "almost have wifi going one last thing..."
date: 2006-05-29
forum: General Help
---

### Post by onesojourner on 2006-05-29
I posted this in the dapper forum but its over running right now and it just keeps getting lost.

I have an old dell inspiron 7000 (PII 266) that I installed dapperRC on. I did have breezy but the 4 gig hdd filled up and would not allow the computer to boot... (is that fixed in dapper?) anyways I had wireless working on it sort of. I tried and tried and finally manually configured it during the breezy install and it would work but only on my wireless network. I could never get it to connect to anything else. Its not that big of a deal since the tank of a laptop is mainly stuck under the couch so some one can grab it and check email or such. the card is a d-link DWL-G630. it is detectect and I activated it. in network settings I clicked properties and it would not list the network so I manually typed it in
network name: hartmanhouse
key typer: hexadecimal
wep key: **********
DHCP

I double checked and everything is right. in connection properties wlan1 status is disconnected but signal strength is high 80-90%. whats going on? why will this stupid thing not get on the network?

I ran lspci and found the card

0000:06:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless interface

any thoughts? I thought maybe I would try this network manager that everyone is talking about but how would I do that with no internet connection? I wish they would stick that stuff on the cd. thanks for any help you guys can give.

---

### Post by sadjack on 2006-05-29
I had a similar problem and fixed it with this entry in /etc/network/interfaces

I used "sudo gedit /etc/network/interfaces" to edit the file.

# The primary network interface
iface eth0 inet static
	network 192.168.1.0
	broadcast 192.168.1.255
	# wireless-* options are implemented by the wireless-tools package
	**wireless-mode managed**
	wireless-essid Untitled
	wireless-key1 ********************
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 212.74.112.66 212.74.112.67
	wireless-key ******************
	address 192.168.1.5
	netmask 255.255.255.0
	gateway 192.168.1.254

The line that did it for me was "wireless-mode managed". I obvioulsy have a static IP address allocated to eth0 but I do not see that as the issue. Without the above line I had the exact symptoms as you.

Anyway it may give you an idea.

---

### Post by onesojourner on 2006-05-29
ok I stuck it in there. mine really looked alot different than yours though. still dont have it going though.

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid hartmanhouse
wireless-key **********

iface wlan1 inet dhcp
wireless-mode managed
wireless-essid hartmanhouse
wireless-key **********

auto wla

---

### Post by sadjack on 2006-05-29
Hi

I'm no guru on this but you seem to have a lot of interfaces there, you may of course have more than one card. If you "sudo ifconfig" can you identify which is your wireless card. On my system it shows as eth0. Is there any chance there are erroneous entries there? If there are, perhaps clearing them out will help. Might be a good idea to backup the configuration you have first so at least you can get back to your current state.

Sorry its not the complete answer but hope it helps.

---

### Post by onesojourner on 2006-05-29
ok here is what ifconfig gets

peter@oldlaptop:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7604 (7.4 KiB)  TX bytes:7604 (7.4 KiB)

wlan1     Link encap:Ethernet  HWaddr 00:0F:3D:0B:C4:71
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

peter@oldlaptop:~$

---

### Post by onesojourner on 2006-05-29
[QUOTE=onesojourner]ok here is what ifconfig gets

peter@oldlaptop:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7604 (7.4 KiB)  TX bytes:7604 (7.4 KiB)

wlan1     Link encap:Ethernet  HWaddr 00:0F:3D:0B:C4:71
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

peter@oldlaptop:~$[/QUOTE]


so you think I should make my interfaces file look like this

auto wlan0
iface wlan0 inet dhcp
wireless-essid hartmanhouse
wireless-key **********

iface wlan1 inet dhcp
wireless-mode managed
wireless-essid hartmanhouse
wireless-key **********

auto wla

?

---

### Post by sadjack on 2006-05-29
As I said earlier, I'm no guru at this, but unless you have two cards why do you have refernce to wlan0 and wlan1?

If you only have one card is the reference to two causing some problems? 

If you do have only one try commenting out the other, if ifconfig makes refernce to wlan1, comment out wlan0 and see what happens.

I would try

# The primary network interface
iface wlan1 inet dhcp
# wireless-* options are implemented by the wireless-tools package
wireless-mode managed
wireless-essid Untitled
wireless-key1 ********************
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers *************
wireless-key ******************
gateway *************

You maybe able to comment out dns-nameservers and gateway as well if you are using dhcp.

I'm sue there mybe others with a little more knowledge to help you, but you do not seem to be far off..good luck

Tony

---

### Post by onesojourner on 2006-05-30
I am still not getting any where with this problem. any other ideas?

---

### Post by sadjack on 2006-05-31
ok, i've looked at some other interfaces configs and this is one from a laptop

# static addressing

iface ra0 inet static
address *********
netmask 255.255.255.0
gateway *********
wireless-essid Untitled
wireless-key ***************
wireless-mode managed
wireless-keymode restricted

auto ra0

ra0 being the wireless card detected by Breezy.

Note the addition of wireless-keymode restricted.

Sorry i cannot be more helpful as most of what i have learnt is from trial and error myself.

Ifanyone else out there can help this guy, please jump on board.

Cheers

---

### Post by Imre Mehesz on 2006-06-12
hello, 

i have the exact same problem.. i have signal strength and everything but the properties say: disconnected and i cannot connect to the network/internet

fresh installation by the way, still warm!

if i'll find the solution i'll let you know...

emzmim

---

### Post by Silver Bullet on 2006-06-22
I am having a similar issue.... I can connect to my wireless router but only when I am right beside it. Before Dapper I could go all over my house. I am still looking to resolve this as it is pointless to have wireless when you have to set your laptop on top of the wireless router.:D

---

