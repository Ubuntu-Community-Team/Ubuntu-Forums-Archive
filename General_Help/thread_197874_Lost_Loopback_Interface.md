---
title: "Lost Loopback Interface"
date: 2006-06-16
forum: General Help
---

### Post by ultralame on 2006-06-16
I installed Ubuntu 6.06 and all was working fine.  I added a few packages (apache2, DNS, DHCP Server, etc) and it was still great.

I then remounted /home and /var on separate RAID volumes (logged in using a live CD to do so) and rebooted.  The only problem was that the networking is now messed up, and I am not sure why.  The new volumes are wokring correctly, as far as I can tell.

The loopback adapter seems to have dissapeared.  Can someone tell me how to get it back?

Details:

/etc/network/interfaces:
(note:  I only have eth0 on this system)
[INDENT]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.254

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp[/INDENT]


$ sudo ifconfig
[INDENT]
eth0      Link encap:Ethernet  HWaddr 00:0F:B5:8D:74:F3
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: <MAC>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24516 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10692071 (10.1 MiB)  TX bytes:9188974 (8.7 MiB)
          Interrupt:201 Base address:0x6000[/INDENT]

---

### Post by DeadEyes on 2006-06-16
have you tried?
```

$ifconfig lo 127.0.0.1

```

---

### Post by TicTac on 2006-10-01
I had the same issue when putting /var on another disk. It seems that it mounts first 
varrun                  257988        88    257900   1% /var/run
varlock                 257988         4    257984   1% /var/lock


and then /var. I didn't understand the details but the following link explains how to solve the problem:
[http://www.mail-archive.com/slug@slug.org.au/msg57731.html]("http://www.mail-archive.com/slug@slug.org.au/msg57731.html")

To just sum up the following commands solve the problem for me:
  ```
mount --bind / /mnt && mkdir /mnt/var/run /mnt/var/lock && umount /mnt
```

If the command fails in the middle, just redo the mkdir on one or both dirs, and umount command.


Hope it will work for you

---

### Post by Jaime E. Villate on 2006-10-06
I had the same problem. I could get the loopback interface back with
```
sudo ifconfig lo up
```
but the problems continued because "lo" was not being brought up automatically at bootime. I finally found the cause of the problem by following the advice of varunus in thread 48557: run
```
sudo /etc/init.d/networking restart
```
manually to detect the problem: it pinpointed a simple syntax error in /etc/network/interfaces which was causing the problem.

---

