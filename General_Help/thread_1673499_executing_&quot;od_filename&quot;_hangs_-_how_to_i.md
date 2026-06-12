---
title: "executing &quot;od filename&quot; hangs - how to identify the problem"
date: 2011-01-22
forum: General Help
---

### Post by 666f6f on 2011-01-22
Hi,

When I try to read a specific file by executing ```
od filename
``` od hangs.

I have run ```
sudo e2fsck /dev/sdb6 -n -f
``` and reported no errors.

I plan to run a badblocks ckeck but that will take ages to complete. Is there anything else I can do?

Thanks
666f6f

---

### Post by gmargo on 2011-01-22
What file?  Any file or some special file?  **od(1)** works fine for me.  Do you have a script or alias that is interfering?  Does od really hang or is it just reading from standard input?

---

### Post by 666f6f on 2011-01-22
> **gmargo said:**
> What file? Any file or some special file? 


It is a normal file. But it doesn't hang for every normal file, it hangs only when I try to read a specific file (foo.mp3). I suspect a hardware problem :(

> **gmargo said:**
> **od(1)** works fine for me. Do you have a script or alias that is interfering?  Does od really hang or is it just reading from standard input?

It really hangs. It dumps the hex output up to a certain point and then, at a specific address, it just hangs.

It is a Western Digital Green 1 TB hard disk drive. I have started the badblock scan because I suspect it's broken :(

---

### Post by gmargo on 2011-01-22
Sounds like a hardware issue.  Check the logs under /var/logs/ (syslog? messages?) to see if you have any kernel messages about disk errors.

---

### Post by 666f6f on 2011-01-22
> **gmargo said:**
> Sounds like a hardware issue.  Check the logs under /var/logs/ (syslog? messages?) to see if you have any kernel messages about disk errors.

I do get this, which obviously isn't great news.. (yes, the log entry is from Jan 16. I experience this problem for quite some time now).

```

Jan 16 14:03:56 chronos kernel: [322712.548010] usb 4-1: USB disconnect, address 2
Jan 16 14:03:56 chronos kernel: [322712.548401] sd 2:0:0:0: [sdb] Unhandled error code
Jan 16 14:03:56 chronos kernel: [322712.548410] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
Jan 16 14:03:56 chronos kernel: [322712.548422] sd 2:0:0:0: [sdb] CDB: Read(10): 28 00 5a d8 38 bd 00 00 f0 00
Jan 16 14:03:56 chronos kernel: [322712.548904] sd 2:0:0:0: [sdb] Unhandled error code
Jan 16 14:03:56 chronos kernel: [322712.548913] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jan 16 14:03:56 chronos kernel: [322712.548924] sd 2:0:0:0: [sdb] CDB: Read(10): 28 00 5a d8 39 ad 00 00 10 00
Jan 16 14:03:56 chronos kernel: [322712.549053] sd 2:0:0:0: [sdb] Unhandled error code
Jan 16 14:03:56 chronos kernel: [322712.549061] sd 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jan 16 14:03:56 chronos kernel: [322712.549072] sd 2:0:0:0: [sdb] CDB: Read(10): 28 00 5a d8 39 bd 00 00 f0 00
Jan 16 14:03:57 chronos kernel: [322713.064192] usb 4-1: new high speed USB device using ehci_hcd and address 4
Jan 16 14:04:02 chronos kernel: [322718.203881] scsi3 : usb-storage 4-1:1.0
Jan 16 14:04:03 chronos kernel: [322719.209880] scsi 3:0:0:0: Direct-Access     WDC WD10 EADS-00M2B0           PQ: 0 ANSI: 2
Jan 16 14:04:03 chronos kernel: [322719.214765] sd 3:0:0:0: Attached scsi generic sg1 type 0
Jan 16 14:04:03 chronos kernel: [322719.216829] sd 3:0:0:0: [sdc] 1953523055 512-byte logical blocks: (1.00 TB/931 GiB)
Jan 16 14:04:03 chronos kernel: [322719.219195] sd 3:0:0:0: [sdc] Write Protect is off
Jan 16 14:04:03 chronos kernel: [322719.223705]  sdc: sdc1 sdc2 sdc3 < sdc5 sdc6 >
Jan 16 14:04:03 chronos kernel: [322719.278215] sd 3:0:0:0: [sdc] Attached SCSI disk
Jan 16 14:05:06 chronos kernel: Kernel logging (proc) stopped.

```

---

### Post by 666f6f on 2011-01-23
For the records, badblocks did not find any badblock.. :S And now I can normally read the foo.mp3..

---

### Post by 666f6f on 2011-01-24
I connect my USB hard disk via a USB cardbus adapter, which has two USB ports. If on the other USB port I connect a wireless adapter, my hard disk stops working randomly. So, the problem in my case turns out to be insufficient power supply to my cardbus USB adapter.

---

