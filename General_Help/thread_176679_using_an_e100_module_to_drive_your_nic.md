---
title: "using an e100 module to drive your nic?"
date: 2006-05-15
forum: General Help
---

### Post by dmizer on 2006-05-15
after the latest round of updates, i had the worst time trying to get online via my wired Intel(R) PRO/100 Network card.

i tried everything i could think of, and everything i could find in the forums including directly editing network.conf.

sometimes i could get online for a brief amount of time but then i dropped again, it was extremely frustrating and puzzling.

but i fixed it with the following action:
```
sudo modprobe -r e100
sudo modprobe e100
```
then i reconfigured my network and no problems, even after reboot.

don't know what happened exactly, but i wanted to post this up here in case someone else is still strugling with the same problem.

---

### Post by dargaud on 2006-06-02
Well, I'm just trying Ubuntu for the first time (6.06) on my old laptop and I have the same problem but your workaround doesn't seem to do anything in my case.
During boot I get "E100_EEPROM_LOAD: EEPROM corrupted" and also "e100 probe failed with error -11"

BUT the NIC works fine under Win2K and Knoppix 3.3.

When I try your workaround, I get:
insmod /lib/modules/2.6.15-23-386/kernel/drivers/net/mii.ko
insmod /lib/modules/2.6.15-23-386/kernel/drivers/net/e100.ko

But then I don't see any difference in ifconfig (still only the loopback and a address-less eth0) or the [System][Administration][Networking]
Maybe I need to request a new DHCP lease but dhclient returns "No DHCPOFFERS received"

Note: I'm still on the bootable CD, so it may make a difference.

---

### Post by dargaud on 2006-06-02
Well, I'm just trying Ubuntu for the first time (6.06) on my old laptop and I have the same problem but your workaround doesn't seem to do anything in my case.
During boot I get "E100_EEPROM_LOAD: EEPROM corrupted" and also "e100 probe failed with error -11"

BUT the NIC works fine under Win2K and Knoppix 3.3.

When I try your workaround, I get:
insmod /lib/modules/2.6.15-23-386/kernel/drivers/net/mii.ko
insmod /lib/modules/2.6.15-23-386/kernel/drivers/net/e100.ko

But then I don't see any difference in ifconfig (still only the loopback and a address-less eth0) or the [System][Administration][Networking]
Maybe I need to request a new DHCP lease but dhclient returns "No DHCPOFFERS received"

Note: I'm still on the bootable CD, so it may make a difference.

---

### Post by dargaud on 2006-06-02
Sorry for the double post, I got an error message first try.

A precision: after checking dmesg of the working Knoppix, I figured it was using eepro100 instead of e100. Now both Gentoo 2006 livecd and Ubuntu livecd make the mistake and try to use e100 instead. Now if I boot gentoo with the kernel options "noload=e100 doload=eepro100" it works. The same command has no effect with Ubuntu (different kernel syntax ?)

Thanks for any complementary info.

---

### Post by dmizer on 2006-06-02
you could try (no idea if it will work, but it won't hurt anything if it doesn't) ...
```
sudo modprobe -r e100
sudo modprobe eepro100
```
then do a lsmod to verify that the module loaded for your nic.  if not, post back.

---

### Post by dargaud on 2006-06-02
Well, I tried that, taking into account the fact that eepro100 is blacklisted in /etc/modprobe.d/blacklist (I inverted the blacklist).
In both cases I get an empty eth0:
[FONT="Lucida Console"]  Link encap:Ehternet HWaddr:....
  UP BROADCAST MULTICAST MTU:1500 Metric:1
  RX:0 error:0 dropped:0 Overruns:0 frame:0
  TX:0 errors:0 dropped:0 overruns:0 carrier:0
  collisions:0...
  Interrupt:3 Base Addr:0x100[/FONT]
If I call [FONT="Lucida Console"]dhclient[/FONT], it fails, and if I force "[FONT="Lucida Console"]ifconfig eth0 192.168.1.5[/FONT]", I still don't get a comm (no RX/TX).

I feel like I'm missing something elementary but can't figure it out.

---

