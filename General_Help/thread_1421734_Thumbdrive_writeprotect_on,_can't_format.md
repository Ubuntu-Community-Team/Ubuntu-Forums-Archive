---
title: "Thumbdrive writeprotect on, can't format"
date: 2010-03-04
forum: General Help
---

### Post by doobiest on 2010-03-04
I see lots of posts on thumbdrives in read only, none seem to hit the mark with me. I'm leaning towards a corrupted storage device, probably because it's a cheap drive.

[871947.058028] scsi 15:0:0:0: Direct-Access              Flash Disk       8.07 PQ: 0 ANSI: 2
[871947.058604] sd 15:0:0:0: Attached scsi generic sg2 type 0
[871947.075626] sd 15:0:0:0: [sdc] 3892352 512-byte logical blocks: (1.99 GB/1.85 GiB)
[871947.076242] sd 15:0:0:0: [sdc] Write Protect is off
[871947.076248] sd 15:0:0:0: [sdc] Mode Sense: 03 00 00 00
[871947.076252] sd 15:0:0:0: [sdc] Assuming drive cache: write through
[871947.081239] sd 15:0:0:0: [sdc] Assuming drive cache: write through
[871947.081247]  sdc: sdc1
[871947.358365] sd 15:0:0:0: [sdc] Write Protect is on
[871947.358371] sd 15:0:0:0: [sdc] Mode Sense: 03 00 80 00
[871947.358375] sd 15:0:0:0: [sdc] Assuming drive cache: write through
[871947.358381] sd 15:0:0:0: [sdc] Attached SCSI removable disk

Notice how when I plug it in write protect is off then suddenly on.  This occurs on any computer I put it in whether windows or linux.

In linux I cannot fdisk to /dev/<device> at all

I cannot format it.

I cannot dd if=/dev/zero of=dev/<device>

---

### Post by egalvan on 2010-03-04
Two things to look at...

does it have a "write-protect" switch?

was it properly un-mounted the las time it worked correctly?

---

### Post by pastalavista on 2010-03-04
have you been using sudo for your commands?

---

### Post by doobiest on 2010-03-04
1) No switch. I even removed it from the casing to see if I could find anything on the pcb.

2) Who knows. bottom line is if that caused it theres no way to correct the fs as it's in write protect mode.  I have put it into a windows box and properly removed it.

Also I dont think this is a at the filesystem level it's probably at the controller level. The device is write protect so no changes can be made to any aspect of the storage medium. Its not a partition thing or anything like that.

---

### Post by stoneage on 2010-03-04
Have you had any trouble recently writing to it? The last time I had a flash drive with write protect on, it died two days later.......

---

### Post by doobiest on 2010-03-04
*retracted.. screw it not worth the debate*

---

### Post by doobiest on 2010-03-04
> **stoneage said:**
> Have you had any trouble recently writing to it? The last time I had a flash drive with write protect on, it died two days later.......

I installed cygwin onto it and half way through the install it failed writing to it. And I've had this issue ever since. Which is why I suspect crappy hardware/corruption/cheap flash memory.

Since dmesg said write protect off for a moment I was hoping it was a controllable thing. But I have a feeling it defaults to off for reporting, then once it actually polls the device for it's status it updates the log to write protect on.

---

### Post by pastalavista on 2010-03-04
> **doobiest said:**
> Please dont try to help if the quality of your suggestions are of this level.

:rolleyes: You're absolutely right. You deserve only the best service possible and I hope you won't tell my manager... please, I really need this job.

---

### Post by doobiest on 2010-03-04
Ya I do hope for good input and I do try to be as detailed, complete, and anti-fluff in my threads as possible.

I probably should have left out all detail except for the dmesg output. Because any help people give me should be focused on the write-protect issue. It doesnt matter what I'm trying to do to the device while that's outstanding.

I think I'd have better luck getting technical advice of that level on a non-distro specific forum in the future, but in the case I'm going to call the drive garbage.

---

