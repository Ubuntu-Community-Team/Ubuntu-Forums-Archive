---
title: "Hibernated from LightDM and now...."
date: 2012-01-07
forum: General Help
---

### Post by arkanabar on 2012-01-07
I use 32-bit 11.10 with the unity interface.

Here's what happened.

I had been afk long enough for the screen to lock, and I needed to shut down and leave  in a hurry.  I use a complicated password and my keyboard will occasionally input characters I have not typed.  So I chose "switch user," which put me in lightDM (login screen), and from there selected "hibernate."  If I remember correctly, it hung or failed, I don't remember how, and so I forced shutdown by holding down the power button on my case.  This has done something to the disk.  I have run nano on ubuntu, but as yet nothing on Mint 11 LXDE at all.  I've run fsck in recovery, but it doesn't fix anything.  My / filesystem mounts read only, but I can write to /home.  X won't launch any more; nor will irssi, and w3m throws out a bunch of ata3.00 errors on exit, something like 
```
ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x6
ata3.00:  BMDMA stat 0x4
ata3: SError: {Handshk}
ata3.00: failed command: WRITE DMA EXT
ata3.00: cmd 35/00:08:e0:aa:93/00:00:12:00:00/e0 tag 0 dma 4096 out
         res 51/84:08:e0:aa:93/84:00:12:00:00/e0 Emask 0x10 (ATA bus error)
ata3.00: status: { DRDY ERR }
ata3.00: error: { ICRC ABRT }
```

fstab has the right UUID for swap, as does /etc/initramfs-tools/conf.d/resume

I have a copy of GParted 5.10 live cd that I can use to edit config files if I need to, or edit partitions.

Any suggestions at all, either diagnostic or possible solutions, would be welcome.  I'd rather not start over, as that could mean a few days of trying not to annoy the other people on my network with excessive bandwidth usage.

---

### Post by arkanabar on 2012-01-07
I've sort of given up on restoration, or even backing up WoW (which, tbh, takes longer than all my other downloads combined and that I can easily live without).  Since I have a fairly complicated partitioning  scheme, I decided to boot PartedMagic 5.10.  Neither GParted 0.8.0 nor GSmart Control 0.8.5 nor TestDisk 6.12 can recognize the disk where Ubuntu 11.10 & Mint 11 are installed.  So, somehow, this action of mine appears to have messed up my partition table.

---

