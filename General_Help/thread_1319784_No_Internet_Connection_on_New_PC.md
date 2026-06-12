---
title: "No Internet Connection on New PC"
date: 2009-11-08
forum: General Help
---

### Post by rgd55 on 2009-11-08
I just built a pc from the following parts:
   Gigabyte GA-G31M-ES2L motherboard with on board ethernet controller
   Intel Pentium E5200
   1 gb of ram
  I loaded Windows XP Pro first and Ubuntu 9.04 next as a dual
 boot pc.Both operating systems will boot,however only
 Windows will connect to the internet.
  Ubuntu does not.I did a few commands in the terminal last night after
 doing some searching and it appears my onboard ehternet is made
 by a company called Attansic Technologies Corp.
   This is about all the info I have now.I really need Ubuntu   
 online.**Please Help**

---

### Post by cariboo on 2009-11-08
Could you please paste he output of:

```
sudo lshw -C network
```

in your next post.

---

### Post by rgd55 on 2009-11-08
*-network Unclaimed
    description:Ethernet controller
    product:Attansic Technology Corp.
    vendor:Attansic Technology Corp.
    physical id:0
    bus info:pci@0000:02:00.0
    version:c0
    width:64 bits
    clock:33MHz
    capabilities:pm msi pciexpress vpd bus_master cap_list
    configuration:latency=0
*-network DISABLED
     description:Ethernet interface
     physical id: 1
     logical name:pan0
     serial:96:c4:59:20:99:f8
     capabilities:broadcast=yes driver=bridge driverversion=2.3 firmware=N/A Link=yes

---

### Post by rgd55 on 2009-11-09
Can anyone help me with this?
I am thinking that I should look into
getting a ubuntu supported pci ethernet card as
a last resort.

---

