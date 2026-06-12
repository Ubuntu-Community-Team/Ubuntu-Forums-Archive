---
title: "RTL8139 driver"
date: 2006-06-29
forum: General Help
---

### Post by aaronvegh on 2006-06-29
Hi there,
I seem to be having trouble with my ethernet hardware, and possibly as a result Ubuntu didn't install a suitable driver for my card during installation. Now I'm trying to troubleshoot the card but I want to install the driver. Keeping in mind that I don't have network access on this machine, how would I acquire the RTL8139 driver that works with Ubuntu? I tried the Red Hat source code available on the Realtek site but it spat out a whack of errors before dying. 

Thanks!
Aaron.

---

### Post by hayalci on 2006-06-29
There are two drivers for 8139; 8139too and 8139cp
Try the following on a terminal window;
```
sudo modprobe 8139too
sudo modprobe 8139cp
```

Then diagonize the problem by issuing
```
sudo ifconfig -a
dmesg|tail
```

If the driver is OK, ifconfig should show your ethernet device as eth0 or so. If there is no ethernet device, dmesg may have printed error messages. You may also verify your ethernet card's chipset by issuing "lspci" command.

---

### Post by aaronvegh on 2006-06-29
Hi there,
Thanks for writing back! There is progress to report...

I ran the modprobe's as you suggested and by god, it worked! So I guess I never needed to install the drivers anyway.

After that I ran dmesg again, and it showed entries for both ethernet controllers. Just to be sure it stuck, I rebooted, and then ran lspci... and it showed an ethernet controller! W00t!

But then I ran ifup eth0 (btw, ifconfig showed eth0 without an address) and it couldn't pick up an address from my dhcp server. Hmm... I'm going to keep plugging away, and we'll see where we get. Thanks for your help so far!

Cheers,
Aaron.

---

### Post by FuturePast on 2006-06-29
Try:
```
sudo dhclient eth0
```

If that works edit /etc/network/interfaces to add the line
```
iface eth0 inet dhcp
```

---

### Post by hayalci on 2006-06-29
[QUOTE=aaronvegh]Hi there,
.....
After that I ran dmesg again, and it showed entries for both ethernet controllers. Just to be sure it stuck, I rebooted, and then ran lspci... and it showed an ethernet controller! W00t!....
[/QUOTE]

If the drivers are not modprobed automatically, your reboot must have unloaded them. You can check it by "lsmod" command, output will contain the driver's name (8139(too|cp)) if the driver is loaded. [ sidenote: use "lsmod | grep 8139" for easy spotting of the driver ] To make it load at every reboot, you should add its name to /etc/modules file, one line for each module.

lspci will show the ethernet card regardless of the driver's status.

And, after the driver is loaded,it is perfectly fine to use shiny GUI for network configuration :)

---

### Post by aaronvegh on 2006-06-29
Hi there,
Thanks for all your input. Turns out that there's a hardware defect with the onboard ethernet controller; a call to Asus (pronounced A-sooos, not Asuss! Am I the only one who didn't know that?) determined that. I'm going to RMA the barebone, and hopefully be up and running next week.
Cheers!
Aaron.

---

