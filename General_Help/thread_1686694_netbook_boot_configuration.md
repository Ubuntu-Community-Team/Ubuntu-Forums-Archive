---
title: "netbook boot configuration"
date: 2011-02-12
forum: General Help
---

### Post by ricardopresto on 2011-02-12
[I'm re-posting this here because I think I posted it in the wrong section to begin with...sorry]

Hi folks

The ssd in my aspire1 netbook has given up the ghost so I'm running ubuntu off a live usb, which is bearable but not ideal. The aspire1 has two onboard sd card slots, but is not able to boot to them. So I was wondering if there's any way to have just the bootloader on the usb stick, which would then load the os files from the sd card?

Or am I talking gibberish because I don't really understand how bootloaders work? :rolleyes:

Any advice gratefully received

ricardo

---

### Post by dcstar on 2011-02-13
> **ricardopresto said:**
> [I'm re-posting this here because I think I posted it in the wrong section to begin with...sorry]

Hi folks

The ssd in my aspire1 netbook has given up the ghost so I'm running ubuntu off a live usb, which is bearable but not ideal. The aspire1 has two onboard sd card slots, but is not able to boot to them. So I was wondering if there's any way to have just the bootloader on the usb stick, which would then load the os files from the sd card?

Or am I talking gibberish because I don't really understand how bootloaders work? :rolleyes:

Any advice gratefully received

ricardo

When you do the install select "manual" partitioning and create a small /boot partition (100MB) on the USB, and the "/" and Swap partitions on the SD card(s).

That should allow Grub to load off the USB and then boot the main OS on the SD card(s).

---

### Post by ricardopresto on 2011-02-13
Cheers mate!

---

### Post by ricardopresto on 2011-02-25
Finally got round to trying this...and it doesn't work. :(

'No Operating System Found'

Any ideas?

ricardo

---

