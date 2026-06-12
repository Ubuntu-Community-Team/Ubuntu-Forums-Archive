---
title: "Update error"
date: 2010-11-26
forum: General Help
---

### Post by Ali Kante on 2010-11-26
Hi,

when I run 

```
 sudo apt-get update && sudo apt-get upgrade

```

I receive the following error:
```

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

So I searched for this error and I already read a lot of threads here resulting in the following command:
```
 sudo  apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932

```

But with the following result:
```

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
gpg: requesting key 02FDF932 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Connection timed out
gpgkeys: HTTP fetch error 7: couldn't connect: Connection timed out
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

I already tried some other key servers, also without any success. I've been at the web site ([Keyserver]("http://keyserver.ubuntu.com:11371/pks/lookup?search=DB141E2302FDF932&op=vindex")), but the result was an error. (Not found)

So, actually I'm out of clues... 

any hints anyone? 8-)

---

### Post by wet-willy on 2010-11-26
When ever I get this error I resort to my notes and run the command below, but I change the eight digits highlighted in red to match the last eight digits of the key apt bitched about:
```
sudo gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys [COLOR="Red"]02FDF932[/COLOR] && gpg --armor --export [COLOR="Red"]02FDF932[/COLOR] | apt-key add -
```

---

### Post by Ali Kante on 2010-11-26
Thank you for the answer...

I guess the problem lies within my proxy settings.

If I try to ping the keyserver I get an not reachable error. I can do wget or apt-get, etc. but I can't ping or traceroute the key servers. I guess that's because tracert and ping use ICMP, but I didn't find a solution yet. Maybe someone can help me out here.

here's my network details:

netstat -nr
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.0.2.0        0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         10.0.2.2        0.0.0.0         UG        0 0          0 eth0

```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 08:00:27:f1:17:35  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fef1:1735/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7920 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15386000 (15.3 MB)  TX bytes:512791 (512.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4362 (4.3 KB)  TX bytes:4362 (4.3 KB)

```

arp -a
```
reserv-02-VPN-FW.NET.example.net (10.0.2.2) at 52:54:00:12:35:02 [ether] on eth0

```

---

### Post by Ali Kante on 2010-11-29
Noone with an idea? :confused:

---

