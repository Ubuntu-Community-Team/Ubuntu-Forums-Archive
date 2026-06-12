---
title: "corrupt mbr/grub cannot detect HDD"
date: 2010-04-09
forum: General Help
---

### Post by mike596 on 2010-04-09
Hello folks my first thread on ubuntu forums. Ive search google for a while as well as ubuntu forums with not much luck.

   I have a dual boot windows xp/ubuntu64 9.04 rig at home. Ubuntu is installed alongside windows(if i worded that correctly?). well last night i got the infamous error #15. so i popped in the live cd  and messed around with grub. well i changed grubs boot to point to h0,5  which is where ubuntu resides and as you can guess i can not boot. i want to change it back to h0,0 or h0,1 however the hard drive is undetected.

  I tried windows repair console but same thing cannot detect the drive. I pulled the drive out slipped it in my other machine and still same thing. so my question is how can i go about editing the grub menu.lst if i can't mount the drive?:confused:  
  
  Maybe i can just install a new grub/mbr? but i cant figure out hot to mount the drive. 
thank you folks for your time and my applogies if i started a duplicate thread.

---

### Post by mike596 on 2010-04-09
Ill see if g-parted can mount the drive when I get home from work.

---

### Post by oldfred on 2010-04-09
The best way to see what is where and what versions are installed for booting:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by mike596 on 2010-04-09
Thanks for the reply oldfred, i though this thread got burried. ill post back in a couple hours :)

---

### Post by mike596 on 2010-04-10
hrrm so as i suspected nothing

the drive is a sata 80g WD btw


   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


hdb: _________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hdb                                                iso9660    SLAX                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)


==================== hdb: Location of files loaded by Grub: ====================


    .0GB: boot/initrd.gz
    .0GB: boot/vmlinuz
=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file

---

### Post by oldfred on 2010-04-10
Script did not see any drives. Did you use a SLAX live cd to run the script? A couple of days ago I helped someone who used SLAX and it seemed to work but all drives were labeled hda not sda.

Does your BIOS show the drives?

---

### Post by motsteve on 2010-04-10
If you are using a liveCD, I would also like to suggest dropping into a terminal and:

$ sudo fdisk -l

This will show what partitions you have and where.

If you can get a hold of another computer, you may need to download the PMagic 4.9 iso and burn it to a disk and use it as your liveCD.  It has every tool you would need to work on your main drive and it has a gui interface for easy of use.

---

### Post by motsteve on 2010-04-10
If you are using a liveCD, I would also like to suggest dropping into a terminal and:

$ sudo fdisk -l

This will show what partitions you have and where.

If you can get a hold of another computer, you may need to download the PMagic 4.9 iso and burn it to a disk and use it as your liveCD.  It has every tool you would need to work on your main drive and it has a gui interface for ease of use.

---

### Post by oldfred on 2010-04-10
The script actually runs fdisk or sfdisk, blkid and several other tools, probes the MBR and boot sectors (PBR) for bootable systems and did not find anything. Hard drive is missing in action.

---

### Post by mike596 on 2010-04-12
> **oldfred said:**
> Script did not see any drives. Did you use a SLAX live cd to run the script? A couple of days ago I helped someone who used SLAX and it seemed to work but all drives were labeled hda not sda.

Does your BIOS show the drives?

I was using backtrack3 to run the script. I couldn't get ubuntu,puppy, or windows to boot since they couldn't see the drive. I'll have to check if bios detects the drive.

---

### Post by mike596 on 2010-04-13
ok bios is detecting the drive however  gparted seems to think the drive doesn't even exist. I just want my files. ](*,)

k tried to mount with 
sudo mount -t ext3 /dev/sda /mnt/root

then got this which is what i get when booting minus the other 2781 lines

