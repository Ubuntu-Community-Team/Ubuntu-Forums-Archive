---
title: "Running Ubuntu from VMWARE = No internet"
date: 2006-06-16
forum: General Help
---

### Post by shaynaynay on 2006-06-16
Hi there.
I'm using win xp pro, running latest version of vmware workstation.
I can't connect to the internet from ubuntu (which is running of the VM).

I tried every setting in VM and in Ubuntu: Bridge, Nat, whatever...
I tried a static IP (I'm using router), I tried DHCP... nothing.

What am I doing wrong?
It used to work once.. I don't remeber what I've changed.
(I have in "my connections" [on the xp] vmnat0 and vmnat8 installed by VM).

Thanks!

---

### Post by scxtt on 2006-06-16
what does "ifconfig -a" produce in ubuntu?

and what IPs are addressed to your vmnets in XP?

---

### Post by shaynaynay on 2006-06-17
When VMWARE is set to use VMnet8 (which its IP is 192.168.1.5) and Ubuntu is set to DHCP, ifconfig -a shows:
[[IMG]http://img83.imageshack.us/img83/1618/15li1.th.jpg[/IMG]](http://img83.imageshack.us/my.php?image=15li1.jpg)

and when Ubuntu is set to static IP (192.168.1.5) I get this:
[[IMG]http://img133.imageshack.us/img133/1531/26cs2.th.jpg[/IMG]](http://img133.imageshack.us/my.php?image=26cs2.jpg)

Thanks!
(I have a windows XP of the VM too, which is set to Bridge (in VM) and gets auto IP, internet works great).

---

### Post by scxtt on 2006-06-17
i see that you said you've tried everything, but i've only used "NAT" for the VM setting and DHCP in the OS of the VM - that's all that's ever worked for me ... including right now, i'm running XP as a VM in ubuntu ...

---

