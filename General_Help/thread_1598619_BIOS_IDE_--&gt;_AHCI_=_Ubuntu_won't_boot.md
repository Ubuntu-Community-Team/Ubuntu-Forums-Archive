---
title: "BIOS IDE --&gt; AHCI = Ubuntu won't boot"
date: 2010-10-16
forum: General Help
---

### Post by davidmenges on 2010-10-16
I did a stupid thing (apparently), and am wondering if anyone has also done it.

Long story short, I changed these BIOS settings (and changed them back), but now Ubuntu won't boot:

[INDENT]SATA RAID/AHCI Mode:  from Disabled to AHCI
Onboard SATA/IDE Ctlr Mode:  from IDE to AHCI[/INDENT]

The last thing it says is "Init:  ureadahead-other main process (nnn) terminated with status 4".  Booting off an Ubuntu CD and entering Rescue mode gets me to a shell; the file systems are still there, but...

Reward for first solution (other than reload):  $10 Starbucks card!

---

### Post by dcstar on 2010-10-16
> **davidmenges said:**
> I did a stupid thing (apparently), and am wondering if anyone has also done it.

Long story short, I changed these BIOS settings (and changed them back), but now Ubuntu won't boot:

[INDENT]SATA RAID/AHCI Mode:  from Disabled to AHCI
Onboard SATA/IDE Ctlr Mode:  from IDE to AHCI[/INDENT]

The last thing it says is "Init:  ureadahead-other main process (nnn) terminated with status 4".  Booting off an Ubuntu CD and entering Rescue mode gets me to a shell; the file systems are still there, but...

Reward for first solution (other than reload):  $10 Starbucks card!

Firstly, Ubuntu is AHCI compatible, so I'm not sure why it would not boot after this change.

Secondly, are you **100%** sure you returned **all** BIOS settings to what they were before? You should do a full BIOS reset to defaults and see if that allows booting.

---

### Post by davidmenges on 2010-10-16
Never mind...  It turns out there was an entry in /etc/fstab for an eSATA drive I had attached briefly recently, and that's what boot was hung up on.  I happened to hit the "s" key, which "s"kipped the entry and proceeded to boot.  All I had to do then was edit out the extra entry, and all is well.  Thanks, though!

---

### Post by sendblink23 on 2010-10-16
good u got it

---

