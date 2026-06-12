---
title: "ubuntu LTSP dhcp problem"
date: 2011-05-03
forum: General Help
---

### Post by L Style on 2011-05-03
I'm using ubuntu 10.04, Im going to setup LTSP sever, But I cant start dhcp3 server this errors are come, how can I fix this

[SIZE=3]**this error comes when I tried to start dhcp3 server**[/SIZE]

lachitha@lachitha-desktop:~$ sudo /etc/init.d/dhcp3-server start
 * Starting DHCP server dhcpd3                                                 
* check syslog for diagnostics.        [fail]

[SIZE=2]**This is the syslog **[/SIZE]

May  3 13:21:18 lachitha-desktop dhcpd: No subnet declaration for eth1 (0.0.0.0).
May  3 13:21:18 lachitha-desktop dhcpd: ** Ignoring requests on eth1.  If this is not what
May  3 13:21:18 lachitha-desktop dhcpd:    you want, please write a subnet declaration
May  3 13:21:18 lachitha-desktop dhcpd:    in your dhcpd.conf file for the network segment
May  3 13:21:18 lachitha-desktop dhcpd:    to which interface eth1 is attached. **
May  3 13:21:18 lachitha-desktop dhcpd: 
May  3 13:21:18 lachitha-desktop dhcpd: 
May  3 13:21:18 lachitha-desktop dhcpd: Not configured to listen on any interfaces!

**this is my dhcpd.conf file**
#
# Default LTSP dhcpd.conf config file.[SIZE=2]
#[/SIZE]

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.20 192.168.0.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
# next-server 192.168.0.1;
# get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}

[SIZE=2]**This is my dhcp3-server file**[/SIZE]
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#    Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1"

[SIZE=3][COLOR=Red]Please guys help me to fix this problem. [/COLOR][/SIZE]

---

### Post by L Style on 2011-05-03
bump

---

### Post by Azdour on 2011-05-03
Hi,

What does ifconfig tell you about eth1?

Is it on the 192.168.0.0 subnet that is defined in the dhcpd.conf?

---

### Post by L Style on 2011-05-03
> **Azdour said:**
> Hi,

What does ifconfig tell you about eth1?

Is it on the 192.168.0.0 subnet that is defined in the dhcpd.conf?

this is what ifconfig display. please friend help me to fix thix

lachitha@lachitha-desktop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:2a:43:00:6e:f5  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15088 (15.0 KB)  TX bytes:15088 (15.0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:175.157.207.12  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1293 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1027859 (1.0 MB)  TX bytes:179817 (179.8 KB)

---

### Post by L Style on 2011-05-03
bump

---

### Post by L Style on 2011-05-03
bump. please help me guys

---

### Post by Azdour on 2011-05-03
Hi,

It looks like eth1 has not been set up. Are you using the ppp interface to connect to the Internet?

I know very little about ltsp. Other people more experienced with ltsp may be able to give you better advise than myself. The only thing I can suggest is to go into the /etc/network directory and edit the interfaces file. Since I do not really know your system setup I am not sure if doing the following will give you more issues.

Put into it:

```

auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0
network 192.168.0.0

```

Then run:

```

sudo /etc/init.d/networking restart

```

If you type in ifconfig again you should see that eth1 now has the IP 192.168.0.1

Try to start the dhcp and it might start this time.

---

### Post by L Style on 2011-05-03
> **Azdour said:**
> Hi,

It looks like eth1 has not been set up. Are you using the ppp interface to connect to the Internet?

I know very little about ltsp. Other people more experienced with ltsp may be able to give you better advise than myself. The only thing I can suggest is to go into the /etc/network directory and edit the interfaces file. Since I do not really know your system setup I am not sure if doing the following will give you more issues.

Put into it:

```

auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0
network 192.168.0.0

```Then run:

```

sudo /etc/init.d/networking restart

```If you type in ifconfig again you should see that eth1 now has the IP 192.168.0.1

Try to start the dhcp and it might start this time.

[SIZE=2][COLOR=Red]Thanks friend it's work[/COLOR][/SIZE] **[SIZE=2]but I got a another problem when client machine connected, ubuntu boot screen display and vanished no error message displayed,machine's screen goes black and not responding. Can you help me with this problem. please help me. [SIZE=3]this problem is a headache.[/SIZE][/SIZE]**

---

### Post by Azdour on 2011-05-04
Hi,

Sorry that's as far as my knowledge goes. If you get no joy here you may want to try joining the ltsp mailing list:

[http://sourceforge.net/apps/mediawiki/ltsp/index.php?title=Ltsp_Support](http://sourceforge.net/apps/mediawiki/ltsp/index.php?title=Ltsp_Support)

---

### Post by L Style on 2011-05-04
bump

---

