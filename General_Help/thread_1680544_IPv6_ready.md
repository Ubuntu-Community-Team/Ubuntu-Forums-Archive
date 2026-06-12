---
title: "IPv6 ready?"
date: 2011-02-02
forum: General Help
---

### Post by JohnH on 2011-02-02
Hi all,

I've been reading quite a bit lately about the introduction of IPv6 but there has been nothing on readiness for this new protocol.

Is Ubuntu and or Firefox ready to handle this?

Do I need a new modem router? 

Will all IPv4 addresses roll over to v6?

Regards
John

---

### Post by slooksterpsv on 2011-02-02
> **JohnH said:**
> Hi all,

I've been reading quite a bit lately about the introduction of IPv6 but there has been nothing on readiness for this new protocol.

Is Ubuntu and or Firefox ready to handle this?

Do I need a new modem router? 

Will all IPv4 addresses roll over to v6?

Regards
John

1. Ubuntu already has IPv6 capabilities built-in, same with pretty much most if not all Linux distros. It's Windows that's been behind in the game (only with Vista implementing IPv6 (XP you had to use 3rd party programs))

Firefox has been ready to handle it, there's some IPv6 websites out there. You may need a tunnel broker in order to access them or you may be able to already. It varies.

2. Depends on the modem, they may have tunneling capabilities, which translate an IPv4 to an IPv6, so you in essence tunnel through it.

3. That's up to the ISP to decide. Websites will probably keep the IPv4 address, and modems moved to IPv6 or at least have a tunnel broker installed. I can't say for sure.

---

### Post by JohnH on 2011-02-02
thank you for your prompt reply  - much appreciated.

John

---

### Post by mathgeek2000 on 2011-02-02
> **JohnH said:**
> thank you for your prompt reply  - much appreciated.
John

Linux Magazine wrote an article on how to tunnel ipv6 over ipv4, as Comcast has started ipv6 trials.

[http://www.linux.com/learn/tutorials/371742:ipv6-6rd-linux-router-on-comcast-using-ubuntu-maverick-1010](http://www.linux.com/learn/tutorials/371742:ipv6-6rd-linux-router-on-comcast-using-ubuntu-maverick-1010)

You need Ubuntu 10.10 for this, however, and you need to plug directly in to the Cable Modem. In my case, I don't think the modem does IPv6 directly.

---

### Post by misterfixit on 2011-02-16
I've been trying ... really I have!

See this capture:

dave@The-Mighty-Wurlitzer:~$ ip address show

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:1d:92:f0:b4:79 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.100/24 brd 192.168.0.255 scope global eth0
    inet6 fe80::21d:92ff:fef0:b479/64 scope link 
       valid_lft forever preferred_lft forever
3: vboxnet0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 0a:00:27:00:00:00 brd ff:ff:ff:ff:ff:ff

dave@The-Mighty-Wurlitzer:~$ ip -4 route show

192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.100  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.0.1 dev eth0  proto static 
dave@The-Mighty-Wurlitzer:~$ ip -6 route show
fe80::/64 dev eth0  proto kernel  metric 256  mtu 1500 advmss 1440 hoplimit 4294967295

dave@The-Mighty-Wurlitzer:~$ sudo ping6 ipv6.google.com
connect: Network is unreachable

dave@The-Mighty-Wurlitzer:~$ sudo echo $(ip -4 addr show dev eth0 | awk '/inet / {print $2}' | cut -d/ -f1)

192.168.0.100

dave@The-Mighty-Wurlitzer:~$ sudo echo $(printf "2001:55c:%02x%02x:%02x%02x" $(echo 10.10.10.10 | tr . ' '))

2001:55c:0a0a:0a0a

dave@The-Mighty-Wurlitzer:~$ sudo ip tunnel add 6rdtun mode sit local 10.10.10.10 ttl 64
dave@The-Mighty-Wurlitzer:~$ sudo ip tunnel 6rd dev 6rdtun 6rd-prefix 2001:55c::/32
dave@The-Mighty-Wurlitzer:~$ sudo ip link set 6rdtun up
dave@The-Mighty-Wurlitzer:~$ sudo ip -6 addr add 2001:55c:0a0a:0a0a:0::1/32 dev 6rdtun
dave@The-Mighty-Wurlitzer:~$ sudo ip -6 addr add 2001:55c:0a0a:0a0a:1::1/64 dev eth0
dave@The-Mighty-Wurlitzer:~$ sudo ip -6 route add 2000::/3 via ::69.252.80.66 dev 6rdtun

After this still unable.  various ipv6 sites show only ipv4

Service:  Comcast
Cable Adaptor:  Motorola SB6120 - ipv6 ready and able
Router:  D-Link DIR-615

Request assistance

---

### Post by lemming465 on 2011-02-16
Double check the situation with your ISP versus your cable modem.  6rd tunnels are normally between the modem and the ISP's 6rd relay, not between your host and the relay.  If you are setting up a tunnel between your host and the ISP, make sure that both your router and your modem pass IPv4 protocol 41.  Also, your tunnel setup is going to have to specify the remote IPv4 address of the relay; it's not automatic.

---

### Post by hawkmage on 2011-02-16
I have used Hurricane Electric to get a free IPv6 tunnel that I configured on an Ubuntu 10.10 system for the 6to4 tunnel.  It works great.

The only thing is that the DHCP server that is part of Ubuntu is an old version that is not IPv6 aware.

---

### Post by lemming465 on 2011-02-17
Technically your tunnelbroker.net setup is a "6in4" tunnel; "6to4" uses anycast relays 192.88.99.1 rather than point to point relays.  All three of 6in4, 6to4, and 6rd do use protocol 41 encapsulation (slap an IPv4 header on the front of the IPv6 packet) by default.

---

