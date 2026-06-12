---
title: "Lucid/ThunderbirdKVM *host* SMTP send broken"
date: 2010-09-07
forum: General Help
---

### Post by jaimito on 2010-09-07
I suspect that I have done something stupid and would ask for a kick in the right direction to fix it.

System: clean install Lucid/dual boot running /64 with Xeon 2.13 and ATI with proprietary

All was working fine. I run XP/Win7 in virtual machines originally under Oracle VirtualBox.
I had significant issues post a recent VirtualBox upgrade so removed all VB and installed KVM, built new virtual machines. This works fine and is much faster than VB.

To give the virtual machines full network access I edited the /etc/network/interfaces files

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

```I am not certain this is actually related, but subsequently at some point I find I now have problems sending (but not receiving) email from Thunderbird (and Claws, installed to check) on the KVM host machine (no email client installed on vm's).

The (partially anonymised) log result of an attempted send from Claws is:

```

11:34:20] IMAP4< 10 OK STORE completed. 
* Connecting to SMTP server: mail.stabilys.com ...
[11:34:21] SMTP< 220 postalmail-a8.g.dreamhost.com ESMTP
[11:34:21] ESMTP> EHLO jaimito-f-desktop
[11:34:22] ESMTP< 250-postalmail-a8.g.dreamhost.com
[11:34:22] ESMTP< 250-PIPELINING
[11:34:22] ESMTP< 250-SIZE 40960000
[11:34:22] ESMTP< 250-ETRN
[11:34:22] ESMTP< 250-STARTTLS
[11:34:22] ESMTP< 250-AUTH LOGIN PLAIN
[11:34:22] ESMTP< 250-AUTH=LOGIN PLAIN
[11:34:22] ESMTP< 250 8BITMIME
[11:34:22] ESMTP> MAIL FROM:<me.at@stabilys.com> SIZE=379
[11:34:22] SMTP< 250 Ok
[11:34:22] SMTP> RCPT TO:<me.at@stabilys.com>
[11:34:22] SMTP< 554 <unknown[78.32.my.ip]>: Client host rejected: Access denied
** error occurred on SMTP session
*** Error occurred while sending the message:
554 <unknown[78.32.my.ip]>: Client host rejected: Access denied

```Tests with telnet to the SMTP server from this box time out.

I can send mail to this server from my wife's Win box on this network and have checked with ISP no problems on their network.

The route is:

```

~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.11.0      *               255.255.255.0   U     0      0        0 br0
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
link-local      *               255.255.0.0     U     1000   0        0 br0
default         home.gateway    0.0.0.0         UG    100    0        0 br0


```My brain is not working. Any hints/brickbats etc will be much appreciated, tyvm.

Jaimito

---

