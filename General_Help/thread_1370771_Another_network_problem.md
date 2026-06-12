---
title: "Another network problem"
date: 2010-01-02
forum: General Help
---

### Post by scriptsit on 2010-01-02
Ok, so like any other linux n00b, I'm working to no avail trying to configure the network. I have this hp mini 1035 where I used to have ubuntu 8.10 installed.. no issues. The netbook worked fine until I had an incident with someone's bulldog chewing through my dongle cable. I put the thing up, got myself involved with another project, and eventually forgot about the machine.

I tried to restart the machine a few weeks ago only to discover that I'd forgotten the password. By then, 9.10 had been released so I figured a fresh install wouldn't hurt anything at all. I installed the desktop edition only to discover that it would neither read my wired or wireless network interfaces. Well, at least it seemed to WANT to read my wireless card as it suggested such a download was available.. only continually would not connect through the wired connection. 

Any help would be appreciated.

---

### Post by Manyette on 2010-01-02
Not sure this is a lot of help, but during the install, it is necessary to have the network cable attached.  It's bitten me twice because I forgot to plug it in.  And it it doesn't install the network on the system install, I had a great deal of trouble getting it work after the install.

---

### Post by scriptsit on 2010-01-02
I appreciate the reply, but I did happen to know that trick. I did keep the ethernet cable installed during the process.

Here's something else I noticed. If I boot from the live cd (USB), the OS will recognize the ethernet connection. But it will not recognize it booting from the HD.

Any thoughts?

---

### Post by Manyette on 2010-01-02
Hopefully someone more knowledgeable that me will pick this up.  The only thing that occurs to me is that you might not be using DHCP when booting from the Hard Drive.  Maybe someone else can offer more.

---

### Post by Iowan on 2010-01-02
If you're using Network Manager, look at the settings for "Auto eth0" - verify the MAC address, etc. As a side note, **ifconfig -a**  should show all available interfaces. **lshw -C network** should show if the interfaces have a driver and alias assigned.

---

### Post by scriptsit on 2010-01-03
Here is the output of those two commands:

  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:feafc000-feafffff


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

pan0      Link encap:Ethernet  HWaddr a6:49:13:bd:e8:d5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

It still reads "no network devices available"

---

