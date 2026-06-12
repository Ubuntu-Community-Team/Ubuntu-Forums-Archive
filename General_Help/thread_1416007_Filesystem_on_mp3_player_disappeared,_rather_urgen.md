---
title: "Filesystem on mp3 player *disappeared*, rather urgent file recovery"
date: 2010-02-25
forum: General Help
---

### Post by btnz on 2010-02-25
Hi,
so, weird things are happening: I have some text files stored on my mp3 player, and until like 3 days ago everything worked just fine with it, I used it to listen to music etc.
Now today I try to access it, plug it into my notebook running ubuntu 9.10 (USB) and it just doesn't get mounted.
When I unplug it and try to play music or access the internal storage in any other way it says 'disk error'.
In gparted it shows up as unallocated space.
Unfortunately I don't know what file-system it previously was, as it is just a standard 1GB chip, I'd guess for FAT16 though.

So, please, how do I proceed?
thx!

oh, here is what i get in kern.log when i plug it in:
```
                               
 usb 2-1: new high speed USB device using ehci_hcd and address 23               
 usb 2-1: configuration #1 chosen from 1 choice                                 
 scsi22 : SCSI emulation for USB Mass Storage devices                           
 usb-storage: device found at 23                                                
 usb-storage: waiting for device to settle before scanning                      
 usb-storage: device scan complete                                              
 scsi scan: INQUIRY result too short (5), using 36                              
 scsi 22:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
 sd 22:0:0:0: Attached scsi generic sg3 type 0                                  
 1982129 512-byte logical blocks: (1.01 GB/967 MiB)                             
 Write Protect is off                                                           
 Mode Sense: 00 c0 00 00                                                        
 Assuming drive cache: write through                                            
 Assuming drive cache: write through                                            
**  sdc: unknown partition table **                                                 
 Assuming drive cache: write through                                            
 Attached SCSI removable disk              

```

---

### Post by Chronon on 2010-02-25
This page seems promising: [http://www.linuxjournal.com/article/8366](http://www.linuxjournal.com/article/8366)

Let me know if that procedure works for you.  Obviously, make sure you use the correct device (/dev/sdc if nothing changes) with the dd command.

The whole article is a bit involved. . . the summary of what worked can be found on the last page: [http://www.linuxjournal.com/article/8366?page=0,3](http://www.linuxjournal.com/article/8366?page=0,3).  However, it's probably worth reading the whole article since I'm not sure precisely which conditions are common to both situations.

---

