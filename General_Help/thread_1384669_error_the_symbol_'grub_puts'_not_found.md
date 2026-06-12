---
title: "error: the symbol 'grub_puts' not found"
date: 2010-01-18
forum: General Help
---

### Post by alphabravoxxx on 2010-01-18
About 1 week ago, one of my PC's Hard Drives had stopped working. Because of that, I replaced the HD with a 2-set of Hard Disks from a earlier PC (whose Pentium 4 CPU failed). Because of a failed attempt in dual-booting with M$ WINDOW$, the MBR and Linux are separated between the hard drives. The computer booted up fine on first try (and even got into KDE), but it's internet didn't work (didn't even show eth0 on ifconfig). I decided to install some software via my old 8.04 LiveCD (I can't afford to format that PC for I have critical data on it, 0 DVDs, and no Flash drive), mounting it then chrooting it remembering to mount dev/pts sys and proc. Because the system was something old (Debian Squeeze from ~1 month ago), It had a kernel and GRUB upgrades which I missed among the ~600 others. Naturally, it failed to upgrade because of the missing /dev. Finally, I restarted my computer hoping for a upgraded PC with the programs. However, I instead got this:

```

| Sec. Slave Disk  : LBA,SATA,  160GB
-----------------------------------------------------------------------------------
IDE Channel 0 . Slave Disk HDD S.M.A.R.T. capability .... Disabled
IDE Channel 1 . Slave Disk HDD S.M.A.R.T. capability .... Disabled

PCI Devices Listing ...
Bus Dev Fun Vendor Device SVID SSID Class Device Class                          IRQ
-----------------------------------------------------------------------------------------------
 0   27   0   8086   27D8 1458 A002 0403  Multimedia Device                      5
 0   29   0   8086   27C8 1458 5004 0C03  USB 1.1 Host Cntrlr                    9
 0   29   1   8086   27C9 1458 5004 0C03  USB 1.1 Host Cntrlr                   11
 0   29   2   8086   27CA 1458 5004 0C03  USB 1.1 Host Cntrlr                   11
 0   29   3   8086   27CB 1458 5004 0C03  USB 1.1 Host Cntrlr                    5
 0   29   7   8086   27CC 1458 5006 0C03  USB 2.0 Host Cntrlr                    9
 0   31   2   8086   27C0 1458 B002 0101  IDE Cntrlr                            14
 0   31   2   8086   27DA 1458 5001 0C05  SMBUS Cntrlr                          11
 1    0   0   1002   5B63 17AF 3000 0300  Display Cntrlr                         5
 2    5   0   10EC   8167 1458 E000 0200  Network Cntrlr                         9
                                          ACPI Controller

GRUB loading.
Welcome to GRUB!

Entering rescue mode...
error: the symbol 'grub_puts' not found
grub rescue>

```

Yes its a Debian Squeeze, but IIRC Debian ~ Ubuntu (and this issue my apply to Ubuntu)

- AlphaBravo

---

### Post by Julian David Pitt on 2010-04-15
I have the same issue following a partial distribution upgrade this afternoon. I don't know I was asked to upgrade yet but it was offered so I took it. After all the files had copied over and during their installation I was asked where I wanted to install grub and chose my boot partition. When all had finished I was left with a Lucid desktop at 800 by 600. I tried to rectify this but my Nvidia card was not recognised so I rebooted which left me where I am now. Any idea what is causing it?

---

### Post by malandro95 on 2010-05-28
Did you ever get a resolution for this?

I did the 2010.04 upgrade and ended up with a grub rescue prompt.  I'm at a loss.

---

### Post by dino99 on 2010-05-28
[http://ubuntuforums.org/showthread.php?t=1476183](http://ubuntuforums.org/showthread.php?t=1476183)

---

