---
title: "Lost networking after hw replacement"
date: 2010-07-17
forum: General Help
---

### Post by richardeng2005 on 2010-07-17
HELP! I'm in a serious pickle...

My Dell PowerEdge R200 server just died. Dell had to replace the motherboard, but now networking doesn't work. I'm running Ubuntu Linux Server 7.04 which is a very old version. I think maybe the kernel driver doesn't support the newer revision of the Broadcom adapter on the motherboard. When I try to restart networking, I get the following error:

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: no such device

How do I restore networking? Do I require a kernel update? Which kernel version? How do I get this kernel since I don't have network access (so forget apt-get)?

Is there an easier way to resolve this problem?

Do I have to resort to the worst-case scenario of reinstalling *everything* from scratch -- latest Ubuntu version, LAMP, my server application? Dear God!

Here's what the bios tells me:

Embedded Gb NIC1... Enabled without PXE
Embedded Gb NIC2... Enabled without PXE

Further, in the IRQ section:

NIC1... IRQ 15
NIC2... IRQ 14

I did a 'dmesg | less' and scanned for any references to networking. I found that eth0 and eth1 are associated with 'Tigon3'.

Doing a Google search, I found that Tigon3 refers to the Broadcom adapter. So apparently the system is able to recognize the NIC. And Tigon3 is supported in all kernels from 2.6.0 and up.

Thanks.

---

### Post by richardeng2005 on 2010-07-17
I'm rather shocked that no one is able to offer any assistance. It seems I made a mistake choosing Ubuntu Server Linux over Red Hat/CentOS. At least with Red Hat, Dell could've helped me. Oh well.

---

### Post by jmszr on 2010-07-17
richardeng2005,

Perhaps you would have an increased likelihood of response if you posted to the "Server Platforms" subforum: [http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339) .

---

