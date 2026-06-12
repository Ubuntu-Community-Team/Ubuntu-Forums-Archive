---
title: "Internet connected with 3G USB wireless but Firefox not"
date: 2010-04-11
forum: General Help
---

### Post by t3ubu on 2010-04-11
Hi there, 

Can't find a thread that matches my circumstances so here goes...

Am using Ubuntu 9.10 live disc.

Plugged in the 3G wireless usb modem and followed network connection prompts- internet connection is working (little lighthouse icon and network manager indicates that it is connected).

Firefox however does not want to connect to the internet.

I've done the usual checks- deselected "work offline"; looked under advanced preferences and ensured 'no proxy' under the network connections tab. 

Also, I've followed the below to disable IPV6:

_**Additional: Disabling ipv6 in Firefox**_
[LIST=1]
[*]Type about:config in your address entry bar (in firefox)
[*]Type "ipv6" in the filter
[*]Change the value of "network.dns.disableIPv6" to true
[/LIST]
However still no internet.

Problem seems to be firefox not recognising the live network connection, so any tips or workarounds are welcome. 

Thanks in advance, 

Tim

---

### Post by 3rdalbum on 2010-04-11
Try going to the network manager applet on your panel (that looks like a lighthouse) and right-click it, and go to Edit Connections. Select your mobile broadband and click Edit, go to IPv4 Settings and change it to "Automatic (DHCP addresses only)".

The DNS field will become active. Type in it:

```
208.67.222.222,208.67.220.220
```

Save your changes, disconnect and reconnect. Your DNS is now handled by the OpenDNS service, rather than relying on your ISP to send its DNS address.

If this doesn't help, then you may be encountering a known bug in Ubuntu 9.10, and you should try Ubuntu 10.04 which is currently in Beta 2 (to be released at the end of the month).

---

### Post by t3ubu on 2010-04-12
> **3rdalbum said:**
> Try going to the network manager applet on your panel (that looks like a lighthouse) and right-click it, and go to Edit Connections. Select your mobile broadband and click Edit, go to IPv4 Settings and change it to "Automatic (DHCP addresses only)".

The DNS field will become active. Type in it:

```
208.67.222.222,208.67.220.220
```Save your changes, disconnect and reconnect. Your DNS is now handled by the OpenDNS service, rather than relying on your ISP to send its DNS address.
.

All resolved.

Connection is now live. Cheering :KS

---

### Post by t3ubu on 2010-04-12
> **t3ubu said:**
> All resolved.

Connection is now live. 

Uh oh. Shutdown computer, went through the live CD process etc then edited network connection as above, [I]except...

[/I]"apply" button on dialog box no longer stays green when I input 
208.67.222.222,208.67.220.220
into the blank DNS field...

Whereas in the last live session, it would accept the DNS entries as above and fully establish the connection, the green button blanks out at the first digit entry.

Is there any workaround to this?

---

### Post by t3ubu on 2010-04-16
[QUOTE=

Is there any workaround to this?[/QUOTE]


The only workaround it seems is to burn a bootable disc of the Beta 2 version of v10.4 from another online machine. 

This has finally been done. And internet connection appears to be restored (for at least this session in any case). 

Fingers crossed this thread can close.

---

### Post by gaving on 2010-06-23
I am new to Linux. Very green, but persisting to get away from Windows.

I am experiencing a similar problem in that sometimes I can get Firefox and Thunderbird to work and the next day it does not work. I am using a Vodacom / Vodafone red USB 3G dongle.  What is the bug in 9.10?

I will have to upgrade to 10.4 as I cannot go without emails and internet and go back to windows to get them. 

Gavin

---