[ 2782.180694] ata1.00: irq_stat 0x40000001
[ 2782.180702] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[ 2782.180704]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2782.180709] ata1.00: status: { DRDY ERR }
[ 2782.180713] ata1.00: error: { UNC }
[ 2782.181791] ata1.00: configured for UDMA/133
[ 2782.181800] ata1: EH complete
[ 2784.044599] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2784.044603] ata1.00: irq_stat 0x40000001
[ 2784.044611] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[ 2784.044613]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2784.044618] ata1.00: status: { DRDY ERR }
[ 2784.044621] ata1.00: error: { UNC }
[ 2784.045711] ata1.00: configured for UDMA/133
[ 2784.045731] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2784.045738] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 2784.045747] Descriptor sense data with sense descriptors (in hex):
[ 2784.045751]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2784.045766]         00 00 00 00 
[ 2784.045772] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 2784.045782] end_request: I/O error, dev sda, sector 0
[ 2784.045791] Buffer I/O error on device sda, logical block 0
[ 2784.045805] Buffer I/O error on device sda, logical block 1
[ 2784.045810] Buffer I/O error on device sda, logical block 2
[ 2784.045816] Buffer I/O error on device sda, logical block 3
[ 2784.045844] ata1: EH complete
[ 2785.908471] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2785.908476] ata1.00: irq_stat 0x40000001
[ 2785.908486] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 2785.908489]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2785.908494] ata1.00: status: { DRDY ERR }
[ 2785.908497] ata1.00: error: { UNC }
[ 2785.911113] ata1.00: configured for UDMA/133
[ 2785.911126] ata1: EH complete
[ 2787.872824] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2787.872832] ata1.00: irq_stat 0x40000001
[ 2787.872843] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 2787.872846]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2787.872851] ata1.00: status: { DRDY ERR }
[ 2787.872855] ata1.00: error: { UNC }
[ 2787.874119] ata1.00: configured for UDMA/133
[ 2787.874145] ata1: EH complete
[ 2789.736181] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2789.736188] ata1.00: irq_stat 0x40000001
[ 2789.736198] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 2789.736200]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2789.736206] ata1.00: status: { DRDY ERR }
[ 2789.736209] ata1.00: error: { UNC }
[ 2789.743382] ata1.00: configured for UDMA/133
[ 2789.743401] ata1: EH complete
[ 2791.608411] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2791.608416] ata1.00: irq_stat 0x40000001
[ 2791.608424] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 2791.608427]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2791.608432] ata1.00: status: { DRDY ERR }
[ 2791.608435] ata1.00: error: { UNC }
[ 2791.615321] ata1.00: configured for UDMA/133
[ 2791.615336] ata1: EH complete
[ 2793.530624] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2793.530629] ata1.00: irq_stat 0x40000001
[ 2793.530637] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 2793.530639]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2793.530644] ata1.00: status: { DRDY ERR }
[ 2793.530647] ata1.00: error: { UNC }
[ 2793.531746] ata1.00: configured for UDMA/133
[ 2793.531755] ata1: EH complete
[ 2795.444935] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2795.444940] ata1.00: irq_stat 0x40000001
[ 2795.444948] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 2795.444950]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2795.444955] ata1.00: status: { DRDY ERR }
[ 2795.444958] ata1.00: error: { UNC }
[ 2795.446053] ata1.00: configured for UDMA/133
[ 2795.446074] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2795.446081] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 2795.446090] Descriptor sense data with sense descriptors (in hex):
[ 2795.446094]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2795.446108]         00 00 00 00 
[ 2795.446115] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 2795.446125] end_request: I/O error, dev sda, sector 0
[ 2795.446133] Buffer I/O error on device sda, logical block 0
[ 2795.446166] ata1: EH complete
[ 2795.446217] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2795.446273] sd 0:0:0:0: [sda] Write Protect is off
[ 2795.446278] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2795.446325] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2795.446384] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2795.446409] sd 0:0:0:0: [sda] Write Protect is off
[ 2795.446413] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2795.446457] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2797.333400] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2797.333405] ata1.00: irq_stat 0x40000001
[ 2797.333415] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[ 2797.333417]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2797.333423] ata1.00: status: { DRDY ERR }
[ 2797.333426] ata1.00: error: { UNC }
[ 2797.334532] ata1.00: configured for UDMA/133
[ 2797.334546] ata1: EH complete
[ 2799.247771] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2799.247776] ata1.00: irq_stat 0x40000001
[ 2799.247783] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[ 2799.247786]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2799.247791] ata1.00: status: { DRDY ERR }
[ 2799.247794] ata1.00: error: { UNC }
[ 2799.250520] ata1.00: configured for UDMA/133
[ 2799.250532] ata1: EH complete
[ 2801.312478] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2801.312487] ata1.00: irq_stat 0x40000001
[ 2801.312499] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[ 2801.312501]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2801.312530] ata1.00: status: { DRDY ERR }
[ 2801.312534] ata1.00: error: { UNC }
[ 2801.315370] ata1.00: configured for UDMA/133
[ 2801.315398] ata1: EH complete
[ 2803.233032] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2803.233036] ata1.00: irq_stat 0x40000001
[ 2803.233040] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[ 2803.233041]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2803.233043] ata1.00: status: { DRDY ERR }
[ 2803.233045] ata1.00: error: { UNC }
[ 2803.234082] ata1.00: configured for UDMA/133
[ 2803.234092] ata1: EH complete
[ 2805.096986] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2805.096995] ata1.00: irq_stat 0x40000001
[ 2805.097006] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[ 2805.097008]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2805.097014] ata1.00: status: { DRDY ERR }
[ 2805.097018] ata1.00: error: { UNC }
[ 2805.098105] ata1.00: configured for UDMA/133
[ 2805.098128] ata1: EH complete
[ 2807.060786] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2807.060797] ata1.00: irq_stat 0x40000001
[ 2807.060810] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[ 2807.060813]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2807.060819] ata1.00: status: { DRDY ERR }
[ 2807.060822] ata1.00: error: { UNC }
[ 2807.061936] ata1.00: configured for UDMA/133
[ 2807.061971] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2807.061979] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 2807.061989] Descriptor sense data with sense descriptors (in hex):
[ 2807.061993]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2807.062007]         00 00 00 00 
[ 2807.062012] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 2807.062024] end_request: I/O error, dev sda, sector 0
[ 2807.062035] Buffer I/O error on device sda, logical block 0
[ 2807.062058] Buffer I/O error on device sda, logical block 1
[ 2807.062064] Buffer I/O error on device sda, logical block 2
[ 2807.062069] Buffer I/O error on device sda, logical block 3
[ 2807.062117] ata1: EH complete
[ 2808.974538] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2808.974547] ata1.00: irq_stat 0x40000001
[ 2808.974559] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 2808.974561]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2808.974568] ata1.00: status: { DRDY ERR }
[ 2808.974571] ata1.00: error: { UNC }
[ 2808.975666] ata1.00: configured for UDMA/133
[ 2808.975692] ata1: EH complete
[ 2810.988219] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2810.988224] ata1.00: irq_stat 0x40000001
[ 2810.988233] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 2810.988236]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2810.988241] ata1.00: status: { DRDY ERR }
[ 2810.988244] ata1.00: error: { UNC }
[ 2810.991119] ata1.00: configured for UDMA/133
[ 2810.991134] ata1: EH complete
[ 2812.852195] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2812.852202] ata1.00: irq_stat 0x40000001
[ 2812.852213] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 2812.852215]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2812.852220] ata1.00: status: { DRDY ERR }
[ 2812.852224] ata1.00: error: { UNC }
[ 2812.855192] ata1.00: configured for UDMA/133
[ 2812.855214] ata1: EH complete
[ 2814.766013] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2814.766024] ata1.00: irq_stat 0x40000001
[ 2814.766035] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 2814.766037]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2814.766043] ata1.00: status: { DRDY ERR }
[ 2814.766047] ata1.00: error: { UNC }
[ 2814.767153] ata1.00: configured for UDMA/133
[ 2814.767177] ata1: EH complete
[ 2816.680414] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2816.680425] ata1.00: irq_stat 0x40000001
[ 2816.680435] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 2816.680438]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2816.680444] ata1.00: status: { DRDY ERR }
[ 2816.680448] ata1.00: error: { UNC }
[ 2816.683346] ata1.00: configured for UDMA/133
[ 2816.683372] ata1: EH complete
[ 2818.543802] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2818.543807] ata1.00: irq_stat 0x40000001
[ 2818.543815] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 2818.543818]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2818.543823] ata1.00: status: { DRDY ERR }
[ 2818.543826] ata1.00: error: { UNC }
[ 2818.546540] ata1.00: configured for UDMA/133
[ 2818.546563] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2818.546570] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 2818.546580] Descriptor sense data with sense descriptors (in hex):
[ 2818.546584]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2818.546600]         00 00 00 00 
[ 2818.546606] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 2818.546616] end_request: I/O error, dev sda, sector 0
[ 2818.546624] Buffer I/O error on device sda, logical block 0
[ 2818.546659] ata1: EH complete
[ 2818.546712] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2818.546948] sd 0:0:0:0: [sda] Write Protect is off
[ 2818.546952] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2818.547000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2818.547060] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 2818.547086] sd 0:0:0:0: [sda] Write Protect is off
[ 2818.547090] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2818.547134] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3111.436612] end_request: I/O error, dev fd0, sector 0
[ 3123.601641] end_request: I/O error, dev fd0, sector 0
[ 3123.601657] Buffer I/O error on device fd0, logical block 0
[ 3135.768328] end_request: I/O error, dev fd0, sector 0
[ 3135.768344] Buffer I/O error on device fd0, logical block 0
[ 3137.691164] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3137.691170] ata1.00: irq_stat 0x40000001
[ 3137.691181] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[ 3137.691184]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 3137.691190] ata1.00: status: { DRDY ERR }
[ 3137.691194] ata1.00: error: { UNC }
[ 3137.692314] ata1.00: configured for UDMA/133
[ 3137.692328] ata1: EH complete
[ 3139.705404] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3139.705414] ata1.00: irq_stat 0x40000001
[ 3139.705425] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[ 3139.705428]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 3139.705434] ata1.00: status: { DRDY ERR }
[ 3139.705438] ata1.00: error: { UNC }
[ 3139.706522] ata1.00: configured for UDMA/133
[ 3139.706548] ata1: EH complete
[ 3141.618188] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3141.618198] ata1.00: irq_stat 0x40000001
[ 3141.618210] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[ 3141.618212]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 3141.618218] ata1.00: status: { DRDY ERR }
[ 3141.618223] ata1.00: error: { UNC }
[ 3141.619307] ata1.00: configured for UDMA/133
[ 3141.619331] ata1: EH complete
[ 3143.482108] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3143.482117] ata1.00: irq_stat 0x40000001
[ 3143.482128] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[ 3143.482131]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 3143.482137] ata1.00: status: { DRDY ERR }
[ 3143.482140] ata1.00: error: { UNC }
[ 3143.483229] ata1.00: configured for UDMA/133
[ 3143.483246] ata1: EH complete
[ 3145.346035] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3145.346046] ata1.00: irq_stat 0x40000001
[ 3145.346057] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[ 3145.346060]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 3145.346066] ata1.00: status: { DRDY ERR }
[ 3145.346069] ata1.00: error: { UNC }
[ 3145.347150] ata1.00: configured for UDMA/133
[ 3145.347175] ata1: EH complete
[ 3147.259878] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3147.259889] ata1.00: irq_stat 0x40000001
[ 3147.259900] ata1.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
[ 3147.259902]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 3147.259909] ata1.00: status: { DRDY ERR }
[ 3147.259913] ata1.00: error: { UNC }
[ 3147.263085] ata1.00: configured for UDMA/133
[ 3147.263107] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3147.263115] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 3147.263124] Descriptor sense data with sense descriptors (in hex):
[ 3147.263128]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 3147.263142]         00 00 00 00 
[ 3147.263148] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 3147.263158] end_request: I/O error, dev sda, sector 0
[ 3147.263166] Buffer I/O error on device sda, logical block 0
[ 3147.263176] Buffer I/O error on device sda, logical block 1
[ 3147.263182] Buffer I/O error on device sda, logical block 2
[ 3147.263188] Buffer I/O error on device sda, logical block 3
[ 3147.263206] ata1: EH complete
[ 3149.174205] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3149.174214] ata1.00: irq_stat 0x40000001
[ 3149.174226] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 3149.174228]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 3149.174234] ata1.00: status: { DRDY ERR }
[ 3149.174237] ata1.00: error: { UNC }
[ 3149.175510] ata1.00: configured for UDMA/133
[ 3149.175527] ata1: EH complete
[ 3151.137984] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3151.137993] ata1.00: irq_stat 0x40000001
[ 3151.138005] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 3151.138007]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 3151.138013] ata1.00: status: { DRDY ERR }
[ 3151.138017] ata1.00: error: { UNC }
[ 3151.139132] ata1.00: configured for UDMA/133
[ 3151.139149] ata1: EH complete
[ 3153.001354] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3153.001362] ata1.00: irq_stat 0x40000001
[ 3153.001374] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 3153.001376]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 3153.001382] ata1.00: status: { DRDY ERR }
[ 3153.001386] ata1.00: error: { UNC }
[ 3153.002496] ata1.00: configured for UDMA/133
[ 3153.002520] ata1: EH complete
[ 3154.915265] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3154.915285] ata1.00: irq_stat 0x40000001
[ 3154.915301] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 3154.915304]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 3154.915310] ata1.00: status: { DRDY ERR }
[ 3154.915314] ata1.00: error: { UNC }
[ 3154.916453] ata1.00: configured for UDMA/133
[ 3154.916540] ata1: EH complete
[ 3156.779126] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3156.779136] ata1.00: irq_stat 0x40000001
[ 3156.779147] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 3156.779150]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 3156.779155] ata1.00: status: { DRDY ERR }
[ 3156.779159] ata1.00: error: { UNC }
[ 3156.780265] ata1.00: configured for UDMA/133
[ 3156.780291] ata1: EH complete
[ 3158.692964] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3158.692974] ata1.00: irq_stat 0x40000001
[ 3158.692985] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 3158.692988]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 3158.692994] ata1.00: status: { DRDY ERR }
[ 3158.692998] ata1.00: error: { UNC }
[ 3158.694119] ata1.00: configured for UDMA/133
[ 3158.694146] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3158.694153] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 3158.694163] Descriptor sense data with sense descriptors (in hex):
[ 3158.694167]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 3158.694181]         00 00 00 00 
[ 3158.694187] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 3158.694198] end_request: I/O error, dev sda, sector 0
[ 3158.694207] Buffer I/O error on device sda, logical block 0
[ 3158.694242] ata1: EH complete
[ 3158.694648] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 3158.694691] sd 0:0:0:0: [sda] Write Protect is off
[ 3158.694695] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3158.694744] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3158.694801] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 3158.694828] sd 0:0:0:0: [sda] Write Protect is off
[ 3158.694832] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3158.694877] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3508.420067] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3508.420077] ata1.00: irq_stat 0x40000001
[ 3508.420088] ata1.00: cmd c8/00:02:02:00:00/00:00:00:00:00/e0 tag 0 dma 1024 in
[ 3508.420091]          res 51/40:00:02:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 3508.420096] ata1.00: status: { DRDY ERR }
[ 3508.420101] ata1.00: error: { UNC }
[ 3508.422658] ata1.00: configured for UDMA/133
[ 3508.422678] ata1: EH complete
[ 3510.341847] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3510.341857] ata1.00: irq_stat 0x40000001
[ 3510.341868] ata1.00: cmd c8/00:02:02:00:00/00:00:00:00:00/e0 tag 0 dma 1024 in
[ 3510.341870]          res 51/40:00:02:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 3510.341876] ata1.00: status: { DRDY ERR }
[ 3510.341880] ata1.00: error: { UNC }
[ 3510.343143] ata1.00: configured for UDMA/133
[ 3510.343167] ata1: EH complete
[ 3512.214069] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3512.214078] ata1.00: irq_stat 0x40000001
[ 3512.214089] ata1.00: cmd c8/00:02:02:00:00/00:00:00:00:00/e0 tag 0 dma 1024 in
[ 3512.214091]          res 51/40:00:02:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 3512.214097] ata1.00: status: { DRDY ERR }
[ 3512.214100] ata1.00: error: { UNC }
[ 3512.215183] ata1.00: configured for UDMA/133
[ 3512.215207] ata1: EH complete
[ 3514.086312] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3514.086321] ata1.00: irq_stat 0x40000001
[ 3514.086331] ata1.00: cmd c8/00:02:02:00:00/00:00:00:00:00/e0 tag 0 dma 1024 in
[ 3514.086333]          res 51/40:00:02:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 3514.086339] ata1.00: status: { DRDY ERR }
[ 3514.086343] ata1.00: error: { UNC }
[ 3514.087427] ata1.00: configured for UDMA/133
[ 3514.087450] ata1: EH complete
[ 3516.008500] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3516.008534] ata1.00: irq_stat 0x40000001
[ 3516.008546] ata1.00: cmd c8/00:02:02:00:00/00:00:00:00:00/e0 tag 0 dma 1024 in
[ 3516.008548]          res 51/40:00:02:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 3516.008554] ata1.00: status: { DRDY ERR }
[ 3516.008558] ata1.00: error: { UNC }
[ 3516.011988] ata1.00: configured for UDMA/133
[ 3516.012014] ata1: EH complete
[ 3517.981608] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ubuntu@ubuntu:~$ ~~~~

---

### Post by prodigy_ on 2010-04-13
If BIOS detects the drive, it might be that motherboard causes the problem, not the drive itself. Either way it's most likely a hardware issue.

If possible, try to attach this drive to a different PC. Maybe there you'll be able to access it.

---

### Post by mike596 on 2010-04-13
and when i try and find stage1


grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found


this worked before I changed (hd0,0) to (hd0,5)

---

