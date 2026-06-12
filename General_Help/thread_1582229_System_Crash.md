---
title: "System Crash?"
date: 2010-09-26
forum: General Help
---

### Post by snorkytheweasel on 2010-09-26
10.04 / 64-bit / 2 SATA drives each with more than 150 GB free.
 
While ripping a CD, after ripping several tracks successfully, I started getting errors: "cannot write to read only disk". I tried two other CDs, each refusing to rip/copy anything, with the same "read-only" error. 

Then I could not reboot - after clicking on restart, nothing happened.

I powered down, waited a while, and tried to boot up. The boot process started ok (hardware diagnostics) but hung with only "GRUB" on the screen. Subsequent retries gave the same results.

What happened? What should I do to recover from this?

---

### Post by TeoBigusGeekus on 2010-09-26
Boot up with a live cd and fsck your drives.

---

### Post by P4man on 2010-09-26
sounds like a harddisk that gave up on you. The read-only thing is (I suspect) ubuntu (re-)mounting the drive as readonly to prevent further damage.

Here is what I would do: boot an ubuntu cd or usb stick. Go to system > administration > disk utility. Check the smart status of the drives. Good chance your boot drive has died.

---

### Post by snorkytheweasel on 2010-10-03
It was a hard drive failure.

---

