---
title: "Trouble accessing the internet"
date: 2009-08-20
forum: General Help
---

### Post by growthmetal on 2009-08-20
I recently installed Ubuntu 8.04 off a CD on my Compaq Presario CQ60 laptop.  When I connect it with ethernet to a router and boot up Ubuntu, I see the little icon with the two computers in the upper right corner has no exclamation point.  However, I can't connect to any websites.  I pinged ubuntu.com's IP address with 5 packets and 0% were returned.  (Or at least I suspect it's ubuntu.com's IP address.  It's the one you're suggested to ping in the documentation.)  The help docs say this means my internet connection is extremely bad or nonexistent, but the connection works with no configuration whatsoever through another laptop, or with my Compaq laptop when it's running Vista.

No idea if this is relevant, but if I unplug & replug the ethernet, the exclamation point will appear and not go away.  Also, if I shut my laptop, Ubuntu stays awake instead of going to sleep like Vista.  I get the feeling that Ubuntu hasn't spread its tendrils fully throughout my hardware or something.  The mouse and keyboard work though.

---

### Post by FewClues on 2009-08-20
Right click on the ICON and make sure you have networking enabled. Also check to make sure your network is setup for DHCP.

---

### Post by doas777 on 2009-08-20
run this in a terminal:
```
sudo ifconfig
sudo lshw -C network
sudo route
```and post the output.

that should tell us what your ip configuration is, your network hardware, and what route your pc thinks it should take to get to the internet

---

### Post by growthmetal on 2009-08-21
Networking was enabled already.  I changed my wired connection so that it used DHCP to no avail.

Here is a copy-paste from a terminal session:

```
johniv@johniv-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:6e:9d:74  
          inet6 addr: fe80::21f:16ff:fe6e:9d74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967210 overruns:0 frame:0
          TX packets:0 errors:0 dropped:65 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Base address:0xe000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1f:16:6e:9d:74  
          inet addr:169.254.6.78  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:221 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73616 (71.8 KB)  TX bytes:73616 (71.8 KB)

johniv@johniv-laptop:~$ sudo lshw -C network
  *-generic               
       description: Ethernet interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: ff
       serial: 00:1f:16:6e:9d:74
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=255 link=yes maxlatency=255 mingnt=255 module=r8169 multicast=yes port=twisted pair speed=1GB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
johniv@johniv-laptop:~$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0

```

---

### Post by bchurchill on 2009-08-21
I'm no expert on these issues, but it looks like your router gateway isn't setup correctly.  The first thing I would try is dhcp using

```
sudo dhclient eth0
```

and the second thing I would try is

```
sudo route add default gw <ip address of router>
```

also try pinging your router and well known pages like [www.google.com](www.google.com)

---

### Post by doas777 on 2009-08-21
the problem appears to be that you don't have an IP address. 
as bchurchill pointed out, 
sudo dhclient eth0will hopefully fix your issue. if not try
```
sudo ifdown eth0
sudo ifup eth0
```

the run ifconfig again, and see if you have a valid value for "inet addr", and everything will work fine.

---

### Post by growthmetal on 2009-08-24
Thanks guys, sudo dhclient eth0 worked!

My only question now is: any way to automate things so that command runs every time my laptop wakes up from being suspended?  Because the internet often seems not to work without it.  Should I learn about cron for this, or does cron only do time-dependent stuff and no event-dependent stuff?

---

### Post by doas777 on 2009-08-24
put it in a script and drop it in
```

/etc/acpi/resume.d/

```

---

### Post by growthmetal on 2009-08-24
OK, here's my script:

```
#!/bin/sh

sudo dhclient eth0
```

I put it in /etc/acpi/resume.d and added the execute permission for user, group, and other:

-rwxr-xr-x 1 johniv johniv   30 2009-08-24 13:57 internet-connect.sh

It doesn't seem to be working.  Although typing ./internet-connnet.sh while in /etc/acpi/resume.d seems to substitute fine for typing "sudo dhclient eth0" myself.

Sorry, I'm a bit of a noob when it comes to unix.  I took a quarter-long introductory class but I haven't read any books and I don't have extensive experience.

---

### Post by doas777 on 2009-08-24
> **growthmetal said:**
> 
Sorry, I'm a bit of a noob when it comes to unix.  I took a quarter-long introductory class but I haven't read any books and I don't have extensive experience.

no worries man; I've never hooked off resume either. the documentation says it should work, but power managment is still a little flakey.
try renaming your script to '99-internet-connect.sh'. I believe the number represents the order of execution, so that your's fires last.
also add this line to the bottom of your script ```
touch \home\<username>\script-ran
```  save and exit.
that way we can tell if it is running, but not fixing the problem. 

then after a resume, check your home dir for the "script-ran" file. if it's there, your script ran. you can remove or commend out the 'touch' line once everything is working fine.

---

### Post by growthmetal on 2009-08-24
I replaced the backslashes in your path with forward slashes.  The script appears not to have run.  I even tried another simpler script:

-rwxr-xr-x 1 johniv root     40 2009-08-24 18:05 1-test.sh
```

!# /bin/sh

touch /home/johniv/test-ran
```

Didn't seem to run either.

---

### Post by doas777 on 2009-08-24
> **growthmetal said:**
> I replaced the backslashes in your path with forward slashes.  The script appears not to have run.  I even tried another simpler script:

-rwxr-xr-x 1 johniv root     40 2009-08-24 18:05 1-test.sh
```

!# /bin/sh

touch /home/johniv/test-ran
```Didn't seem to run either.
ahh sorry bout that. 

hmmm. all of my scripts are owned by root. try
```
sudo chown root:root 1-test.sh
```
the acpi deamon is running as root so I guess that makes sense.

---

### Post by doas777 on 2009-08-24
ok, just found somthing useful.

according to this: [http://ubuntuforums.org/showpost.php?p=5222967&postcount=5](http://ubuntuforums.org/showpost.php?p=5222967&postcount=5)
the resume.d doesn;t work anymore (no idea why), but the poster provides a suitable script. check it out.

---

### Post by growthmetal on 2009-08-25
That didn't work either, unfortunately.  I found something that did work though.

In the network menu, I right-clicked and selected edit connections.  Then I created a new one with the MAC address of my router and its maximum transmission unit.  When I suspended my computer and then woke it up again things magically started working.

Thanks for your help.

---

