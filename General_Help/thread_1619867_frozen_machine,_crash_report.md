---
title: "frozen machine, crash report?"
date: 2010-11-12
forum: General Help
---

### Post by anthalamus on 2010-11-12
Hi everyone,
where can I find logs after my box crashes (freezing)? it happens like once a week on average, and I have no idea why... even the magic key (sysreq) has no effect whatsoever. 
I can't find anything informative in /var/log/messages or /var/log/syslog... i think it has do to with either the x server or with gnome itself...
thanks,
Anthony

---

### Post by anthalamus on 2010-11-15
really, no one..? :(
it crashed again over the weekend... saturday around 3pm, that's when the last entry says in syslog. I have absolutely no idea how to go about fixing that issue...! maybe upgrading from 10.04 to 10.10?

---

### Post by kimberlite on 2010-11-15
You should provide some more info on your crashes. Post your output of 
```
tail /var/log/dmesg 
```
immediately after it happens next time.

Also some info on your hardware would be useful.

---

### Post by cucu007 on 2010-11-15
> **anthalamus said:**
> really, no one..? :(
it crashed again over the weekend... saturday around 3pm, that's when the last entry says in syslog. I have absolutely no idea how to go about fixing that issue...! maybe upgrading from 10.04 to 10.10?


try posting the output of dmesg to see how we can assist you.

# cat /var/log/dmesg > crash-dump.txt

And paste the content to a reply.

---

### Post by anthalamus on 2010-11-25
Hi guys, first of all thanks a lot for your help!
It crashed again and this time I backed up the whole /var/log folder right after it. I attached a tarball of the dmesg files (dmesg and dmesg.0). I've tried to read through it myself but am not sure what to look for..!
thanks,
Anthony

PS: I upgraded to 10.10 last week and here's some info about the hardware:

```

lshw -short
H/W path             Device      Class          Description
===========================================================
                                 system         7484ANU
/0                               bus            LENOVO
/0/0                             memory         125KiB BIOS
/0/4                             processor      Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz
/0/4/5                           memory         16KiB L1 cache
/0/4/6                           memory         6MiB L2 cache
/0/4/1.1                         processor      Logical CPU
/0/4/1.2                         processor      Logical CPU
/0/4/1.3                         processor      Logical CPU
/0/4/1.4                         processor      Logical CPU
/0/1e                            memory         5GiB System Memory
/0/1e/0                          memory         1GiB DIMM DDR2 Synchronous 1067 MHz (0.9 ns)
/0/1e/1                          memory         2GiB DIMM DDR2 Synchronous 1067 MHz (0.9 ns)
/0/1e/2                          memory         1GiB DIMM DDR2 Synchronous 1067 MHz (0.9 ns)
/0/1e/3                          memory         1GiB DIMM DDR2 Synchronous 1067 MHz (0.9 ns)
/0/1                             processor      
/0/1/1.1                         processor      Logical CPU
/0/1/1.2                         processor      Logical CPU
/0/1/1.3                         processor      Logical CPU
/0/1/1.4                         processor      Logical CPU
/0/2                             processor      
/0/2/1.1                         processor      Logical CPU
/0/2/1.2                         processor      Logical CPU
/0/2/1.3                         processor      Logical CPU
/0/2/1.4                         processor      Logical CPU
/0/3                             processor      
/0/3/1.1                         processor      Logical CPU
/0/3/1.2                         processor      Logical CPU
/0/3/1.3                         processor      Logical CPU
/0/3/1.4                         processor      Logical CPU
/0/100                           bridge         4 Series Chipset DRAM Controller
/0/100/1                         bridge         4 Series Chipset PCI Express Root Port
/0/100/1/0                       display        G98 [GeForce 8400 GS]
/0/100/3                         communication  4 Series Chipset HECI Controller
/0/100/3.2                       storage        4 Series Chipset PT IDER Controller
/0/100/3.3                       communication  4 Series Chipset Serial KT Controller
/0/100/19            eth0        network        82567LM-3 Gigabit Network Connection
/0/100/1a                        bus            82801JD/DO (ICH10 Family) USB UHCI Controller #4
/0/100/1a.1                      bus            82801JD/DO (ICH10 Family) USB UHCI Controller #5
/0/100/1a.2                      bus            82801JD/DO (ICH10 Family) USB UHCI Controller #6
/0/100/1a.7                      bus            82801JD/DO (ICH10 Family) USB2 EHCI Controller #2
/0/100/1b                        multimedia     82801JD/DO (ICH10 Family) HD Audio Controller
/0/100/1d                        bus            82801JD/DO (ICH10 Family) USB UHCI Controller #1
/0/100/1d.1                      bus            82801JD/DO (ICH10 Family) USB UHCI Controller #2
/0/100/1d.2                      bus            82801JD/DO (ICH10 Family) USB UHCI Controller #3
/0/100/1d.7                      bus            82801JD/DO (ICH10 Family) USB2 EHCI Controller #1
/0/100/1e                        bridge         82801 PCI Bridge
/0/100/1f                        bridge         82801JDO (ICH10DO) LPC Interface Controller
/0/100/1f.2          scsi0       storage        82801JD/DO (ICH10 Family) SATA AHCI Controller
/0/100/1f.2/0        /dev/sda    disk           160GB Hitachi HDP72501
/0/100/1f.2/0/1      /dev/sda1   volume         142GiB EXT3 volume
/0/100/1f.2/0/2      /dev/sda2   volume         6236MiB Extended partition
/0/100/1f.2/0/2/5    /dev/sda5   volume         6236MiB Linux swap / Solaris partition
/0/100/1f.2/1        /dev/cdrom  disk           DVD-RAM GH10N
/0/100/1f.2/0.0.0    /dev/sdb    disk           500GB ST3500820AS
/0/100/1f.2/0.0.0/1  /dev/sdb1   volume         196MiB EXT3 volume
/0/100/1f.2/0.0.0/2  /dev/sdb2   volume         465GiB Linux LVM Physical Volume partition
/0/100/1f.3                      bus            82801JD/DO (ICH10 Family) SMBus Controller
/1                               system         
/2                               power          Diamond MM #87997/1845333

```

---

### Post by anthalamus on 2011-03-08
bump...

this is still on recurring problem for me, it occurs every 3-5 days or so. i attached a tarball of my dmesgs. Here's an excerpt highlighting messages like "error", "not found", ...:

```

[    0.361871] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.361876] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701b9d8), AE_ALREADY_EXISTS
[    0.361881] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.365730] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.365735] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701b9d8), AE_ALREADY_EXISTS
[    0.373718] HEST: Table is not found!
[    0.404035] system 00:01: [mem 0xfed45000-0xfed8ffff] could not be reserved
[    0.467990] ERST: Table is not found!
[    0.516391] PM: Resume from disk failed.
[    0.516737] EDD information not available.
[   28.018938] apm: BIOS not found.

```

The "PM: Resume from disk failed." is the most worrying one i guess, should i infer that my disks are simply faulty?

here's df's output:

```

$ df -T
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda1     ext3   147549816 124251788  15802904  89% /
none      devtmpfs     1735828       256   1735572   1% /dev
none         tmpfs     1741432      3560   1737872   1% /dev/shm
none         tmpfs     1741432       324   1741108   1% /var/run
none         tmpfs     1741432         0   1741432   0% /var/lock

```

I used smartctl for a quick check but everything passed:

```

sudo smartctl -i /dev/sda1
sudo smartctl -d ata -H /dev/sda1

```

any ideas?

---

### Post by anthalamus on 2011-05-10
bump....

still pretty desperate here, the machine crashes about once a week on average (with big variance). i'm still unsure what it is that i should be looking for... the dmesg is NOT self-explanatory :-k ..!! any pointers would be appreciated!!

thanks a lot

---

