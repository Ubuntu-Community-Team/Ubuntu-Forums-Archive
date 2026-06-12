---
title: "Slow startup"
date: 2010-05-09
forum: General Help
---

### Post by padnoter on 2010-05-09
Hi,
Just upgrade to 10.04LTS and my bootup time is slow, it pauses for about a minute after grub, while displaying "Starting up ..." on the screen.
Having browsed the forums, I installed bootchart and include the picture from it... the pause seems to be to do with async/2 3 4 5 maybe? and I have seen other posts about older CD drives causing problems - but not a solution (other than unplugging).

Can someone have a look at the pictures (I've tried to gimp some of them for the size restriction - I hope it's clear!) and see if they agree?

It shows,
0 - 70seconds
kthreadd
khelper
kseriod
scsi_eh_1
async/2
async/3
async/4
async/5
- all in parallel (the only things running), at 70seconds all the async/2-3-4-5 end, and then all the other bootup processes start & complete by 95seconds total... so it seems the async/2/3/4/5 are causing the 70second bootup delay.... do you agree? and any solutions please?


Is there a way to disable drives without unplugging them for bootup (if you think this may be the problem)?

btw I don't have any drives plugged into USB.

Thanks
pn

---

### Post by Interruptor on 2010-07-30
I'm having the same problem, **but** only if I plug-in one old HDD ([ST360021A]("http://www.seagate.com/support/disc/ata/st360021a.html")).
> kthreadd
khelper
kseriod
async/0
async/3
are waiting 125 seconds before letting other processes in.
Without that HDD everything was fine.

