---
title: "2 NIC's causing SSH problems"
date: 2011-11-06
forum: General Help
---

### Post by Coiler on 2011-11-06
I'm running Ubuntu 10.04 as a VM on my Xenserver.

For that i've given it 2 network interfaces both on a different network:
1. eth0: 192.168.1.0/24
2. eth1: 10.0.0.0/24

I've set the /etc/network/interfaces as following:
```
#The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.201
netmask 255.255.255.0
gateway 192.168.1.254

# The secondary network interface
auto eth1
iface eth1 inet static
address 10.0.0.201
netmask 255.255.255.0

```

The interfaces are both up and running with the right ip addresses (the 10.0.0.0 network is purely for internal xenserver communication so no gateway).

my resolv.conf looks like this:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

Using the route command I get the following:
```
Destination Gateway Genmask Flags Metric Ref Use Iface
10.0.0.0 * 255.255.255.0 U 0 0 0 eth1
192.168.1.0 * 255.255.255.0 U 0 0 0 eth0
default 192.168.1.254 0.0.0.0 UG 100 0 0 eth0

```

When I try to connect to my server (from the 192.168.1.0 network) using putty (ssh) it sometimes works for a minute and other times it quits immediatly saying:
> Network error: Software caused connection abort

This will also cause my webmin to stop working for a few minutes.
Netstat will show the following after the problem occurs:
```
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address Foreign Address State
tcp 0 69 192.168.1.201:ssh 192.168.1.1:51203 FIN_WAIT1

```

I've also tried it on a new VM with no software (just openssh) which gives the same result.

My guess is that it has to do with the 2 NIC's but I can't be sure.

Hopefully someone is able to help me out here.

Regards,
Coiler

---

### Post by collisionystm on 2011-11-06
So disable the 2nd NIC and see if it still happens

---

### Post by clrg on 2011-11-06
You can try telling sshd to bind to a specific IP. From sshd_config(5):

```

     ListenAddress
             Specifies the local addresses sshd(8) should listen on.  The fol&#8208;
             lowing forms may be used:

                   ListenAddress host|IPv4_addr|IPv6_addr
                   ListenAddress host|IPv4_addr:port
                   ListenAddress [host|IPv6_addr]:port

             If port is not specified, sshd will listen on the address and all
             prior Port options specified.  The default is to listen on all
             local addresses.  Multiple ListenAddress options are permitted.
             Additionally, any Port options must precede this option for non-
             port qualified addresses.


```

Put "ListenAddress 192.168.1.201" in your /etc/ssh/sshd_config and restart sshd.

---

### Post by Coiler on 2011-11-06
Putting it off (ifdown eth0) will still cause the problem to occur.

Setting the SSH config to the fixed ipaddress also doesn't change the problem.

---

### Post by collisionystm on 2011-11-06
What kind of network switch

---

### Post by Coiler on 2011-11-06
> **collisionystm said:**
> What kind of network switch

What do you mean by that?

I'm running the ubuntu server as an Virtual Machine on my xen server.
Where the 10.0.0.0 network is the internal server network (connecting all the VM's with eachother) and 192.168.1.0 is the network that connects to the rest of the network and to the Internet.

My other existing ubuntu 11.04 server doesn't have any problems with the same configuration without any fixed ip set.

---

### Post by collisionystm on 2011-11-06
> **Coiler said:**
> What do you mean by that?

I'm running the ubuntu server as an Virtual Machine on my xen server.
My other existing ubuntu 11.04 server doesn't have any problems with the same configuration without any fixed ip set.

OHHH sorry. I was thinking a bit more complicated.

I have not dealt with Xen networks. However I recall reading about making your Xen network Bridged. You must do this. Having it NAT will not work. Nat will only allow a 1 way communication.

---

### Post by clrg on 2011-11-06
> **Coiler said:**
> Putting it off (ifdown eth0) will still cause the problem to occur.



That's because you are putting down the wrong interface. Look at your /etc/network/interfaces, you say there that eth0 is your primary interface and eth1 is the second one.

Assuming you want to communicate with the VM using the primary, you should 

```
ifdown eth1
```

instead :)

---

### Post by Coiler on 2011-11-06
> **clrg said:**
> That's because you are putting down the wrong interface. Look at your /etc/network/interfaces, you say there that eth0 is your primary interface and eth1 is the second one.

Assuming you want to communicate with the VM using the primary, you should 

```
ifdown eth1
```

instead :)

Little typo, I was putting down the eth1 (sorry)


Edit: Making a completely new VM with only 1 NIC gives me the same problem. I think my Xenserver is broken :(

---

### Post by Coiler on 2011-11-06
Ok, the problem was way more simple.

IP conflict, new testserver that hadn't been documented yet by my co-worker used the same IP-address.

Sorry to have wasted your time.

---

### Post by collisionystm on 2011-11-07
> **Coiler said:**
> Ok, the problem was way more simple.

IP conflict, new testserver that hadn't been documented yet by my co-worker used the same IP-address.

Sorry to have wasted your time.

Well, glad you figured it out!

---

