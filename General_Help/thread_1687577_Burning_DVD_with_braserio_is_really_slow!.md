---
title: "Burning DVD with braserio is really slow!"
date: 2011-02-14
forum: General Help
---

### Post by fbonsignori on 2011-02-14
I use Brasero 2.32.0 to burn DVD's and the max speed I reach writing on my 16x DVD's is 2.5x (more or less).

Follows info's about my OS and HW setup:

[COLOR=Blue]$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

$ cat /proc/version
Linux version 2.6.35-25-generic (buildd@crested) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011

$ dmesg
...
[    5.116842] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.119538] ata2.00: ATAPI: PIONEER BD-ROM  BDC-TD03, 1.00, max UDMA/100
[    5.122559] ata2.00: configured for UDMA/100
[    5.141953] scsi 1:0:0:0: CD-ROM            PIONEER  BD-ROM  BDC-TD03 1.00 PQ: 0 ANSI: 5
[    5.178280] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.178286] Uniform CD-ROM driver Revision: 3.20
[    5.178444] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.178530] sr 1:0:0:0: Attached scsi generic sg1 type 5
...[/COLOR]
 
Any idea about?

Thanks in advance for any suggestion.

---

### Post by aaryansh on 2011-02-14
Hey there,
16x is the speed supported by your disk not your drive.
PIONEER BDC-TD03 has a max speed of 8x for dvd writing.[i think]

Try this to be sure about your drive speed.

```
wodim dev=/dev/sr0 -prcap
```

but 2.5x is still low.
have you tried changing the write speeds in brasero, if yes.
You may consider using some other apps, like K3B or GnomeBaker.

---

### Post by fbonsignori on 2011-02-14
> **aaryansh said:**
> Hey there,
16x is the speed supported by your disk not your drive.
PIONEER BDC-TD03 has a max speed of 8x for dvd writing.[i think]

You are right! wodim output is

[COLOR=Blue]...
  Maximum read  speed: 11080 kB/s (CD  62x, DVD  8x)
  Current read  speed: 11080 kB/s (CD  62x, DVD  8x)
  Maximum write speed: 11080 kB/s (CD  62x, DVD  8x)
  Current write speed: 11080 kB/s (CD  62x, DVD  8x)
  Rotational control selected: CLV/PCAV
  Buffer size in KB: 4000
  Copy management revision supported: 1
  Number of supported write speeds: 7
  Write speed # 0: 11080 kB/s CLV/PCAV (CD  62x, DVD  8x)
  Write speed # 1:  8310 kB/s CLV/PCAV (CD  47x, DVD  6x)
  Write speed # 2:  6925 kB/s CLV/PCAV (CD  39x, DVD  5x)
  Write speed # 3:  5540 kB/s CLV/PCAV (CD  31x, DVD  4x)
  Write speed # 4:  4155 kB/s CLV/PCAV (CD  23x, DVD  3x)
  Write speed # 5:  2770 kB/s CLV/PCAV (CD  15x, DVD  2x)
  Write speed # 6:  1385 kB/s CLV/PCAV (CD   7x, DVD  1x)
...

[/COLOR]> but 2.5x is still low.
have you tried changing the write speeds in brasero, if yes.
You may consider using some other apps, like K3B or GnomeBaker.

Doing more tests I noticed that speed raises to 4 and more if an image is prepared before. It seems a buffering issue ...

This is the execution of hdparm  result

[COLOR=Blue]$ hdparm -i /dev/sr0

/dev/sr0:
 HDIO_DRIVE_CMD(identify) failed: Bad address

 Model=PIONEER BD-ROM  BDC-TD03, FwRev=1.00, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode

[/COLOR]Question: buffer size printed out by hdparm and wodim are referring to the same buffer?

---

### Post by aaryansh on 2011-02-14
The wodim and hdparm output should give the same buffer size.
that is the buffer of your dvd drive.
I think the wodim output is pretty accurate, you have 4mb buffer [pretty sweet, i have 2mb].

I also don't think that it is a buffer problem,
cause buffer problems usually result in buffer underrun error.

Try this.

sudo hdparm -tT /dev/sr0

have you tried using an app other brasero,
maybe that could help.

---

### Post by fbonsignori on 2011-02-14
> **aaryansh said:**
> The wodim and hdparm output should give the same buffer size.
that is the buffer of your dvd drive.
I think the wodim output is pretty accurate, you have 4mb buffer [pretty sweet, i have 2mb].

I also don't think that it is a buffer problem,
cause buffer problems usually result in buffer underrun error.

Try this.

sudo hdparm -tT /dev/sr0

[COLOR=Blue]$ sudo hdparm -tT /dev/sr0 

/dev/sr0:
 Timing cached reads:   9098 MB in  2.00 seconds = 4551.90 MB/sec
 Timing buffered disk reads:    8 MB in  3.12 seconds =   2.56 MB/sec

[/COLOR] 
> have you tried using an app other brasero,
maybe that could help.

Made a test using GnomeBaker: 4.5x is the resulting speed, comparable to that obtained using Braseiro burning a prepared image.

---

### Post by aaryansh on 2011-02-14
OK. Here are some things you can try.

*enable 32-bit mode

```
hdparm -c1 /dev/sr0
```

*enable dma and switch between some modes.
As we already know, the drive supports a max of 8x[dvd speed]
so you should be okay with all udma modes and mdma1 and mdma2,

```
hdparm -d1 -Xmdma2 /dev/sr0
```

if mdma2 does not work,
try udma instead.

I really can't think of anything else man.
hope this solves your problem.

---

### Post by fbonsignori on 2011-02-15
> **aaryansh said:**
> OK. Here are some things you can try.

*enable 32-bit mode

```
hdparm -c1 /dev/sr0
```*enable dma and switch between some modes.
As we already know, the drive supports a max of 8x[dvd speed]
so you should be okay with all udma modes and mdma1 and mdma2,

```
hdparm -d1 -Xmdma2 /dev/sr0
```if mdma2 does not work,
try udma instead.
[COLOR=Black]
Follows the output I get using commands you suggested me
  
[/COLOR][COLOR=Blue]$ sudo hdparm -c1 /dev/sr0
  
/dev/sr0:
 setting 32-bit IO_support flag to 1
 IO_support    =  1 (32-bit)
  
$ sudo hdparm -d1 -Xmdma2 /dev/sr0
  
/dev/sr0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 setting xfermode to 34 (multiword DMA mode2)
 HDIO_DRIVE_CMD(setxfermode) failed: Invalid exchange
 HDIO_GET_DMA failed: Inappropriate ioctl for device
[/COLOR]
Same result for other transfer mode setting.

> **aaryansh said:**
> I really can't think of anything else man.
hope this solves your problem.

Thanks a lot for your help, I will continue looking for ...

---

