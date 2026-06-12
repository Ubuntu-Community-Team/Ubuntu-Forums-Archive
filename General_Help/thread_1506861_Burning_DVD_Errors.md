---
title: "Burning DVD Errors"
date: 2010-06-10
forum: General Help
---

### Post by igorcherfas on 2010-06-10
Hi, 

I'm having trouble burning a DVD via command line or Brasero. The DVD Burner is the only IDE Device in the system. Although Disk Utility seems to display it as SCISI. Originally Ubuntu would only see the drive but do nothing when a DVD is inserted it. atleast recognizes the DVD now. 

**LSHW:**
```

      *-ide:0
             description: IDE interface
             product: MCP55 IDE
             vendor: nVidia Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             logical name: scsi0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ec00(size=16)
           *-cdrom
                description: DVD-RAM writer
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: status=open
        *-ide:1


```**Disk Utility:**
```
[B]
Model:[/B] ATAPI DVD A DH20A3P
**Firmware Version:** XY13
**Location: **Port1 of PATA Host Adapter
**Device:** /dev/sr0
**Connection:** SCISI

```**Terminal**:
```

igor@igor-desktop:~/Shared$ growisofs -dvd-compat -Z /dev/sr0=bie764210.iso 
:-( unable to INQUIRY: Input/output error

```[B]Last few lines of Brasero Log:
[/B]```
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   717258752/3530555392 (20.3%) @0.0x, remaining 10:00 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: :-( unable to WRITE@LBA=55810h: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stderr: /dev/sr0: flushing cache
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: :-( unable to FLUSH CACHE: Input/output error
BraseroGrowisofs stderr: :-( unable to SYNCHRONOUS FLUSH CACHE: Input/output error
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 5
B
```I appreciate the help in advance. 
Thank You,
Igor

---

### Post by fadey on 2010-06-17
Same problem here. Today I wanted to burn a dvd and growisofs has responded with:

:-( unable to INQUIRY: Input/output error

So, I kept on looking at what was going on and discovered the same symtoms as mentioned above.

Please, help

---

