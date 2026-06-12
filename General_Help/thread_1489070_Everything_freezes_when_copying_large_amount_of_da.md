---
title: "Everything freezes when copying large amount of data"
date: 2010-05-20
forum: General Help
---

### Post by ZequeZ on 2010-05-20
Well, when I copy large amount of data the other applications than Nautilus freezes until the copy is done...

So, what can I do? Because when backuping some data this is really annoying =/

---

### Post by uOpt on 2010-05-20
> **ZequeZ said:**
> Well, when I copy large amount of data the other applications than Nautilus freezes until the copy is done...

So, what can I do? Because when backuping some data this is really annoying =/

Please post a snapshot of your `top` output while this is going on.

What harddrive, harddrive controller and kernel version are you using?

---

### Post by ryan858 on 2010-05-20
I have a similar problem, but it's not just nautilus, the whole damn system locks up. Takes 10 minutes to open a terminal, and so on. It also takes twice as long (or more) to copy a 400mb file than on any other OS. I've been doing research on this and I think it's down to a bug, either in the kernel or in Ubuntu. I didn't have this issue back in 9.04. Though come to think of it, this is the only kernel I have past 2.6.29*. it's 2.6.32-22. Later versions either do not fix the problem, or make it worse. I have tried 2.6.34-999-generic and no luck with this bug.

I will upgrade my kernel in Slackware and see what happens...

---

### Post by ZequeZ on 2010-05-20
> **uOpt said:**
> Please post a snapshot of your `top` output while this is going on.

What harddrive, harddrive controller and kernel version are you using?

What do you mean with a my "top" output?

The kernel is 2.6.32-22-generic
The harddrive is:
```

       *-disk
                description: ATA Disk
                product: WDC WD2500AAJS-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 12.0
                serial: WD-WCASF0090339
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=39143914
```

And the harddrive controller is "sata_via" (is that lsmod throws =S)
And "modinfo sata_via" throws this:


```

zequez@zequez-desktop:~$ modinfo sata_via
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/ata/sata_via.ko
version:        2.4
license:        GPL
description:    SCSI low-level driver for VIA SATA controllers
author:         Jeff Garzik
srcversion:     F697321C1B688D213D9CEA3
alias:          pci:v00001106d00009000sv*sd*bc*sc*i*
alias:          pci:v00001106d00005287sv*sd*bc*sc*i*
alias:          pci:v00001106d00007372sv*sd*bc*sc*i*
alias:          pci:v00001106d00005372sv*sd*bc*sc*i*
alias:          pci:v00001106d00003249sv*sd*bc*sc*i*
alias:          pci:v00001106d00003149sv*sd*bc*sc*i*
alias:          pci:v00001106d00000591sv*sd*bc*sc*i*
alias:          pci:v00001106d00005337sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.32-22-generic SMP mod_unload modversions 

```

---

### Post by alienvenom on 2010-06-20
I had this very same issue playing back a movie from my file server. One of the hard drives was hooked up to a very cheap 2 Port Serial ATA "RAID" card that uses the sata_via kernel module.

I believe this to be a bug in the sata_via module and have effectively solved it using a different card that does not use the sata_via module.

---

### Post by megamandos on 2010-06-20
I have noticed that when copying large files to/from an NTFS partition the whole computer freezes every 600MB or so for about 3-7 seconds. I believe this to be a bug in the NTFS code. Its normal, just dont be copying gigantic files all over for no reason lol. I solved this issue by just having the large files i need on my Ext4 partitions. Also, if windows compatibility is an issue you could try making a FAT32 partition to store your large files on, since it doesn't suffer from the same issue.

GL, and I hope that helped.

---

### Post by technocp on 2010-06-20
start a similar copy go to terminal issue a command called top
copy and paste the result here it will be easy for people to guide you

---

