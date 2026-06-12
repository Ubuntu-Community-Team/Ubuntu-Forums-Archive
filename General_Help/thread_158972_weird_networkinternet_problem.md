---
title: "weird network/internet problem"
date: 2006-04-12
forum: General Help
---

### Post by jturnbul on 2006-04-12
last night was using Kubuntu fine with internet access.  Was even messing around with QEMU, and had internet working fine through a virtual linux system.

Put my laptop into hibernate, and went to bed.

Today, I cant seem to connect to the internet.

ifconfig and iwconfig all show my network card eth1 configured properly.  I also use Kwifimanager, and it show the connection to my router, with the proper IP address, and a full signal.

I have tried ifconfig eth1 up/down, reboots, but nothing works.  I notice that it seems to hang in the boot process during the configuration of the network interfaces for about 10 seconds to long, but the check comes up "OK" with no boot errors.

When I try to open a browser it basically says it cant connect after 30 seconds.  

I have booted to XP, and the connection works fine, so the card itself is functional.

---

### Post by alamba on 2006-04-12
Need some more details buddy:
1. Can you ping your router IP?
2. Can you ping 4.2.2.2
3. Can you ping oracle.com

Let me know which part fails and we should be able to pin point the problem. Oh and can you post your netstat -rn and make sure that both LAN and wireless interface are not enabled at the same time.

A

---

### Post by incubus on 2006-04-12
Sometimes my Internet provider screws up the primary DNS server. That's evident, of course, when everything seems to be fine, but you get "Looking up www.google.com" in a browser. I think Windows goes to the second server quickly, so you don't notice.

If that's the case, you can try commenting out the first server in:
/etc/resolv.conf

But as lamba said, we would need more information to figure out. 
That could be the case if you can ping case #2, but not #3.

incubus

---

### Post by jturnbul on 2006-04-12
thanks for the quick replies.  found something in my dmesg where eth1 was being bridged to br0.  I had set up the bridge a few days ago for QEMU, but never did a reboot.  The reboot obviously put br0 into effect, and it wasnt configured properly.  Anyways commented out the br0 in my /etc/network.interfaces and that fixed it, and QEMU still works with networking.

Thanks again.

---

