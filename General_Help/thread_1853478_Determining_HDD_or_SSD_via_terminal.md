---
title: "Determining HDD or SSD via terminal?"
date: 2011-10-02
forum: General Help
---

### Post by Ikthel on 2011-10-02
Is there any commands that could differentiate between whether your computer is using an SSD or HDD? 
(Need the information to to help out on a script)

If so could someone please post it along with an example of the output? 

Thanks in advance! :)

---

### Post by relay_man on 2011-10-03
Run "lshw" from terminal to give details of all hardware including the hard disk.  (ls = list   hw = hardware)

Be sure to precede this command with "sudo" or Ubuntu will complain.

It is likely the corresponding list will be lengthy.

Below is a portion of the output from my machine.



          *-disk
                description: ATA Disk
                product: WDC WD1600AAJS-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WMAV30582589
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0014e772



Hope this helps

---

### Post by dcstar on 2011-10-03
> **Ikthel said:**
> Is there any commands that could differentiate between whether your computer is using an SSD or HDD? 
(Need the information to to help out on a script)

If so could someone please post it along with an example of the output? 


```
grep . /sys/class/block/sd*/queue/rotational
```
These are all non-SSDs in my system, SSDs are supposed to return 0:
```
/sys/class/block/sda/queue/rotational:1
/sys/class/block/sdb/queue/rotational:1
/sys/class/block/sdc/queue/rotational:1
/sys/class/block/sdd/queue/rotational:1
/sys/class/block/sde/queue/rotational:1
/sys/class/block/sdf/queue/rotational:1
```

---

