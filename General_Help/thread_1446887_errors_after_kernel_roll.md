---
title: "errors after kernel roll"
date: 2010-04-04
forum: General Help
---

### Post by ant2ne on 2010-04-04
I rolled my own 2.6.33.2.

On boot up I get some errors similar to the following...

```
radeonfb 000:00:10.0: invalid ROM contents
ext2-fs hda3 error couldn't mount because of usuported optoinal featuers (240)
ext3-fs hda3 error couldn't mount
init readahead main process (1045) terminated with status 1
mountall could not connect to plymouth
sd 0:0:0:0 sda] assuming drive cache write through
```

The system then continues to boot (quicker than it did with the old kernel) and I can log in and everything seems to work. I'd still like to get these errors cleaned up.

dmesg isn't much help. I think because I've enabled some level of debugging that is spamming my dmesg such as...

```
usb-storage: Bulk Command S 0x43425355 T 0x3b L 18 F 128 Trg 0 LUN 0 CL 6
usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
usb-storage: Status code 0; transferred 31/31
usb-storage: -- transfer complete

```and```
PM: Adding info for No Bus:sequencer
PM: Adding info for No Bus:sequencer2
PM: Removing info for No Bus:0.00030000:radio

```

I've done some googling around but haven't found any good help. I'm wondering if there is a kernel expert who could lend some advice. Attached is my current .config.

---

