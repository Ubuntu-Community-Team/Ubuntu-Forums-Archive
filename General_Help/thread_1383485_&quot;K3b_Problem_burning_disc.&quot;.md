---
title: "&quot;K3b Problem burning disc.&quot;"
date: 2010-01-17
forum: General Help
---

### Post by LinuXGo on 2010-01-17
Hi, I was trying to burn a disc image to my DVD but the program kept producing errors that refuse to burn the selected image. The most frequent error is about the message the medium having a problem and it can't open a new session. What should I do at this point, is there really a problem with the blank disc? I know that its not corrupted, this disc is still brand new so I have no idea whats the problem.

---

### Post by n0dix on 2010-01-17
Run k3b from console and post the output. You try with other DVD? The unit of DVD is ok?

---

### Post by LinuXGo on 2010-01-17
> **n0dix said:**
> Run k3b from console and post the output. You try with other DVD? The unit of DVD is ok?

 I have no clue about running k3b from a console so could you tell me the steps for me to run the program in a console. The DVD is fine, its just that my computer isn't reacting to the media device, when I insert the disc in the drive, the computer just reads and reads repeatly. Disk Utility had detects the blank DVD but won't create a filesystem for it because its a read-only disc.

---

### Post by n0dix on 2010-01-17
Run 
Gnome Alt+F2, then xterm, then k3b.
KDE, in the normal menu, look for Konsole or Terminal, and write k3b in it.

---

### Post by LinuXGo on 2010-01-17
Devices ----------------------- PIONEER DVD-RW  DVR-K14 1.00 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW) [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite] [%7]  System ----------------------- K3b Version: 1.68.0 KDE Version: 4.3.2 (KDE 4.3.2) QT Version:  4.5.2 Kernel:      2.6.31-18-generic  Used versions ----------------------- cdrecord: 1.1.9  cdrecord ----------------------- scsidev: '/dev/sr0' devname: '/dev/sr0' scsibus: -2 target: -2 lun: -2 Linux sg driver version: 3.5.27 Wodim version: 1.1.9 SCSI buffer size: 64512 Beginning DMA speed test. Set CDR_NODMATEST environment variable if device communication breaks or freezes immediately after that. TOC Type: 1 = CD-ROM Driveropts: 'burnfree' Device type    : Removable CD-ROM Version        : 5 Response Format: 2 Capabilities   :  Vendor_info    : 'PIONEER ' Identification : 'DVD-RW  DVR-K14 ' Revision       : '1.00' Device seems to be: Generic mmc2 DVD-R/DVD-RW. Current: 0x0011 (DVD-R sequential recording) Profile: 0x002B (DVD+R/DL)  Profile: 0x001B (DVD+R)  Profile: 0x001A (DVD+RW)  Profile: 0x0014 (DVD-RW sequential recording)  Profile: 0x0013 (DVD-RW restricted overwrite)  Profile: 0x0011 (DVD-R sequential recording) (current) Profile: 0x0010 (DVD-ROM)  Profile: 0x000A (CD-RW)  Profile: 0x0009 (CD-R)  Profile: 0x0008 (CD-ROM)  Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd). Driver flags   : SWABAUDIO BURNFREE  Supported modes: PACKET SAO Drive buf size : 1605632 = 1568 KB FIFO size      : 12582912 = 12288 KB Speed set to 2770 KB/s Track 01: data  2925 MB         Total size:     3359 MB (332:51.22) = 1497842 sectors Lout start:     3360 MB (332:53/17) = 1497842 sectors Current Secsize: 2048 HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction. Blocks total: 1694450 Blocks current: 1694450 Blocks remaining: 196608 Starting to write CD/DVD at speed   2.0 in real SAO mode for single session. Last chance to quit, starting real write in    2 seconds.    1 seconds.    0 seconds. Operation starts. Waiting for reader process to fill input buffer ... Errno: 5 (Input/output error), reserve track scsi sendcmd: no error CDB:  53 00 00 00 00 00 16 DA F2 00 status: 0x2 (CHECK CONDITION) Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 72 05 00 00 Sense Key: 0x5 Illegal Request, Segment 0 Sense Code: 0x72 Qual 0x05 (no more track reservations allowed) Fru 0x0 Sense flags: Blk 0 (not valid)  cmd finished after 0.005s timeout 200s /usr/bin/wodim: Cannot open new session. input buffer ready. Writing  time:    0.103s /usr/bin/wodim: fifo had 192 puts and 0 gets. /usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.  cdrecord command: ----------------------- /usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=2 -sao driveropts=burnfree -data -tsize=1497842s -

