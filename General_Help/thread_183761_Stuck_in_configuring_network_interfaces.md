---
title: "Stuck in configuring network interfaces"
date: 2006-05-28
forum: General Help
---

### Post by JaredW on 2006-05-28
I installed Kubuntu on a iMac.  All went well.  When I had to reboot it, it goes through and gets stuck on the "Configuring network interfaces" stage.  Sometimes it stays like that for about an hour and sometimes my screen goes blank in about five minutes.  Due to no more room on my router, I am using a cross-over cat5 cable from my PC to my Kubuntu.  In my PC I bridged the two netowork devices.  I just need to know what is going on,  Thanks.

---

### Post by hakker.de on 2006-05-29
I would suggest trying the following:
1. Boot the Kubuntu iMac in single user mode and configure the network manually with ifconfig. Then do a ping to the PC and if this works to the router. If this works, too, then something is wrong with DHCP.
2. Configure your PC as a gateway without bridging the devices and instead with different networks on eth0 and eth1. As supposedly the PC has no DHCP daemon running, step 1. is necessary, too.

---

### Post by JaredW on 2006-05-30
I don't understand what you mean.  I am not very good with networks related issues.  I also don't know how to boot in single user mode.

---

### Post by hakker.de on 2006-06-05
After BIOS booting, the bootloader grub shows with some text messages similar to: "... press escape for boot-menu ...". Then press ESC and choose the second entry: Ubuntu, kernel 2.6.15-23-386 (recovery mode)
This should boot the computer to a bash prompt, where you can test some network configurations.

Besides, what about buying a little switch, and connect it with the router. They are quite cheap these days, and no hassle with crossover cable, and using the PC as a router.

---

