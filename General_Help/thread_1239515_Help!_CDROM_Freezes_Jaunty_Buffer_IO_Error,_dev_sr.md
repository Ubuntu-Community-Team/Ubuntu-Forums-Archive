---
title: "Help! CDROM Freezes Jaunty Buffer I/O Error, dev sr0"
date: 2009-08-13
forum: General Help
---

### Post by FireflyCalvin on 2009-08-13
Just last night I updated my system using the Update Manager so I didn't pay attention to exactly what was being upgraded since I never had an issue before.

Today I try to put in a CD to the CDROM and the system froze completely. When I rebooted with the CD in the drive and the system again froze just after the login prompt.

While booting with the CD in the CDROM I noticed this information I pulled from the kernel.log file:

```

Aug 13 09:44:07 WickedZippy kernel: [   57.470612] Buffer I/O error on device sr0, logical block 149990
Aug 13 09:44:07 WickedZippy kernel: [   59.877361] end_request: I/O error, dev sr0, sector 1199920
Aug 13 09:44:07 WickedZippy kernel: [   59.877422] Buffer I/O error on device sr0, logical block 149990
Aug 13 09:44:07 WickedZippy kernel: [   61.702518] end_request: I/O error, dev sr0, sector 1199920
Aug 13 09:44:07 WickedZippy kernel: [   61.702582] Buffer I/O error on device sr0, logical block 149990
Aug 13 09:44:07 WickedZippy kernel: [   63.387570] end_request: I/O error, dev sr0, sector 1199920
Aug 13 09:44:07 WickedZippy kernel: [   63.387633] Buffer I/O error on device sr0, logical block 149990
Aug 13 09:44:07 WickedZippy kernel: [   65.142962] end_request: I/O error, dev sr0, sector 1199920
Aug 13 09:44:07 WickedZippy kernel: [   65.143025] Buffer I/O error on device sr0, logical block 149990
Aug 13 09:44:07 WickedZippy kernel: [   66.792847] end_request: I/O error, dev sr0, sector 1199920
Aug 13 09:44:07 WickedZippy kernel: [   66.792910] Buffer I/O error on device sr0, logical block 149990
Aug 13 09:44:07 WickedZippy kernel: [   68.513094] end_request: I/O error, dev sr0, sector 1199920
Aug 13 09:44:07 WickedZippy kernel: [   68.513157] Buffer I/O error on device sr0, logical block 149990
Aug 13 09:44:07 WickedZippy kernel: [   70.233047] end_request: I/O error, dev sr0, sector 1199920
Aug 13 09:44:07 WickedZippy kernel: [   70.233109] Buffer I/O error on device sr0, logical block 149990
Aug 13 09:44:07 WickedZippy kernel: [   71.953111] end_request: I/O error, dev sr0, sector 1199920
Aug 13 09:44:07 WickedZippy kernel: [   71.953173] Buffer I/O error on device sr0, logical block 149990
Aug 13 09:44:07 WickedZippy kernel: [   74.673885] end_request: I/O error, dev sr0, sector 1199920
Aug 13 09:44:07 WickedZippy kernel: [   74.673948] Buffer I/O error on device sr0, logical block 149990
Aug 13 09:44:07 WickedZippy kernel: [   77.145889] end_request: I/O error, dev sr0, sector 1199920
Aug 13 09:44:07 WickedZippy kernel: [   77.145952] Buffer I/O error on device sr0, logical block 149990
Aug 13 09:44:07 WickedZippy kernel: [   78.619883] end_request: I/O error, dev sr0, sector 1199920
Aug 13 09:44:07 WickedZippy kernel: [   78.619945] Buffer I/O error on device sr0, logical block 149990
Aug 13 09:44:07 WickedZippy kernel: [   80.129262] end_request: I/O error, dev sr0, sector 1199920
Aug 13 09:44:07 WickedZippy kernel: [   80.129323] Buffer I/O error on device sr0, logical block 149990
Aug 13 09:44:07 WickedZippy kernel: [   81.846181] end_request: I/O error, dev sr0, sector 1199920
Aug 13 09:44:07 WickedZippy kernel: [   81.846244] Buffer I/O error on device sr0, logical block 149990
Aug 13 09:44:07 WickedZippy kernel: [   83.393865] end_request: I/O error, dev sr0, sector 1199920
Aug 13 09:44:07 WickedZippy kernel: [   83.393928] Buffer I/O error on device sr0, logical block 149990
Aug 13 09:44:07 WickedZippy kernel: [   84.832897] end_request: I/O error, dev sr0, sector 1199920
Aug 13 09:44:07 WickedZippy kernel: [   84.832959] Buffer I/O error on device sr0, logical block 149990
Aug 13 09:44:07 WickedZippy kernel: [   86.271804] end_request: I/O error, dev sr0, sector 1199920
Aug 13 09:44:07 WickedZippy kernel: [   86.271869] Buffer I/O error on device sr0, logical block 149990
Aug 13 09:44:07 WickedZippy kernel: [   87.859367] end_request: I/O error, dev sr0, sector 1199920
Aug 13 09:44:07 WickedZippy kernel: [   87.859430] Buffer I/O error on device sr0, logical block 149990
Aug 13 09:44:07 WickedZippy kernel: [   88.583425] ISO 9660 Extensions: Microsoft Joliet Level 3
Aug 13 09:44:07 WickedZippy kernel: [   88.630892] ISOFS: changing to secondary root

```