---

### Post by LinuXGo on 2010-01-17
Sorry about the post above, it seemed messy. All because I recently join this forum and I don't know how to navigate the thread.

---

### Post by LinuXGo on 2010-01-17
I've also tried various attempts to nullify the errors that arouse. Such as adding the cdrom group to gain authority and giving the program full root privileges. All of the tried methods are shattered by the swarming errors that rises from the burning procedure.

---

### Post by n0dix on 2010-01-17
You use Gnome or Kde. You try with Brasero?

---

### Post by LinuXGo on 2010-01-17
> **n0dix said:**
> You use Gnome or Kde. You try with Brasero?

  Brasero is even worse, the program can't detect the removable media disc. I already removed the program, and I thought its pretty strange, thinking that it could only detect read/write discs. I'm running GNOME but I'm using a kde application.

---

### Post by LinuXGo on 2010-01-17
> **LinuXGo said:**
> Brasero is even worse, the program can't detect the removable media disc. I already removed the program, and I thought its pretty strange, thinking that it could only detect read/write discs. I'm running GNOME but I'm using a kde application.

 Last time when I'm still running Jaunty, Brasero reacts to the disc being inserted using its application called CD/DVD creator. So my guess is that upgrading to Karmic may've messed things up a bit.

---

### Post by n0dix on 2010-01-17
What about reinstall k3b???

---

### Post by LinuXGo on 2010-01-17
> **n0dix said:**
> What about reinstall k3b???

No it didn't work at all. I've remove the package and install it again but came at the same result. Battering me with the "Cannot open a New Session." "probably a problem with the medium".

---

### Post by LinuXGo on 2010-01-17
[SIZE=3][FONT=Times New Roman]It just occured to me that there's a note located on the back of my DVD case:

Caution:
Use of this disc with certain DVD-R/RW drives or recorders which do not support 16x recording speed many cause writing errors, failures in retrieval of data or damage to the data previously recorded on the disc along with the risk of damaging the drive or recorder. To solve this problem, updating the firmware for your drive is required.

Does that mean that the my DVD drive isn't compatitible with the disc?
[/FONT][/SIZE]

---

### Post by n0dix on 2010-01-17
> **LinuXGo said:**
> [SIZE=3][FONT=Times New Roman]It just occured to me that there's a note located on the back of my DVD case:

Caution:
Use of this disc with certain DVD-R/RW drives or recorders which do not support 16x recording speed many cause writing errors, failures in retrieval of data or damage to the data previously recorded on the disc along with the risk of damaging the drive or recorder. To solve this problem, updating the firmware for your drive is required.

Does that mean that the my DVD drive isn't compatitible with the disc?
[/FONT][/SIZE]

What is the exact specification of your DVD drive? Commonly is in the front of your DVD drive?

---

### Post by LinuXGo on 2010-01-29
Well my DVD Driver is a Pioneer DVD-RW DVR-K14, I'm not sure if you understand my last quote. There's a note on back of my blank DVD jewel case that imprinted that this disc will not be able to run write properly if there's a driver that can't support 16x writing speed. It seem to be true because the reason being is that the maximum K3b can write is 8x. So all I want to ask is that, does all blank DVD have that caution when you're trying to burn it. Like you must have to drive that support 16x or else it won't write properly?

---

### Post by LinuXGo on 2010-03-16
Surely there must be a problem somewhere in the hardware that I'm using but my guess will probably fall on the disc itself since my CD/DVD drive works fine then there'll be no issue involve with the hardware unless some correlated hardware doesn't respond well. I've yet get this problem to work since I'm using a CD that have a vary of writing speed from 1x to 40x. Well anyone respond to this thread would be much appreciated.

---

