---
title: "Hardware RAID very slow"
date: 2010-05-02
forum: General Help
---

### Post by leopardb on 2010-05-02
Hi,

As the title says, my raid system is very very slow (this is for raid5 6x1Tb SAMSUNG HD103UJ):
```

    leo@server:~$ sudo hdparm -tT /dev/sdb

    /dev/sdb:
     Timing cached reads:   1094 MB in  2.00 seconds = 546.79 MB/sec
     Timing buffered disk reads:    8 MB in  3.16 seconds =   2.53 MB/sec
```It's impossible and i've tried every configuration (raid5,raid0,Pass Through), and i become nearly exactly the same speed (with restarts, so i'm sure i'm really talking with the volumes i've defined).

One can compare it with the system drive :

    ```
leo@server:~$ sudo hdparm -tT /dev/sda

    /dev/sda:
     Timing cached reads:   1756 MB in  2.00 seconds = 878.12 MB/sec
     Timing buffered disk reads:  226 MB in  3.01 seconds =  75.14 MB/sec
```Some hardware/software infos :

```
Raid card
    Controller Name     ARC-1230
    Firmware Version     V1.48 2009-12-31
``````
Motherboard
    Manufacturer: ASUSTeK Computer INC.
    Product Name: P5LD2-VM DH
``````
leo@server:~$ uname -a
Linux server 2.6.31-20-server #58-Ubuntu SMP Fri Mar 12 05:40:05 UTC 2010 x86_64 GNU/Linux
``````
IDE Channels

Channel     Usage     Capacity     Model
Ch01     HD103UJ     1000.2GB     SAMSUNG HD103UJ
Ch02     HD103UJ     1000.2GB     SAMSUNG HD103UJ
Ch03     HD103UJ     1000.2GB     SAMSUNG HD103UJ
Ch04     Pass Through     1000.2GB     ST31000340AS
Ch05     Free         1000.2GB     ST31000340AS
Ch06     Free         1000.2GB     ST31000340AS
Ch07     Raid Set test     1000.2GB     SAMSUNG HD103UJ
Ch08     Raid Set test     1000.2GB     SAMSUNG HD103UJ
Ch09     Raid Set test     1000.2GB     SAMSUNG HD103UJ
Ch10     Raid Set test     1000.2GB     SAMSUNG HD103UJ
Ch11     Raid Set test     1000.2GB     SAMSUNG HD103UJ
Ch12     Raid Set test     1000.2GB     SAMSUNG HD103UJ 
```I'm a bit lost now. I could change the motherboard, or some bios settings. I'd be very thankful for any push in the right direction. Thanks a lot to all helpers !

---

### Post by leopardb on 2010-05-03
I know the key to solve linux problems is to know the diagnostic tools. Could anybody help with that ? what should i check/run ?

By the way, i tried to see if there's any incompatibility between this mainboard and the raid card, and i didn't find anything. And i didn't find anything in the log files.

Please, help :sad:

---

### Post by tgalati4 on 2010-05-03
I presume the system drive is also a similar Samsung 1TB drive?  So what you are saying is that a single drive without RAID is getting 77 MB/sec throughput (which is normal) but any RAID configuration is only getting 8 MB/sec?

I would first look through dmesg for errors:

dmesg | grep error
dmesg | more

Page through the entire dmesg file and make note of any strange or unclear entries.

I presume you did a google search on the ARC controller?  Is this part of the ASUS motherboard or an add-in card?

Is there a RAID BIOS that you can boot into (with Control-S or some other boot up key command)?  How old is the controller?  Can it handle 1TB drives?  Do you have smaller drives to test with?

---

### Post by leopardb on 2010-05-04
Thanks for your answer.

> **tgalati4 said:**
> I presume the system drive is also a similar Samsung 1TB drive? So what you are saying is that a single drive without RAID is getting 77 MB/sec throughput (which is normal) but any RAID configuration is only getting 8 MB/sec?

No actually the system drive is a Seagate ST3400620NS. So a single drive, directly attached to the mainboard,  is getting 75.14 MB/sec and anything that goes trough the Areca ARC-1230 card gets 2.53 MB/sec (whatever raid0, raid5 or pass through, meaning direct access).

> **tgalati4 said:**
> I would first look through dmesg for errors:

dmesg | grep error
dmesg | more

Page through the entire dmesg file and make note of any strange or unclear entries.

I found an error but this has to do with a network card :
[    1.692517] e1000e 0000:02:00.0: pci_enable_pcie_error_reporting failed 0xfffffffb

Here is my dmesg :
[http://pastebin.com/eXwuziY5](http://pastebin.com/eXwuziY5)

> **tgalati4 said:**
> I presume you did a google search on the ARC controller? Is this part of the ASUS motherboard or an add-in card?

Is there a RAID BIOS that you can boot into (with Control-S or some other boot up key command)? How old is the controller? Can it handle 1TB drives? Do you have smaller drives to test with?

The Areca ARC-1230 is a pretty mainstream PCI-e raid card, all the settings are available through a web interface (and there is also a boot up key command). Something i didn't mention is that the same machine used to run on windows, and the performance was absolutely normal.

---

### Post by tgalati4 on 2010-05-04
I presume that you had to load Windows drivers for the ARC card provided by Areca to get Windows to recognize it.  I also presume that Areca has not released any specs for the card or any linux drivers for it.

Your dmesg has some troubling entries:

At 1.3 seconds from boot:

#
   1.310685]  sda:
#
[    1.327166] irq 18: nobody cared (try booting with the "irqpoll" option)
#
[    1.327171] Pid: 0, comm: swapper Not tainted 2.6.31-20-server #58-Ubuntu
#
[    1.327174] Call Trace:
#
[    1.327177]  <IRQ>  [<ffffffff810b4ba6>] __report_bad_irq+0x26/0xa0
#
[    1.327192]  [<ffffffff810b4dac>] note_interrupt+0x18c/0x1d0
#
[    1.327199]  [<ffffffff81081b17>] ? getnstimeofday+0x57/0xe0
#
[    1.327204]  [<ffffffff810b5425>] handle_fasteoi_irq+0xd5/0x100
#
[    1.327210]  [<ffffffff81014c5d>] handle_irq+0x1d/0x30
#
[    1.327214]  [<ffffffff81014137>] do_IRQ+0x67/0xe0
#
[    1.327221]  [<ffffffff81012a53>] ret_from_intr+0x0/0x11
#
[    1.327223]  <EOI>  [<ffffffff81086fda>] ? tick_nohz_stop_sched_tick+0x6a/0x3a0
#
[    1.327237]  [<ffffffff81010e02>] ? cpu_idle+0x72/0x100
#
[    1.327243]  [<ffffffff81515ab6>] ? rest_init+0x66/0x70
#
[    1.327250]  [<ffffffff8183c039>] ? start_kernel+0x352/0x35b
#
[    1.327255]  [<ffffffff8183b59a>] ? x86_64_start_reservations+0x125/0x129
#
[    1.327260]  [<ffffffff8183b698>] ? x86_64_start_kernel+0xfa/0x109
#
[    1.327263] handlers:

So something is amiss when you have Call Traces--those are mini-crashes of the kernel during boot.  Linux will try to ignore them and press on.  The user needs to be aware that such operation may not be stable.  There is some reference to 64-bit.

At 1.7 seconds your Areca card is recognized:

#
[    1.764944] ARECA RAID ADAPTER6: FIRMWARE VERSION V1.48 2009-12-31
#
[    1.803230]   alloc irq_desc for 21 on node 0
#
[    1.803236]   alloc kstat_irqs on node 0
#
[    1.803256] e1000 0000:01:09.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
#
[    1.803584] scsi6 : Areca SATA Host Adapter RAID Controller( RAID6 capable)
#
[    1.803586]  Driver Version 1.20.00.15 2008/02/27
#
[    1.813353] scsi 6:0:0:0: Direct-Access     Areca    library          R001 PQ: 0 ANSI: 5
#
[    1.815120] scsi 6:0:0:1: Direct-Access     Areca    HD103UJ          R001 PQ: 0 ANSI: 5
#
[    1.815238] scsi 6:0:0:2: Direct-Access     Seagate  ST31000340AS     R001 PQ: 0 ANSI: 5

Your drives are enumerated, so this is a good sign.  The previous error though means you should try the 32-bit distro because I have a suspicion that your RAID and/or motherboard has an issue with 64-bit.  The slow speeds could be a result of some compatibility mode from 64-bit to 32-bit.

If you want to stick to 64-bit, try Karmic or Jaunty or Hardy.  There may be regressions with the new kernel and you need your hardware to work first before fighting new distro bugs.

---

### Post by The Real Dave on 2010-05-04
Could you try a software RAID with [mdadm]("http://ubuntuforums.org/showthread.php?t=408461")?

---

### Post by leopardb on 2010-05-05
Thx for your answers !

@tgalati4 : well, this raid card is very well supported through the Areca-developped driver arcmsr (and this driver is bundled in all recent kernels). As of 64 bits, it was actually karmic, but in the meantime i upgraded to lucid to try and see if it would solve anything, and it didn't. But i think you're right with the 64 bit problem, that was also my conclusion and i'm going to replace the motherboard with a more recent one. I'll post then the results here.

@The Real Dave: it's a real hardware raid card, that would be a shame to use it with software raid. Also, because the processor on this motherboard is not the most recent one, software raid wouldn't be as transparent on it as with the new quad-cores of today. And last but not least, i would have to use all disk on the card as pass-through and then group them with mdadm, but each individual disk would then have a 2MB/s transfer rate, so with a software raid0 i would probably achieve an impressive 13,5 MB/s, welcome to 1990 ! and if you think that i could just dump the card whatsoever, i have clearly not enough sata ports on this motherboard for 12 disks.

---

### Post by leopardb on 2010-05-08
So i solved the problem by changing the motherboard. It seems that was some kind of incompatibility.

Now i've got those results :

```
/dev/sdb:
 Timing cached reads:   1262 MB in  2.00 seconds = 630.33 MB/sec
 Timing buffered disk reads:  966 MB in  3.01 seconds = 321.41 MB/sec
```

That's a little bit faster ;)

---