My system info:
```

cpu:                                                            
                       AMD Athlon(tm) 64 X2 Dual Core Processor 5600+, 1000 MHz
                       AMD Athlon(tm) 64 X2 Dual Core Processor 5600+, 1000 MHz
keyboard:
  /dev/input/event3    Logitech USB Receiver
mouse:
  /dev/input/mice      Logitech USB Receiver
  /dev/input/mice      Macintosh mouse button emulation
graphics card:
                       nVidia GeForce 7300 GT
                       nVidia GeForce 7025
sound:
                       nVidia MCP67 High Definition Audio
storage:
                       Floppy disk controller
                       nVidia MCP67 AHCI Controller
                       nVidia MCP67 IDE Controller
network:
  eth0                 nVidia MCP67 Ethernet
network interface:
  pan0                 Ethernet network interface
  eth0                 Ethernet network interface
  lo                   Loopback network interface
disk:
  /dev/sda             WDC WD2500AAKS-0
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda3            Partition
[B]cdrom:
  /dev/sr0             HL-DT-ST CD-RW GCE-8483B[/B]
usb controller:
                       nVidia MCP67 EHCI USB 2.0 Controller
                       nVidia MCP67 OHCI USB 1.1 Controller
                       nVidia MCP67 EHCI USB 2.0 Controller
                       nVidia MCP67 OHCI USB 1.1 Controller

```
I have no idea how to restore the system from a couple days ago. I've read a post where back in '07/'08 people were having trouble with optical drives, but that is not what I have and I didn't experience this problem until the last update.

Any ideas? Thanks in advance.

---

### Post by rbeasley on 2009-08-27
I ran into something similar to this recently, and at first I thought it was due to hardware faults rather than an upgrade.  (I only use my CD-ROM drives when ripping new CDs from Rasputin & Amoeba. :))

Anyway, my problem was triggered by HAL's device polling.  Once I disabled that on my drives, everything has run smoothly.

1.  Run "lshal" and look for the UDI corresponding to your CD-ROM drive(s).
2.  Disable polling using "hal-disable-polling --udi $yourUdi".
3.  Either restart the HAL service manually (/etc/init.d/hal restart) or reboot.

You may optionally kill the hal-addon-storage process(es) polling your drive(s).

Hope this helps.  :)

---

### Post by charm_quark on 2009-10-10
i'm having the same error, but this is not an upgrade, its a fresh install! what could be the problem, all hardware is ok! and my disk is also ok!

---

### Post by APU on 2009-12-11
Same Problem here and disablin hal-device-polling does not help at all.

The problem occured a couple months ago when I was running Jaunty still - reading from a CD or DVD completely locked up the system.

Since then I have updated the BIOS, installed Karmic completely from scratch, replaced the DVD Drive with a new one and replaced all cabling - the issue ist still there.

This is what happens:

Put in a DVD (or CD for that matter) - wait abouth half a minute, maybe try to read from it and then the system freezes completely needing a hard reset.

I did not (!!)= have any issues installing a new System using a self-burned Karmic-alternate .iso CD. Booting from a CD never fails or gives problems... so there is definitely some software problem that involves an installed Ubuntu system. 

Ideas anyone???

[EDIT]
I have just found out via an old forum post ([http://ubuntuforums.org/showthread.php?t=826476](http://ubuntuforums.org/showthread.php?t=826476)) that the problem already occured when I was using Hardy 1 1/2 years ago! Back then I only tried to play some DVDs and was blaming libdvdread & co. for it but now I think I was wrong with that. This shows that I do not really need the DVD drive that often but this issue is still very bad.

---

### Post by FireflyCalvin on 2009-12-14
APU,

Sorry to hear you're still having issues. While I technically I should mark this thread [SOLVED], because I do not have the issue any more, it's still a bit of a mystery of what happened.

My problem was solved by simply swapping in a new CD-DVD ROM drive. It worked and I didn't investigate further.

Have you tried other flavors of Linux, or even Ubuntu Karmic Koala (9.10)?

---

