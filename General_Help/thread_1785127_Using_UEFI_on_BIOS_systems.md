---
title: "Using UEFI on BIOS systems"
date: 2011-06-17
forum: General Help
---

### Post by srs5694 on 2011-06-17
If you're curious about UEFI, or if you want to use GPT but have reservations because of a Windows installation that's not GPT-ready, you might be interested in a new Web page I've put up:

[http://www.rodsbooks.com/bios2uefi/index.html](http://www.rodsbooks.com/bios2uefi/index.html)

That page describes how to slap a UEFI implementation atop a standard BIOS computer using something called UEFI DUET. The procedure to do all this is *highly* experimental, so I don't recommend you rush out and convert a working system right away. It could be worth experimenting with if you've got a spare hard disk to use as a guinea pig, though.

To be clear: Ubuntu won't benefit from booting from UEFI, AFAIK. The main advantage to be gained from this sort of setup is to Windows on >2 TiB disks or to a dual-boot configuration if you want to use GPT rather than MBR. (Ubuntu boots fine from GPT disks even on a BIOS-based computer, but Windows requires UEFI to boot from a GPT disk.) Using GPT has a number of advantages:


[LIST]
[*]Support for >2 TiB disks.
[*]No more pesky extended or logical partitions; GPT supports up to 128 partitions by default, and they're all essentially like MBR's primary partitions.
[*]You can move a Windows partition and it'll still boot.
[*]GPT includes CRCs and backups of its data structures, making it theoretically more robust against damage than MBR.
[/LIST]


To reiterate, these advantages are *not* great enough for me to recommend that you casually install UEFI DUET; but if you want to familiarize yourself with UEFI or if you have a real need for its features, you might want to give it a try on a test disk, and maybe then implement it on a "real" disk.

---

