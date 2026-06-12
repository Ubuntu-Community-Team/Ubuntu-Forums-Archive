---
title: "Ownership of /dev/sdd* keeps changing back to root:root"
date: 2011-02-09
forum: General Help
---

### Post by grahambo2005 on 2011-02-09
Hi All

I'm having an issue trying to install a piece of Oracle Software.... namely 11gR2 Grid Infra.

basically what I need to do is give the oracle user (linux user) ownership of:
/dev/sdd

and the partitions I created for it:
/dev/sdd1
/dev/sdd2
/dev/sdd3
/dev/sdd4

So I run as root:
/dev# chown oracle:dba sdd1 sdd2 sdd3 sdd4 sdd

I verify ownership has changed and then run the Grid Configuration tool.
But the ownership of the /dev/sdd disk and its partitions all revert back to root ownership after a period of time.

I need to permanently to have the device ownership as oracle:dba

Is there any way to fix this?

Please note: These are empty partitions. I have not formated them with any File System (Oracle needs them this way)

Thanks
G.

---

### Post by dino99 on 2011-02-09
something related:

[http://www.pythian.com/news/13291/installing-oracle-11gr2-enterprise-edition-on-ubuntu-10-04-lucid-lynx/](http://www.pythian.com/news/13291/installing-oracle-11gr2-enterprise-edition-on-ubuntu-10-04-lucid-lynx/)

[https://mikesmithers.wordpress.com/2010/03/14/installing-oracle-11gr2-on-ubuntu-9-10/](https://mikesmithers.wordpress.com/2010/03/14/installing-oracle-11gr2-on-ubuntu-9-10/)

---

### Post by grahambo2005 on 2011-02-09
Hey

Thanks Mate

I have had a look at those already.
I have figured out how to install the Oracle 11gR2 Database Software and set up a DB Successfully.

My Issue is with another Oracle Product Oracle 11gR2 Grid Infrastructure and setting up an Oracle ASM Managed Disk rather than OS Managed.

In order for me to do that I need to change the ownership of the disk to oracle rather than root. But it keeps switching back to root. :(

G.

---

### Post by Claus7 on 2011-02-09
Hello,

if I were in your shoes I would try something like:

```
sudo chown oracle:dba /dev/sdd
sudo chgrp oracle:dba /dev/sdd
```

Do you know whether this device is mounted. Is it mounted on the first place? If it does, and the mounting point is e.g. somewhere under /media then you should try the above commands pointing to /media...

Hope it will work,
Regards!

---

### Post by grahambo2005 on 2011-02-09
Thanks for the Reply Claus

No the Device Partitions are not Formated or mounted.
Basically the Oracle using user is supposed to take ownership of the Hard drives

If the Drives were mounted then the Operating System would own them.

This may be a job for one of the Oracle Forums. :(

G.

---

### Post by sisco311 on 2011-02-09
You have to create an udev rule. See: [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

If you need more help, please post the output of:
```
sudo udevadm info -a -p $(udevadm info -q path -n /dev/sdd)
```

---

### Post by coffeecat on 2011-02-09
> **grahambo2005 said:**
> I need to permanently to have the device ownership as oracle:dba

Is there any way to fix this?

Yes. You can "own" a Linux filesystem on a partition if you mount it and chown the mountpoint. This has the curious effect of owning the filesystem but not the mountpoint.

Create a temporary mountpoint, say /media/temp. Now mount it:

```
# mount /dev/sdd1 /media/temp
```Now own the fileystem:

```
# chown oracle:dba /media/temp
```The ownership will persist after unmounting and remounting, even on a different mountpoint. And you can prove that the ownership has affected the filesystem and not the mountpoint by doing a 'ls -l /media' before the chown, after the chown, after umounting and after remounting again.

Simply go through sdd2, sdd3 and sdd4 in turn.

Much easier than udev rules :wink: and seemingly a little-known phenomenon, judging by discussions on this forum. You can use chmod as well. The ownership/permissions seem to be stored in the root of the filesystem itself, but the exact details are beyond me.

---

### Post by grahambo2005 on 2011-02-09
Thanks for the replies Guys

I managed to get this "sorted"....


the ownership was actually root:disk

as opposed to root:root

So I have just added the oracle user to the disk group (Is this considered messy?)

I manged to create my first Oracle +ASM Disk groups and have manged to successfully install a Database on it.

sisco311:

I am interested in what you have suggested:

here is the output:

```
root@server003:~# udevadm info -a -p $(udevadm info -q path -n /dev/sdd)


Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.


  looking at device '/devices/pci0000:00/0000:00:14.0/host2/target2:0:0/2:0:0:0/block/sdd':
    KERNEL=="sdd"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{range}=="16"
    ATTR{ext_range}=="256"
    ATTR{removable}=="0"
    ATTR{ro}=="0"
    ATTR{size}=="41943040"
    ATTR{alignment_offset}=="0"
    ATTR{discard_alignment}=="0"
    ATTR{capability}=="50"
    ATTR{stat}=="   18409    62543   579594    47790    44950   418453  3499835   192630        0    75480   240420"
    ATTR{inflight}=="       0        0"


  looking at parent device '/devices/pci0000:00/0000:00:14.0/host2/target2:0:0/2:0:0:0':
    KERNELS=="2:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="6"
    ATTRS{vendor}=="VBOX    "
    ATTRS{model}=="HARDDISK        "
    ATTRS{rev}=="1.0 "
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0xf7f4"
    ATTRS{iodone_cnt}=="0xf7f4"
    ATTRS{ioerr_cnt}=="0x3"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_ramp_up_period}=="120000"
    ATTRS{queue_type}=="none"


  looking at parent device '/devices/pci0000:00/0000:00:14.0/host2/target2:0:0':
    KERNELS=="target2:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""


  looking at parent device '/devices/pci0000:00/0000:00:14.0/host2':
    KERNELS=="host2"
    SUBSYSTEMS=="scsi"
    DRIVERS==""


  looking at parent device '/devices/pci0000:00/0000:00:14.0':
    KERNELS=="0000:00:14.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="mptspi"
    ATTRS{vendor}=="0x1000"
    ATTRS{device}=="0x0030"
    ATTRS{subsystem_vendor}=="0x1000"
    ATTRS{subsystem_device}=="0x8000"
    ATTRS{class}=="0x010000"
    ATTRS{irq}=="20"
    ATTRS{local_cpus}=="00000000,00000001"
    ATTRS{local_cpulist}=="0"
    ATTRS{modalias}=="pci:v00001000d00000030sv00001000sd00008000bc01sc00i00"
    ATTRS{numa_node}=="-1"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{config}==""


  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


root@server003:~#
```

Regards
G.

---

### Post by sisco311 on 2011-02-09
Users in the disk group have read & write access to all hard disks, which is one step away from full root access.


To change the ownership of /dev/sdd you have to create a new .rules file in /etc/udev/rules.d/ (for example: /etc/udev/rules.d/80-oracle.rules) with the following content:

```
SUBSYSTEM=="block", ATTRS{vendor}=="0x1000", ATTRS{device}=="0x0030", OWNER="oracle", GROUP="dba", MODE="0660"
```

then reboot.

---

### Post by grahambo2005 on 2011-02-09
Thanks a Million for your help

I'll add that one to my documentation.

I'll be posting my final instructions on how to get Oracle 11gR2 Database and Grid Infrastructure working on ubuntu 10.10 shortly (I hope)

I will mention you in it for the help you have given me.

Thanks
G.

---

### Post by smannem on 2011-07-28
Did you finish your instructions on how to get Oracle 11gR2 Database and Grid Infrastructure working on ubuntu 10.10?
I'd like to see how you could get Oracle 11gR2 Grid Infra working on Ubuntu 10.10.
I'm trying to do the same, but I am stuck on errors running the second Root script.
The script tries to start CRS, but fails on read errors on the OCR.
I think I'm missing some libraries.

I'm using a Ubuntu 11.04 laptop with KVM and Ubuntu 10.10 Server VM's.
Hope you can help.

---

### Post by smannem on 2011-07-30
Is your instruction already available?
I'm trying to install Grid in Ubuntu 10.10, but I'm having problems with the root script.
It tries to start CRS but receives errors on the OCR.
I hope that your instructions shows me something that I'm missing (like a library).

---

### Post by jim boles on 2012-01-26
The solution of the rule worked for me. I was having the same problem.

Thx!

---

### Post by sisco311 on 2012-01-27
No problem. 

BTW, welcome to the forums, **jim boles**!

---

