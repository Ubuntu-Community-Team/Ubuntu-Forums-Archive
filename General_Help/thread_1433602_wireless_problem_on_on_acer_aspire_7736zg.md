---
title: "wireless problem on on acer aspire 7736zg"
date: 2010-03-19
forum: General Help
---

### Post by eternal243 on 2010-03-19
Hello, I first used Ubuntu in 2008 but due to different reasons I haven't had access to that computer for almost 2 years now and decided to give it another try.
 
I installed Ubuntu 9.10 64-bit on an acer aspire 7736zg a few days ago through Wubi in Windows 7. Most things have worked out well so far, but there is one problem that keeps bugging me that I can't seem to figure out on my own.

I have a wireless connection where I live, and it always work fine when I log in to Ubuntu, sometimes for 10 minutes and sometimes as long as 6 hours, then suddenly I will get disconnected and I won't be able to reconnect until I restart my computer. I usually have to restart around 7-10 times every day because of this issue.

I'm still kind of new to using Ubuntu and don't have so much knowledge of different commands and so on so have patience with me. Any help to solve this would be greatly appreciated.

Here is my **lshw -C network** output.

```
sten@ubuntu:~$ sudo lshw -C network
[sudo] password for sten: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:26:2d:68:34:01
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v2.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:31 memory:f5100000-f510ffff
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 90:4c:e5:39:17:66
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.2.102 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f5200000-f520ffff

```

**[COLOR="Red"]EDIT:[/COLOR]**I just realized i should have posted this in the Networking and Wireless category. It would be good if a moderator could move it to the right place. Sorry for not thinking before posting!

---

### Post by tom4everitt on 2010-03-19
Instead of restarting the entire computer, it might suffice with restarting network mangager:

sudo service network-manager restart

or to unload and load the wireless driver:

sudo modprobe -r ath9k 
sudo modprobe ath9k





What could offer a more permanent solution is a newer kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) (choose a linux-image-...).

You have 2.6.31 now, you could try one of the newer, since they would probably feature newer (and possibly more stable) drivers. There might be drawbacks as well though as your system is not built for them.

Be sure to let us know how it goes, its very useful for other users with the same problem!

---

### Post by eternal243 on 2010-03-19
Thanks for your reply, i'll try your first two suggestions when my connection drops next time. I might also try updating the kernel but i would rather not try that as my first solution. I'll update this thread once i manage to solve the problem.

---

### Post by eternal243 on 2010-03-22
For future reference the command **sudo service network-manager restart** made my computer freeze and I needed to restart with alt+sysrq+reisub.

The commands **sudo modprobe -r ath9k**, **sudo modprobe ath9k** work some of the times with the first command sometimes locking up.

I have also tried to recompile my current kernel with some help from a friend and it didn't work. My next step will probably be to try and upgrade the kernel. Although after the last automatic update with the update manager the problem seems to occur less frequently and also sometimes i'm able to reconnect to the wifi in the normal way.

---

### Post by tom4everitt on 2010-03-22
Hmm, okay. Weird that it locked your computer, it shouldn't. Sorry it didn't work anyway. 

Yeah, your card will most likely get better support with time. If you want you can try the ubuntu lucid beta, its out now and seems pretty cool (and it also comes with a newer kernel).

---

### Post by eternal243 on 2010-03-22
well (i think) i have located the problem with the sudo modprobe locking up sometimes, it seems to lock up whenever "empathy" is running in the background which is almost all the time since it is integrated with ubuntu. but if i manually kill the empathy process before running the sudo modprobe command, then it seems to work. 

so far i have only tried restarting the network manager once and it didn't work, but i can try it again to see if it will still lock up my computer, both with and without empathy running in the background.

---

### Post by tom4everitt on 2010-03-22
Aah, okay that could be. Its still a bug, empathy shouldn't hang your computer just cause your internet disappears... But then again, its a bug that you have to restart your internet in the first place, so whatever works :)

---

### Post by Donall on 2010-04-15
download the software from [www.acer.com](www.acer.com) its work because i also have acer5738z and its wireless create problem but after download from web site its working well so you must try it.best of luck:lolflag:

---

### Post by nofuture on 2010-04-15
> **Donall said:**
> download the software from [www.acer.com](www.acer.com) its work because i also have acer5738z and its wireless create problem but after download from web site its working well so you must try it.best of luck:lolflag:

Thanks for that!

---

### Post by galuzyaki on 2010-04-26
Installing acer drivers should take care of your problem. Good Luck

---

### Post by Elif on 2010-04-27
I don't get it.. I don't see any linux drivers on the acer site... should I install the windows drivers with wine? NDISwrapper?

can someone please provide additional details?

Thanks,
Eli

---

### Post by andisl on 2011-04-19
Hello!

Did you find solution for your problem?

Andis

---

