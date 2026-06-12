---
title: "Can't see network after reboot"
date: 2009-07-21
forum: General Help
---

### Post by Buuntu on 2009-07-21
I'm getting very frustrated!
While trying to solve a problem related to screen resolution, I was required to reboot after installing the latest nvidia drivers.  After restarting though, I find out I have no internet!  Not only that, but I can't even see it on network connections.  It can't be my wireless card, since I'm connected to the router through an Ethernet cable, and I know it's not the hardware since the internet works fine on my windows partition.  Help please???

---

### Post by cariboo on 2009-07-21
Can you open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network > network.txt
```

the above command will create a text file called network.txt that you can copy to your windows partition and paste it into your next post.

---

### Post by Buuntu on 2009-07-22
*-network UNCLAIMED
       description: Ethernet controller
       product: Marvell W8300 802.11 Adapter
       vendor: Marvell Technology Group Ltd.
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 07
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5a:41:6d:a9:22:0b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Buuntu on 2009-07-23
Can you see what's wrong with it?

---

### Post by Buuntu on 2009-07-23
Ok, so I got it back to working by changing the settings of eth0 in /etc/network/interfaces to DHCP instead of static (I had set it to static for another purpose).  I don't think it lets you set up an ip adress the same as your windows partition if you're dual booting, but that's just a guess (it also said there is an ip adress conflict on my windows partition when the internet was down).  Now the only problem is that it still doesn't show in the network connections icon at the top right of the screen.  This is just a minor annoyance but it would be nice to get it to work again.

---

### Post by dcstar on 2009-07-23
> **Buuntu said:**
> Ok, so I got it back to working by changing the settings of eth0 in /etc/network/interfaces to DHCP instead of static (I had set it to static for another purpose).  I don't think it lets you set up an ip adress the same as your windows partition if you're dual booting, but that's just a guess (it also said there is an ip adress conflict on my windows partition when the internet was down).  Now the only problem is that it still doesn't show in the network connections icon at the top right of the screen.  This is just a minor annoyance but it would be nice to get it to work again.

Modifying the /etc/network/interfaces stuff bypasses the dynamic settings that the Ubuntu Network manager does. You basically need an empty file there and then allow the Network Manager load and set things up (and display things....).

I actually have uninstalled the Network Manager and gone back to using the old gnome-network-admin package because I found that the Network Manager starts so late in the boot up process (and takes so long to get going) that other packages that need network connectivity fail.

---

### Post by Buuntu on 2009-07-23
You mean the interfaces file should be an empty file?  I'm not sure if I understood you.

---

