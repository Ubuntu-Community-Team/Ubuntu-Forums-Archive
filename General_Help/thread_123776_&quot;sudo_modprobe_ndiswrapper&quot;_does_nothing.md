---
title: "&quot;sudo modprobe ndiswrapper&quot; does nothing"
date: 2006-01-30
forum: General Help
---

### Post by parad0x on 2006-01-30
Hi,

I installed the boradcom drivers for my wireless card using ndiswrapper.  I followed the steps from a post on the forum.  The driver is bcmwl5.inf. My problem is I dont think modprobe ndiswrapper is actually doing anything, i run the command 
$sudo modprobe ndiswrapper          //and i get nothing

so I checked out of curiosity using
$ndiswrapper -l 
to see if it is actually installed. The ouput says the driver is present and so is the hardware.
I also inserted ndiswrapper at the end of /etc/modules.  Even after all these steps I still don't see the wan0 in the network options, nor does lsmod show anything resembling what need. The device manager also shows that the wireless card is there.... so what is going on?

Thanks ahead of time for your replies.

-Duncan

---

### Post by carlosqueso on 2006-01-30
Can you post the output of ```
ifconfig
```  Maybe your network card just got called something else.

---

### Post by parad0x on 2006-01-31
the output for iwconfig is:

```

lo       no wireless extensions

eth0   no wireless extensions

sit0    no wireless extensions

```

---

### Post by carlosqueso on 2006-01-31
Do you have a wired ethernet connection?  If you don't, try activating the eth0 connection and see if your wireless just got called that somehow.

---

### Post by parad0x on 2006-01-31
I do have a wired connection.

---

### Post by parad0x on 2006-01-31
[QUOTE=parad0x]I do have a wired connection.[/QUOTE]
What else is wierd is that after I do the sudo modprobe ndiswrapper... there is no messages in the dmesg concerning the wireless card.

---

