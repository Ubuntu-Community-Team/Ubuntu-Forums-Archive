---
title: "usb drive, sd card not detected"
date: 2010-07-05
forum: General Help
---

### Post by cheshirekow on 2010-07-05
I just installed 10.04 and my SD card reader and my usb hard drive are not recognized. My USB tablet (Wacom Bamboo) works fine.

I checked dmesg and it seems that usb driver has found the device. Note that I disconnected the device and reconnected it to make sure that the "new high speed USB device" was the usb hard drive.

```

josh@Nadie:~$ dmesg | tail
[  601.142564] EXT3-fs: mounted filesystem with ordered data mode.
[  606.421382] kjournald starting.  Commit interval 5 seconds
[  606.421411] EXT3-fs: mounted filesystem with ordered data mode.
[  606.996796] kjournald starting.  Commit interval 5 seconds
[  606.996867] EXT3-fs: mounted filesystem with ordered data mode.
[ 1310.374797] usb 2-1.3: new high speed USB device using ehci_hcd and address 5
[ 1310.496847] usb 2-1.3: configuration #1 chosen from 1 choice
[ 2040.963946] usb 2-1.3: USB disconnect, address 5
[ 2052.971000] usb 2-1.3: new high speed USB device using ehci_hcd and address 6
[ 2053.083204] usb 2-1.3: configuration #1 chosen from 1 choice


```


and when I try 'lsusb' I also see the hard drive listed (Western Digital):

```

josh@Nadie:~$ lsusb
Bus 002 Device 006: ID 1058:1010 Western Digital Technologies, Inc. 
Bus 002 Device 004: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 002 Device 003: ID 056a:0018 Wacom Co., Ltd 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

But nothing get's listed in /dev

```

josh@Nadie:~$ ls -l /dev/sd*
brw-rw---- 1 root disk 8, 0 2010-07-05 22:07 /dev/sda
brw-rw---- 1 root disk 8, 1 2010-07-05 22:07 /dev/sda1
brw-rw---- 1 root disk 8, 2 2010-07-05 22:07 /dev/sda2
brw-rw---- 1 root disk 8, 3 2010-07-05 22:07 /dev/sda3
brw-rw---- 1 root disk 8, 4 2010-07-05 22:07 /dev/sda4
brw-rw---- 1 root disk 8, 5 2010-07-05 22:07 /dev/sda5
brw-rw---- 1 root disk 8, 6 2010-07-05 22:07 /dev/sda6
brw-rw---- 1 root disk 8, 7 2010-07-05 22:07 /dev/sda7

```

Note that sda is the main hard drive that ubuntu is installed on. I read on linux forums that maybe certain kernal modules were missing but I don't know what they would be called so I tried lsmod and grep'ed for "usb"

```

josh@Nadie:~$ lsmod | grep -P .*usb.*
usbhid                 40988  0 
hid                    83376  1 usbhid

```

I'm not sure what else to do to debug the issue. Any help will be appreciated.

---

### Post by cheshirekow on 2010-07-06
A few additional notes. The hard drive is a Western Digital portable USB drive (i.e. usb powered) (model is passport I believe?) 640GB. It mounts and is accessible on my eeepc running xubuntu 10.04. 

This machine with the problem has previously run 9.04 and at that time the usb hard drives and SD cards were not working either. The hard drive is formated with ext4.

This machine is a dell m4500 with a core i7-820. I'm using 10.04 amd64 (though when I had 9.04 it was the x86 version).

---

### Post by cheshirekow on 2010-07-06
OK. I got the USB drive to work. I did a couple of things but I think the real problem was that I upgraded the kernel to -23... but didn't edit the grub menu (grub menu is manually made) so I was still booting into -21, after already removing the -21 packages from the synaptic. 

The other thing I did after rebooting was to run 

```

modprobe usb_storage

```

And then updated my graphics driver (probably not related). In any case, after rebooting, the USB drive mounts fine. But the SD Card does not. If I insert an SD card this is what appears in dmesg:

```

