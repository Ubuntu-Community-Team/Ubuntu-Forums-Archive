---
title: "HD problem: &quot;Device offlined - not ready after error recovery&quot;"
date: 2012-04-06
forum: General Help
---

### Post by Asmodai on 2012-04-06
Greetings,

I have a problem with one of my external hard disks. Since today, any sort of I/O from/to the disk stops occasionally. When powering off the hard disk and reconnecting it, it works again.

There are ten-thousands of messages in my syslog, like the following:
```
Apr  6 17:26:19 MintX kernel: [ 3506.270049] usb 2-3: reset high speed USB device using ehci_hcd and address 3
Apr  6 17:26:19 MintX kernel: [ 3506.421098] sd 9:0:0:0: Device offlined - not ready after error recovery
Apr  6 17:26:19 MintX kernel: [ 3506.421114] sd 9:0:0:0: [sdk] Unhandled error code
Apr  6 17:26:19 MintX kernel: [ 3506.421116] sd 9:0:0:0: [sdk]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Apr  6 17:26:19 MintX kernel: [ 3506.421121] sd 9:0:0:0: [sdk] CDB: Write(10): 2a 00 04 ea 1a af 00 00 f0 00
Apr  6 17:26:19 MintX kernel: [ 3506.421129] end_request: I/O error, dev sdk, sector 82451119
Apr  6 17:26:19 MintX kernel: [ 3506.421134] Buffer I/O error on device sdk1, logical block 10306382
Apr  6 17:26:19 MintX kernel: [ 3506.421137] lost page write due to I/O error on sdk1
Apr  6 17:26:19 MintX kernel: [ 3506.421143] Buffer I/O error on device sdk1, logical block 10306383
Apr  6 17:26:19 MintX kernel: [ 3506.421145] lost page write due to I/O error on sdk1
[...]
Apr  6 17:26:19 MintX kernel: [ 3506.421184] Buffer I/O error on device sdk1, logical block 10306391
Apr  6 17:26:19 MintX kernel: [ 3506.421186] lost page write due to I/O error on sdk1
Apr  6 17:26:19 MintX kernel: [ 3506.421213] sd 9:0:0:0: rejecting I/O to offline device
Apr  6 17:26:19 MintX kernel: [ 3506.421225] sd 9:0:0:0: rejecting I/O to offline device
Apr  6 17:26:19 MintX kernel: [ 3506.421258] sd 9:0:0:0: rejecting I/O to offline device
[...]
Apr  6 17:26:19 MintX kernel: [ 3506.425148] sd 9:0:0:0: rejecting I/O to offline device
Apr  6 17:26:19 MintX kernel: [ 3506.425173] sd 9:0:0:0: rejecting I/O to offline device
Apr  6 17:26:19 MintX kernel: [ 3506.425261] sd 9:0:0:0: [sdk] Unhandled error code
Apr  6 17:26:19 MintX kernel: [ 3506.425263] sd 9:0:0:0: [sdk]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Apr  6 17:26:19 MintX kernel: [ 3506.425267] sd 9:0:0:0: [sdk] CDB: Write(10): 2a 00 04 ea 1b 9f 00 00 f0 00
Apr  6 17:26:19 MintX kernel: [ 3506.425275] end_request: I/O error, dev sdk, sector 82451359
Apr  6 17:26:19 MintX kernel: [ 3506.425325] sd 9:0:0:0: rejecting I/O to offline device
Apr  6 17:26:19 MintX kernel: [ 3506.425358] sd 9:0:0:0: rejecting I/O to offline device
Apr  6 17:26:19 MintX kernel: [ 3506.425397] sd 9:0:0:0: rejecting I/O to offline device
[...]
Apr  6 17:27:49 MintX kernel: [ 3596.991927] sd 9:0:0:0: rejecting I/O to offline device
Apr  6 17:27:49 MintX kernel: [ 3596.991936] sd 9:0:0:0: rejecting I/O to offline device
Apr  6 17:28:30 MintX kernel: [ 3637.300729] usb 2-3: USB disconnect, address 3

```Can anyone tell what exactly the problem is from these error messages? I'm a bit worried as I currently don't have any spare disks to copy the data over.
Edit: the drive has quite a few relocated sectors (about 4,000), however those are not new (the drive suffered from a hit) and I've been using the drive despite that for about a year without any real problems.

---

### Post by dcstar on 2012-04-07
> **Asmodai said:**
> Greetings,

I have a problem with one of my external hard disks. Since today, any sort of I/O from/to the disk stops occasionally. When powering off the hard disk and reconnecting it, it works again.
.........
Edit: the drive has quite a few relocated sectors (about 4,000), however those are not new (the drive suffered from a hit) and I've been using the drive despite that for about a year without any real problems.

Don't worry too much, I sure the problem will go away after a more restarts when the drive dies totally.

---

