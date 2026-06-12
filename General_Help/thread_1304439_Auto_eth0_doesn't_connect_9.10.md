---
title: "Auto eth0 doesn't connect 9.10"
date: 2009-10-29
forum: General Help
---

### Post by subiet on 2009-10-29
I updated to 9.10rc, when i connect to wired LAN, i can see AutoEth0 in network manager applet, but when i try connecting to it, it tries for 45 seconds and then says "wired eth0 disconnected"

It used to work fine with 9.04

---

### Post by phillw on 2009-10-29
you probably have already, but try re-booting your router.

Phill.

---

### Post by subiet on 2009-10-29
I am in a university, and i don't really have the option to reboot the router. 


also, No, my MAC isn't blocked, cause it works fine on windows

---

### Post by alphaniner on 2009-10-29
> it tries for 45 seconds and then says "wired eth0 disconnected"

This is what I see when I use a LiveCD and it tries to get IP info from my non-DHCP LAN.

Have you checked the configuration by right clicking on the icon and selecting 'configure' (or whatever, I don't use the applet)?  It may be that it lost your setup during the upgrade.

---

### Post by subiet on 2009-10-29
My lan has a DHCP, and it is working on other windows machine.

Also i did a fresh install

---

### Post by subiet on 2009-10-29
DHCP on wireless lan works

any help on how to solve this issue. on 9.04 it used to work even on wired

---

### Post by alphaniner on 2009-10-29
If I were you I would try to temporarily disable network-manager (or make it so network-manager wasn't controlling eth0) and see if I could get it working through config files.

---

### Post by subiet on 2009-10-29
could you please elaborate the steps for both.

disabling network-manager 

and also what config files

---

### Post by alphaniner on 2009-10-29
If I knew I would have told you :)

I don't use network-manager so I don't have the first clue about how to disable it.  Without uninstalling it, that is.

As for config files, I've not yet used 9.10 so I don't know if anything has changed from 9.04.  Assuming it's the same, you have a file /etc/network/interfaces

If so, add the following lines to it:

```
auto eth0
iface eth0 inet dhcp
```

Then do

```
sudo /etc/init.d/networking restart
```

and post the output.  It should show what is going on as it tries to get an address through DHCP.

That's just my 2c, there are probably better ways.

---

### Post by subiet on 2009-10-31
tried, doesn't help. Anybody?

---

### Post by subiet on 2009-11-01
1) On the same LAN port, my windows machine connect.

2) If i use the live cd of 9.10 it still doesn't connect

3) If if use the live cd of 9.10 on some other machine on the same lan port it DOES connect

4) i have noticed that when i go to "edit connections" from the network manager option it shows a different mac address than the windows machine?

5) when i changed the mac address over there to the one that windows reported (via the GUI) i just got a new connection called auto ethernet instead of auto eth0 and it still doesn't connect

based on all of this any help please?

---

### Post by aimaaditya on 2009-11-01
i having this trouble ever since my coll decided to go with MAC filtering with wireless  access points...i am able to connect with dual booted win7 on the same system as well as with karmic on wep enabled access points..but not on MAC filtered ones...i am able to connect using Win 7 though.....

so, everything works except connection to MAC filtered access points gets dropped...

---

### Post by 00Kavi on 2009-11-01
I have this problem about 30% of the time I boot, the other 70% there are no troubles whatsoever. Resetting the router does not help, but rebooting usually solves it. Not a huge problem for me as I rarely have to reboot but it is a little annoying.

Using an alternative to network manager (such as wicd) would, I imagine, solve the issue.

Note: Win7 on same machine works fine.

---

### Post by aimaaditya on 2009-11-01
thanks, 
u mean to say i need to reboot my pC, lets see, will try that, anyways i did have a go at wicd, no improvement, and there is no optio of reseting the ap, it belongs to the university...

---

### Post by subiet on 2009-11-02
2 Things:

1) Then why does karmic works super fine on some machines. If it is from the server side, then the problem should be on all clients

2) assuming that is the problem, then any solutions?

---

### Post by gorg_karlo on 2009-11-02
> **alphaniner said:**
> If I knew I would have told you :)

I don't use network-manager so I don't have the first clue about how to disable it.  Without uninstalling it, that is.

As for config files, I've not yet used 9.10 so I don't know if anything has changed from 9.04.  Assuming it's the same, you have a file /etc/network/interfaces

If so, add the following lines to it:

```
auto eth0
iface eth0 inet dhcp
```

Then do

```
sudo /etc/init.d/networking restart
```

and post the output.  It should show what is going on as it tries to get an address through DHCP.

That's just my 2c, there are probably better ways.

As for disabling network-manager for your wired connections, you can try doing this:

```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```

Find the line which says:

[ifupdown]
managed=true

Change the value to false.

---

### Post by subiet on 2009-11-03
Here is the problem and what I have tried till now:

The problem:

Can't connect to wired LAN (auto eth0)

It used to work in jaunty.

What all have i tried:

1) LAN works on win7, so hardware is fine.

2) used the same live cd on a different machine and it connects.

Then I checked my mac address in windows and in linux (network manager > edit connections > edit auto eth0) and it shows a different one than windows one. 

below is the output of lshw -c network

```
 *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:1e:8c:57:14:ff
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.3 duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:19 memory:fd5fcc00-fd5fcc7f ioport:cc00(size=128)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:af:6f:51:cb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=10.2.3.11 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fd7f0000-fd7fffff

```

---

### Post by subiet on 2009-11-03
it is now showing the correct mac, but still stuck, just can't hop on the network

---

### Post by P4man on 2009-11-03
I found this:
[http://ubuntuforums.org/showthread.php?t=907692](http://ubuntuforums.org/showthread.php?t=907692)

> Even then there's still a bug in the sis190 driver itself, it needs a workaround to work properly by setting the MTU to 1024. Don't know exactly why but it works for me.

---

### Post by acousticlinux on 2010-04-04
Had a similar problem recently and this was the fix for me

Right click the network-manager icon in the task bar

Select Edit Connections

Click Wired Tab (if not automatically selected by default)

Select Auto eth0

Click Edit

Click on the IPv6 Settings Tab

Click Method drop down menu

Select Ignore

Select Apply and close out everything

Worked for me I hope it helps someone else.

---

### Post by hitbyambulance on 2010-07-07
> **acousticlinux said:**
> Had a similar problem recently and this was the fix for me

Right click the network-manager icon in the task bar

Select Edit Connections

Click Wired Tab (if not automatically selected by default)

Select Auto eth0

Click Edit

Click on the IPv6 Settings Tab

Click Method drop down menu

Select Ignore

Select Apply and close out everything

Worked for me I hope it helps someone else.

Just wanted to chime in - this worked for me as well on 10.04. So why would IPv6 suddenly cause this? it had been on 'auto' before and worked fine.

---

### Post by gphilip on 2011-09-02
> **acousticlinux said:**
> Had a similar problem recently and this was the fix for me

Right click the network-manager icon in the task bar

Select Edit Connections

Click Wired Tab (if not automatically selected by default)

Select Auto eth0

Click Edit

Click on the IPv6 Settings Tab

Click Method drop down menu

Select Ignore

Select Apply and close out everything

Worked for me I hope it helps someone else.

This worked for me (on Arch Linux!) as well. :guitar:

I had been wondering for a couple of days why my eth0 connection was not showing up on NM, even though I was connected to the internet using eth0. For me, the eth0 connection was absent from the list of wired connections in NM, so I had to create a new one and then follow the steps above. But it worked now, thanks!

---