-------
UPD 1:
```
$ sudo smartctl --all /dev/sdb
**...**
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   071   065   034    Pre-fail  Always       -       27409093
  3 Spin_Up_Time            0x0003   070   070   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       489
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   084   060   030    Pre-fail  Always       -       274547420
  9 **Power_On_Hours**          0x0032   089   089   000    Old_age   Always       -       **10162**
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   097   097   020    Old_age   Always       -       3631
194 Temperature_Celsius     0x0022   048   062   000    Old_age   Always       -       48
195 Hardware_ECC_Recovered  0x001a   071   065   000    Old_age   Always       -       27409093
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   164   000    Old_age   Always       -       108
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0
**...**
ATA Error Count: 488
**...**
Error **488** occurred at disk power-on lifetime: **9253 hours** (385 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 f0  Error: ICRC, ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 03 01 00 00 00 f0 00      00:00:13.901  READ DMA
  ef 03 45 01 00 02 b0 00      00:00:13.899  SET FEATURES [Set transfer mode]
  ef 03 0c 01 00 02 b0 00      00:00:13.899  SET FEATURES [Set transfer mode]
  c6 95 30 01 00 02 b0 00      00:00:13.710  SET MULTIPLE MODE
  ef 95 45 01 00 02 b0 00      00:00:13.567  SET FEATURES [Enable Media Status Notf]
**...**
Error **487** occurred at disk power-on lifetime: **7757 hours** (323 days + 5 hours)
**...**

```
Is it dying or not?
-------
UPD 2:
**syslog**:
```
Jul 31 00:44:07 home kernel: [    0.893696] sd 1:0:0:0: [sdb] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
Jul 31 00:44:07 home kernel: [    0.893760] sd 1:0:0:0: [sdb] Write Protect is off
Jul 31 00:44:07 home kernel: [    0.893765] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Jul 31 00:44:07 home kernel: [    0.893798] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 31 00:44:07 home kernel: [    0.893989]  sdb: sda1 sda2 < sda5 sda6 sda7 > sda3
Jul 31 00:44:07 home kernel: [    0.939071] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 31 00:44:07 home kernel: [   31.816022] ata2: lost interrupt (Status 0x58)
Jul 31 00:44:07 home kernel: [   31.820003] ata2: drained 32768 bytes to clear DRQ.
Jul 31 00:44:07 home kernel: [   31.882635] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jul 31 00:44:07 home kernel: [   31.882641] ata2.00: failed command: READ DMA
Jul 31 00:44:07 home kernel: [   31.882650] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
Jul 31 00:44:07 home kernel: [   31.882652]          res 40/00:02:00:24:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Jul 31 00:44:07 home avahi-daemon[699]: Successfully called chroot().
Jul 31 00:44:07 home avahi-daemon[699]: Successfully dropped remaining capabilities.
Jul 31 00:44:07 home kernel: [   31.882656] ata2.00: status: { DRDY }
Jul 31 00:44:07 home kernel: [   31.882689] ata2: soft resetting link
Jul 31 00:44:07 home kernel: [   32.060331] ata2.00: configured for UDMA/100
Jul 31 00:44:07 home kernel: [   32.076233] ata2.01: configured for UDMA/33
Jul 31 00:44:07 home kernel: [   32.076474] ata2.00: device reported invalid CHS sector 0
Jul 31 00:44:07 home kernel: [   32.076483] ata2: EH complete
Jul 31 00:44:07 home kernel: [   62.816017] ata2: lost interrupt (Status 0x58)
Jul 31 00:44:07 home kernel: [   62.820003] ata2: drained 32768 bytes to clear DRQ.
Jul 31 00:44:07 home kernel: [   62.882616] ata2.00: limiting speed to UDMA/66:PIO4
Jul 31 00:44:07 home kernel: [   62.882621] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jul 31 00:44:07 home kernel: [   62.882626] ata2.00: failed command: READ DMA
Jul 31 00:44:07 home kernel: [   62.882634] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
Jul 31 00:44:07 home kernel: [   62.882635]          res 40/00:02:00:24:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Jul 31 00:44:07 home kernel: [   62.882639] ata2.00: status: { DRDY }
Jul 31 00:44:07 home kernel: [   62.882664] ata2: soft resetting link
Jul 31 00:44:07 home kernel: [   63.068331] ata2.00: configured for UDMA/66
Jul 31 00:44:07 home kernel: [   63.084233] ata2.01: configured for UDMA/33
Jul 31 00:44:07 home kernel: [   63.084611] ata2.00: device reported invalid CHS sector 0
Jul 31 00:44:07 home kernel: [   63.084618] ata2: EH complete
Jul 31 00:44:07 home kernel: [   93.816016] ata2: lost interrupt (Status 0x58)
Jul 31 00:44:07 home kernel: [   93.820003] ata2: drained 32768 bytes to clear DRQ.
Jul 31 00:44:07 home kernel: [   93.882616] ata2.00: limiting speed to UDMA/33:PIO4
Jul 31 00:44:07 home kernel: [   93.882621] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jul 31 00:44:07 home kernel: [   93.882625] ata2.00: failed command: READ DMA
Jul 31 00:44:07 home kernel: [   93.882633] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
Jul 31 00:44:07 home kernel: [   93.882635]          res 40/00:02:00:24:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Jul 31 00:44:07 home kernel: [   93.882639] ata2.00: status: { DRDY }
Jul 31 00:44:07 home kernel: [   93.882664] ata2: soft resetting link
Jul 31 00:44:07 home kernel: [   94.068335] ata2.00: configured for UDMA/33
Jul 31 00:44:07 home kernel: [   94.084233] ata2.01: configured for UDMA/33
Jul 31 00:44:07 home kernel: [   94.084472] ata2.00: device reported invalid CHS sector 0
Jul 31 00:44:07 home kernel: [   94.084478] ata2: EH complete
Jul 31 00:44:07 home kernel: [  124.816016] ata2: lost interrupt (Status 0x58)
Jul 31 00:44:07 home kernel: [  124.820003] ata2: drained 32768 bytes to clear DRQ.
Jul 31 00:44:07 home kernel: [  124.882615] ata2.00: limiting speed to PIO4
Jul 31 00:44:07 home kernel: [  124.882620] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jul 31 00:44:07 home kernel: [  124.882624] ata2.00: failed command: READ DMA
Jul 31 00:44:07 home kernel: [  124.882633] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
Jul 31 00:44:07 home kernel: [  124.882635]          res 40/00:02:00:24:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Jul 31 00:44:07 home kernel: [  124.882639] ata2.00: status: { DRDY }
Jul 31 00:44:07 home kernel: [  124.882664] ata2: soft resetting link
Jul 31 00:44:07 home kernel: [  125.068334] ata2.00: configured for PIO4
Jul 31 00:44:07 home kernel: [  125.084233] ata2.01: configured for UDMA/33
Jul 31 00:44:07 home kernel: [  125.084462] ata2.00: device reported invalid CHS sector 0
Jul 31 00:44:07 home kernel: [  125.084468] ata2: EH complete
Jul 31 00:44:07 home kernel: [  125.102855]  sdb1 sdb2 sdb3 <
```
:-s   :-k

---

### Post by Interruptor on 2010-07-30
<strike out>[COLOR="Silver"]**[SIZE="3"]Incorrect jumper configuration[/SIZE]** was the reason of slow boot.
Now boot time is ~50s.[/COLOR]</strike out>

**Wait. Now I can't see it at all.**

And syslog DMA errors are caused by **broken 21st pin** - DMARQ.
(pins description was found in that [HDD Manual]("http://www.seagate.com/support/disc/manuals/ata/100129212b.pdf") on page 34)
It was definitely broken by previous owner during improper installation attempt - IDE cable has fool-tolerance closing right in that place if cable was turned upside-down.

---

### Post by padnoter on 2010-07-31
Hi,
I can confirm my slow startup was due to an old hard disk in the system  that had died (no power on).... hadn't noticed it before as the main  RAID drives were good, and this one was just for archive material. Took  the lid off to try removing CD drives and remembered it... LOL :o.
So my 10.04 is all fine now..
thanks

---