josh@Nadie:~$ dmesg | tail -n 44
[  546.042559] usb 2-1.3: USB disconnect, address 5
[  570.269700] mmc0: Unexpected interrupt 0x02000000.
[  570.269705] sdhci: ============== REGISTER DUMP ==============
[  570.269711] sdhci: Sys addr: 0x00000000 | Version:  0x00000402
[  570.269718] sdhci: Blk size: 0x00007008 | Blk cnt:  0x00000001
[  570.269723] sdhci: Argument: 0x00000000 | Trn mode: 0x00000013
[  570.269729] sdhci: Present:  0x01ff0202 | Host ctl: 0x00000011
[  570.269735] sdhci: Power:    0x0000000f | Blk gap:  0x00000000
[  570.269741] sdhci: Wake-up:  0x00000000 | Clock:    0x00004007
[  570.269747] sdhci: Timeout:  0x0000000a | Int stat: 0x02008008
[  570.269752] sdhci: Int enab: 0x02ff00cb | Sig enab: 0x02ff00cb
[  570.269758] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000001
[  570.269764] sdhci: Caps:     0x21e832b2 | Max curr: 0x00000040
[  570.269769] sdhci: ADMA Err: 0x00000001 | ADMA Ptr: 0x201f3934
[  570.269772] sdhci: ===========================================
[  570.269785] mmc0: Unexpected interrupt 0x02000000.
[  570.269787] sdhci: ============== REGISTER DUMP ==============
[  570.269793] sdhci: Sys addr: 0x00000000 | Version:  0x00000402
[  570.269799] sdhci: Blk size: 0x00007008 | Blk cnt:  0x00000001
[  570.269805] sdhci: Argument: 0x00000000 | Trn mode: 0x00000013
[  570.269811] sdhci: Present:  0x01ff0202 | Host ctl: 0x00000011
[  570.269816] sdhci: Power:    0x0000000f | Blk gap:  0x00000000
[  570.269822] sdhci: Wake-up:  0x00000000 | Clock:    0x00004007
[  570.269828] sdhci: Timeout:  0x0000000a | Int stat: 0x02008008
[  570.269834] sdhci: Int enab: 0x02ff00cb | Sig enab: 0x02ff00cb
[  570.269843] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000001
[  570.269852] sdhci: Caps:     0x21e832b2 | Max curr: 0x00000040
[  570.269862] sdhci: ADMA Err: 0x00000001 | ADMA Ptr: 0x00000028
[  570.269864] sdhci: ===========================================
[  580.264697] mmc0: Timeout waiting for hardware interrupt.
[  580.264704] sdhci: ============== REGISTER DUMP ==============
[  580.264716] sdhci: Sys addr: 0x00000000 | Version:  0x00000402
[  580.264727] sdhci: Blk size: 0x00007008 | Blk cnt:  0x00000001
[  580.264738] sdhci: Argument: 0x00000000 | Trn mode: 0x00000013
[  580.264749] sdhci: Present:  0x01ff0202 | Host ctl: 0x00000011
[  580.264760] sdhci: Power:    0x0000000f | Blk gap:  0x00000000
[  580.264771] sdhci: Wake-up:  0x00000000 | Clock:    0x00004007
[  580.264782] sdhci: Timeout:  0x0000000a | Int stat: 0x00000000
[  580.264793] sdhci: Int enab: 0x02ff00cb | Sig enab: 0x02ff00cb
[  580.264803] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[  580.264812] sdhci: Caps:     0x21e832b2 | Max curr: 0x00000040
[  580.264822] sdhci: ADMA Err: 0x00000001 | ADMA Ptr: 0x00000028
[  580.264825] sdhci: ===========================================
[  580.267899] mmc0: error -110 whilst initialising SD card
josh@Nadie:~$ 

```

Note, I unplugged the USB drive right before inserting the SD card so I could make sure I knew where the relevant messages were.

---

### Post by CyberCastle on 2010-07-25
For SD reader (Ricoh E822 Device) fix here:

[https://bugzilla.redhat.com/show_bug.cgi?id=596475](https://bugzilla.redhat.com/show_bug.cgi?id=596475)

---

### Post by cheshirekow on 2010-08-04
Thank you very much for the link to the patch for the fix. I am very sorry for the nub-ness but I'm not sure exactly how to apply this. Is sdhc a kernel module? Do I need to download the kernel source package, apply this patch to that, and rebuild the kernel? Or can I somehow download just the source for the sdhc module and patch that? It seems the sources are included on the bugzilla page, but without a makefile I'm at a bit of a loss on what to do. I won't lie.. I'm not 100% sure on how to apply a patch (from the manual, maybe: patch [??] < xxx.diff).

---

