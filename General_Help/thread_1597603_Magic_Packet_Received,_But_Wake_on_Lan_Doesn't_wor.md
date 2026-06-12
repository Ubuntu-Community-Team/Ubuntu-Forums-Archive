---
title: "Magic Packet Received, But Wake on Lan Doesn't work"
date: 2010-10-15
forum: General Help
---

### Post by lorderico on 2010-10-15
Hello,

I am trying to remotely wake up my computer.  I am using the wakeonlan tool as follows wakeonlan -i 146.x.x.x 00:0f:...

I have used wireshark on the remote computer and verified it was getting the magic pack.  wireshark sees the packet, and immediately the remote computer sends an ICMP dest. unreachable (port unreachable) packet back, although I assume that is normal.
On the remote computer, I used ethtool so I am enable to verify that suports wake-on is set to "g" or magic packet.

I believe that wake-on-lan is enabled in the bios.  I have a hp dc5000, so I turned on S5 wake on lan in the bios.  However, the computer does not wake up.

My assumption is that once the computer is off, the router doesn't know where to send to packet because that ip is not there anymore.  Does that make any sense?  What other troubleshooting steps can I take?  I don't have control over the routers though.

Thanks a lot,

Eric

---

### Post by manuelb on 2010-10-15
(EDIT: i assume your Wireshark tests are correct and the machine is receiving the MagicPacket)

I've been setting up an automated backup in my office and had the need to switch on/off the machines at night hours.
One of the machines is running Ubuntu 9.04 and i had to setup quite a few things, however, there is a quite huge thread here on ubuntuforums.org (edit: it should be [this](http://ubuntuforums.org/showthread.php?t=234588))full of various information.
Although ethtool show your network card support the MagicPacket, i had to also enable its PCI address in the acpi/wakeup **AND** uninstall the Network Manager since it was powering off the network card just before shutting the machine down; if you are going to try and remove it, make sure you can configure the network manually first!
Else, you could try to locate the PCI node with:

```

lspci|grep -i ether

```

The output should be prefixed by a number, mine is "00:19.0".
Then, look at what your proc fs say about it:

```

cat /proc/acpi/wakeup

```

You should be able to locate the same sysfs node in the last column just in a slightly different form, mine is "pci:0000:00:19.0".
Lookup the "S-state" and the "status" columns; in my case, i got the network card sysfsnode disabled and had to enable it by echoing the device name ("Device" column) to the proc fs this way:

```

sudo -s
echo <your_device_name> > /proc/acpi/wakeup

```

Note that, at every boot, i run a script that check the state of the device and enable it, then the ethtool is run to enable the wake-on-lan feature on the network card: just add those to your /etc/network/interfaces via "post-up" and "pre-down" (once you uninstalled the NetworkManager else it will overwrite your changes).

I could post my scripts but if you need them you'll need to wait for the whole weekend since i don't have access to the office until Monday ;)

Another note: if you own a forcedeth/nforce4 based network card, try to reverse the MAC address as per [this](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288053)

---

### Post by pricetech on 2010-10-15
I doubt it's going to work over a router since a WOL packet is broadcast, specifically dropped by routers.

You say you have no control over the routers.  Is there another computer on the subnet you can remote into ???

---

