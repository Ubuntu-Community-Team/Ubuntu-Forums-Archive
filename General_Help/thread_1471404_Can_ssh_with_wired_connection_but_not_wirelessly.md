---
title: "Can ssh with wired connection but not wirelessly"
date: 2010-05-03
forum: General Help
---

### Post by madwoollything on 2010-05-03
I'm trying to set up an ssh connection using openssh-server using the wireless connection to a friend's laptop.

I have ssh working if I plug a LAN cable into the laptop, but as soon as I try to use a wireless connection, ssh no longer works. I've found various posts suggesting creating different profiles for wired and wireless connections, but this fix does not appear to work for me.

I've just put a fresh copy of lucid 10.04 onto the laptop. (Previously running Hardy with no issues with ssh over a wireless connection)

I've repeated the same tests but using a different laptop running Jaunty and have the same results, I'm able to connect via ssh with a wired connection but not using a wireless connection.

I also get the same behaviour if I use the remote desktop feature on both laptops. Either will connect with a LAN connection but not wirelessly, which indicates that VNC is behaving in the same way as ssh.

I'm beginning to suspect that the problem is possibly with network manager and the way wireless connections are configured?? It is odd that it should affect different versions of Ubuntu. (No firewalls are running).

Any ideas would be appreciated as this has me stumped (and is preventing me from being able to remote support other's machines)

Found this which I think is linked to my problem [https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/360038](https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/360038)

---

### Post by madwoollything on 2010-11-01
I'm still struggling with this problem where I'm able to connect with wired connection but not through a wireless connection. This is happening across a number of machines.

I'd really appreciate some help and where to find the error log that might shed some light on what is happening.

---

### Post by Wayne_V on 2010-11-01
what is the output of "sudo ifconfig -a" when wired and when not?

try "nmap <ip address>" of both the wired and wireless NIC as well.

---

### Post by madwoollything on 2010-11-06
> **Wayne_V said:**
> what is the output of "sudo ifconfig -a" when wired and when not?

try "nmap <ip address>" of both the wired and wireless NIC as well.

Many thanks ..... something to investigate. The problems I have may be hardware related ..... more investigations to do!

---

