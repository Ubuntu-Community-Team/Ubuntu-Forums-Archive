---
title: "Connection Problems"
date: 2006-04-22
forum: General Help
---

### Post by berwickboy on 2006-04-22
I don't know if this has been asked already but it's really annoying me, i have installed Ubuntu but i cant seem to get it to work online, everything is fine except for that, i had the same problem with SuSE (SUSE) Linux. I connect through a router; D-Link DSL-G604T and it works perfect through my windows XP computer. I was just wondering if anyone had any advice on how to get me connected as its really frustrating, thanks in advance. Also I will keep trying different things but could do with some pointers.

-John.

---

### Post by mips on 2006-04-22
You are in the wrong forum. Please ask a mod to move it to the Hardware-Networking forum.

[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337)

1. Please disable IPv6 and reboot:
[B]sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a[/B]
2. Please post output of **ifconfig eth0**  (Depends on your interface number)
3. Please post output of **lspci | grep Eth**
4. Please post output of **route -n**
5. Please post output of **cat /etc/resolv.conf**
6. Please post output of **cat /etc/network/interfaces**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

---

### Post by berwickboy on 2006-05-07
Yeah its okay, thanks i got it now. Sorry i never said thanks earlier.

-John

---

