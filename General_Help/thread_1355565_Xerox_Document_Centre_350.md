---
title: "Xerox Document Centre 350"
date: 2009-12-15
forum: General Help
---

### Post by rykel on 2009-12-15
Hi,

I am helping a small office convert their PCs to Ubuntu Karmic.

They have a Xerox Document Centre 350 photocopying machine that acts as their printer, and is linked to their PCs via the network.

How do I install this printer and make it work?

Thanks for advising!!

---

### Post by prshah on 2009-12-15
> **rykel said:**
> They have a Xerox Document Centre 350 photocopying machine that acts as their printer, and is linked to their PCs via the network.

You need to get certain information about how the copier is setup. You need the IP address of the copier, and the "Queue" name; both of these will be displayed in the configuration sheet. The configuration sheet can be printed by selecting suitable options on the copier (sorry, don't have more details).

Once you have the required information, open a browser on the Ubuntu system. In the address bar, type ```
http://localhost:631
``` to open the CUPS (Common Unix Printing System) page.

If at any point CUPS asks for a username and password, give the username and password of any sudo capable user on the system.

On the CUPS main page, choose the "Administration" tab. Then choose "Add printer". From the options for network printing, choose "LPR/LPD Host or printer", and choose Next (Continue?). When asked for the "Connection", please enter```
    lpd://ipaddress/queuename
``` where ipaddress and queuename are taken from the configuration sheet. Choose Next/Continue.

Give the printer a name, and fill in whatever other information you feel relevant. Continue. 

In the next screen, provide a .PPD file if you have it available on the driver disk. If you have a PPD file, enter it's location and choose "Add printer".

If you don't have a PPD file, choose the "Make" as Xerox, and "Model" as "Document Centre 400". There are two options; try the other if the first doesn't work. Click "Add Printer" when done. 

Set your default options as suitable to you, including paper sizes, tray options, etc. 

Now your printer should be working fine. Please try a test page, and post back here if you have any problems.

---

### Post by rykel on 2009-12-16
Hello PRShah,

Thank you so much for your help... I believe we are getting closer to getting the printer connected!

Right now, when I "ping 192.168.001.098" it says "ping: unknown host 192.168.001.098"... which means that either my Ubuntu Linux PC is NOT on the office network, OR that the printer is NOT connected to the PCs here, right?

Any help please?

Thank you!!

---

### Post by prshah on 2009-12-16
> **rykel said:**
> when I "ping 192.168.001.098" it says "ping: unknown host 192.168.001.098"...

Try removing the extra zeros, eg 192.168.1.98 (Seems to be a problem with 90 onwards); this shouldn't really matter, just covering all bases. Eg```
Wed Dec 16 @17:04:54:~$ ping -c 1 192.168.1.6
PING 192.168.1.6 (192.168.1.6) 56(84) bytes of data.
64 bytes from 192.168.1.6: icmp_seq=1 ttl=128 time=6.59 ms

--- 192.168.1.6 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 6.598/6.598/6.598/0.000 ms
Wed Dec 16 @17:05:04:~$ ping -c 1 192.168.001.006
PING 192.168.001.006 (192.168.1.6) 56(84) bytes of data.
64 bytes from 192.168.1.6: icmp_seq=1 ttl=128 time=2.86 ms

--- 192.168.001.006 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 2.866/2.866/2.866/0.000 ms
Wed Dec 16 @17:05:09:~$ [color=red]ping -c 1 192.168.1.98[/color]
PING 192.168.1.98 (192.168.1.98) 56(84) bytes of data.
[color=blue]From 192.168.1.23 icmp_seq=1 Destination Host Unreachable[/color]

--- 192.168.1.98 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

Wed Dec 16 @17:05:21:~$ [color=red]ping -c 1 192.168.001.098[/color]
[color=blue]ping: unknown host 192.168.001.098[/color]
Wed Dec 16 @17:05:26:~$ 

```

If you still cannot ping the printer after removing the extra zeros, then yes, either the printer or the ubuntu computer is not on the correct network. The correct message will be "Destination Host Unreachable" (Please see example above).

Ensure that both are on similar IPs, and that subnet masks match exactly.

Please post back with whatever information you feel relevant (including ping output) for more help, if required.

---

### Post by rykel on 2010-02-11
Hi all,

Using **lpd://192.168.1.98** as IP Address and **LP** as Queue, I can indeed print to the network printer now.

HOWEVER, it takes forever to send a page to be printed... so much so that it makes it impractical to use the printer with Ubuntu for real tasks.

What else am I missing? Thanks for helping.

---

