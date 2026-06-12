---
title: "K3b Burn Issue"
date: 2011-05-04
forum: General Help
---

### Post by carolina on 2011-05-04
I am new to k3b and trying to burn an iso and get the following message during the burn process .

" cdrecord has no permission to open the device "

Can anyone point me in the right direction ?

Thanks

---

### Post by ivanovnegro on 2011-05-04
Have you inserted the CD in your device to burn?
What do you want to burn, an ISO, data CD, music CD...?

---

### Post by carolina on 2011-05-04
Burning iso image.. burn starts but then stops during the burn process after about 5 % ..

---

### Post by ivanovnegro on 2011-05-04
Maybe the ISO is corrupted. Did you check the md5sum?
It sounds weird anyway.
Did you check the option, burn an ISO and not something else?

---

### Post by carolina on 2011-05-04
> **ivanovnegro said:**
> Maybe the ISO is corrupted. Did you check the md5sum?
It sounds weird anyway.
Did you check the option, burn an ISO and not something else?


The md5sum is correct & i did check to burn iso .  Burn runs , just doesn't complete . File permissions have been changed in places but i assume k3b changed to what it needs in order to burn .   :-)

---

### Post by ivanovnegro on 2011-05-04
So you want to say that you were actually burning the CD but it didnt complete the process, maybe your CD is broken, I mean the blank CD, try it with another.
I think Im not much of help here as it seems I cannot understand the issue, K3b is working fine here.

---

### Post by carolina on 2011-05-05
Enclosed is some data from error report - maybe someone else can make sense of it .. Have tried 3 different cd's so don't think cd's are the problem . Maybe something in permissions but i am not smart enough to know what they should be . Note: Brasero also can not burn .

  	 	 	 	 	p { margin-bottom: 0.21cm; }  [FONT=Monospace][SIZE=2]System[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]-----------------------[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]K3b Version: 2.0.1[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]KDE Version: 4.5.5 (KDE 4.5.5)[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]QT Version: 4.7.0[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]Kernel: 2.6.35-28-generic[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]cdrecord[/SIZE][/FONT]


   	 	 	 	p { margin-bottom: 0.21cm; }  [FONT=Monospace][SIZE=2]/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]scsidev: '/dev/sr0'[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]devname: '/dev/sr0'[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]scsibus: -2 target: -2 lun: -2[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]Linux sg driver version: 3.5.27[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]Wodim version: 1.1.10[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]SCSI buffer size: 64512[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]Beginning DMA speed test. Set CDR_NODMATEST environment variable if device[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]communication breaks or freezes immediately after that.[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]TOC Type: 1 = CD-ROM[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]Driveropts: 'burnfree'[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]Device type : Removable CD-ROM[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]Version : 5[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]Response Format: 2[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]Capabilities : [/SIZE][/FONT] 
 [FONT=Monospace][SIZE=2]Vendor_info : 'HL-DT-ST'[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]Identification : 'DVD-RAM GSA-H55N'[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]Revision : '1.06'[/SIZE][/FONT]
   	 	 	 	 	p { margin-bottom: 0.21cm; }  [FONT=Monospace][SIZE=2]Track 01: 50 of 693 MB written (fifo 100%) [buf 91%] 16.7x.[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]Track 01: 51 of 693 MB written (fifo 100%) [buf 91%] 16.2x.[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]**Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error**[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]**CDB: 2A 00 00 00 67 E6 00 00 1F 00**[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]**status: 0x2 (CHECK CONDITION)**[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]**Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 09 00 00 00**[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]**Sense Key: 0x4 Hardware Error, Segment 0**[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]**Sense Code: 0x09 Qual 0x00 (track following error) Fru 0x0**[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]**Sense flags: Blk 0 (not valid) **[/SIZE][/FONT] 
 [FONT=Monospace][SIZE=2]**cmd finished after 3.560s timeout 200s**[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]**/usr/bin/wodim: A write error occured.**[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]**/usr/bin/wodim: Please properly read the error message above.**[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]write track data: error after 54472704 bytes[/SIZE][/FONT]


[FONT=Monospace][SIZE=2]Any chance this could be an indication of a bad cd/dvd softwear ?
[/SIZE][/FONT]
 [FONT=Monospace][SIZE=2]
[/SIZE][/FONT]

---

### Post by ivanovnegro on 2011-05-05
Hm, I see here also a hardware error, that could indicate that the CD drive is broken.
Hope to see more opinions on your problem from others.

---

