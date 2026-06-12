---
title: "Setting up internet conection on new Unbuntu server"
date: 2012-05-02
forum: General Help
---

### Post by chorvath on 2012-05-02
On my new tower server I am having problems setting up internet connection. 
When I run this commmand "sudo lshw -class network" I get

        *-network
            description: Ethernet interface
            product: NetXtreme BCM5723 Gigabit Ethernet PCIe
            vendor: Broadcom Corporation
            physical id: 0
            bus info: pci@0000:1e:00.0
            logical name: eth0
            version: 10
            serial: 10:1f:74:3b:e5:7f
            size: 1Gbit/s
            capacity: 1Gbit/s
            width:  64 bits
            clock: 33MHz
            capabilities: pm vpd msi pciexpress bus_master cap_list enthernet physical 
        tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd antonegotiation
            configureation: autonegotiation=on broadcast=yes driver=tg3 
        driverversion=3.119 duplex=full firmware=5723-v3.35, IPMILITE
        v8.07 latency=0 link=yes mlticast=yes port=twisted pair speed=1Gbit/s
            resources: irq:44 memory:df900000-df90ffff

The internet isn't working, suggestions? (I'm brand new at unbuntu server)

---

### Post by acc61287 on 2012-05-03
try ifconfig to show your ip

---

### Post by newbie-user on 2012-05-03
There are a great number of possibilities here. Did you set your ip statically? Is your DHCP server running?

---

