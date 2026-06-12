---
title: "NetworkManager: &quot;Create New Wireless Network&quot; -- &quot;Create&quot; button grayed out"
date: 2010-05-28
forum: General Help
---

### Post by DoubleRing on 2010-05-28
EDIT:  Whoops.  Just realized that there is a Networking subforum.  Apologies.

In 10.04, I am able to get to the dialog in NM that asks for the network name and security for the creation of a new wireless network.  However, the "Connect" button is grayed out and filling out all fields doesn't allow me to press it.  I assume that this means that either there is a problem with my configuration or that my network card is not supported.

Here is the lshw entry for my wireless card:

```
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wlan0
                version: 61
                serial: 00:13:e8:6e:ab:c3
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:29 memory:f9ffe000-f9ffffff

```

On a tangential note, am I assuming the correct usage of this function?  My original intention was to share out an ethernet connection via wireless.

Thanks in advance!

EDIT2: Well, I was able to make an ad hoc connection via "Edit Connections"  This seems to be a bug in the NetworkManager dialog.

---

### Post by gerbman on 2010-08-14
> **DoubleRing said:**
> EDIT:  Whoops.  Just realized that there is a Networking subforum.  Apologies.

In 10.04, I am able to get to the dialog in NM that asks for the network name and security for the creation of a new wireless network.  However, the "Connect" button is grayed out and filling out all fields doesn't allow me to press it.  I assume that this means that either there is a problem with my configuration or that my network card is not supported.

Here is the lshw entry for my wireless card:

```
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wlan0
                version: 61
                serial: 00:13:e8:6e:ab:c3
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:29 memory:f9ffe000-f9ffffff

```

On a tangential note, am I assuming the correct usage of this function?  My original intention was to share out an ethernet connection via wireless.

Thanks in advance!

EDIT2: Well, I was able to make an ad hoc connection via "Edit Connections"  This seems to be a bug in the NetworkManager dialog.

Were you able to get the "Connect" button to be not grayed out?

---

### Post by DoubleRing on 2010-08-16
> **gerbman said:**
> Were you able to get the "Connect" button to be not grayed out?

When I first tried it, it never worked as long as "New" was selected under Connection.  However, I have just tried it again, and the problem appears to have been fixed.

---

### Post by gerbman on 2010-08-16
Yeah, it looks like they released the fix a few days ago. Thanks for the reply.

---

### Post by deerewright on 2010-09-06
How did you resolve this?  I have the same problem, updated my system, but Create button is still greyed out, and if I use "Edit Connections", "Connect" button remains greyed out.

Ubuntu 10.04 64bit

---

### Post by deerewright on 2010-09-07
Here is my workaround that worked for me:

Left click on Network Manager applet, select "Connect to Hidden Wireless Network...", leave Connection set to "New", name your network and select security level.  Then the "Connect" button will be selectable, and you can connect, or edit from there.

---

