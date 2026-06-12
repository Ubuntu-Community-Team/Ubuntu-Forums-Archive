---
title: "Pictures on XD card disappeared"
date: 2009-07-31
forum: General Help
---

### Post by Inane_Asylum on 2009-07-31
I was looking through the pictures on my camera when I got a "picture error" and "card error" message.  I plugged it into my card reader and when it opens up in the file browser, it doesn't show any files, but says "0 items, Free space: 340.7 MB" even though it is a 512 MB card, so I know there's something on it.  Bringing it up in the terminal shows ```
andrew@Vault-13:/dev/disk$ ls -a
.  ..  by-id  by-path  by-uuid
andrew@Vault-13:/dev/disk$ cd by-id
andrew@Vault-13:/dev/disk/by-id$ ls
ata-Maxtor_6Y250M0_Y646E4LE        ata-Maxtor_6Y250M0_Y646E4LE-part5  scsi-1ATA_Maxtor_6Y250M0_Y646E4LE-part1  scsi-1ATA_Maxtor_6Y250M0_Y646E4LE-part6
ata-Maxtor_6Y250M0_Y646E4LE-part1  ata-Maxtor_6Y250M0_Y646E4LE-part6  scsi-1ATA_Maxtor_6Y250M0_Y646E4LE-part2  usb-Generic-_Multi-Card_20060413092100000-0:0
ata-Maxtor_6Y250M0_Y646E4LE-part2  scsi-1ATA_Maxtor_6Y250M0_Y646E4LE  scsi-1ATA_Maxtor_6Y250M0_Y646E4LE-part5  usb-Generic-_Multi-Card_20060413092100000-0:0-part1
andrew@Vault-13:/dev/disk/by-id$ cd ..
andrew@Vault-13:/dev/disk$ cd by-path
andrew@Vault-13:/dev/disk/by-path$ ls
pci-0000:00:0b.1-usb-0:3:1.0-scsi-0:0:0:0        pci-0000:00:0d.0-scsi-0:0:0:0  pci-0000:00:0e.0-scsi-0:0:0:0-part1  pci-0000:00:0e.0-scsi-0:0:0:0-part5
pci-0000:00:0b.1-usb-0:3:1.0-scsi-0:0:0:0-part1  pci-0000:00:0e.0-scsi-0:0:0:0  pci-0000:00:0e.0-scsi-0:0:0:0-part2  pci-0000:00:0e.0-scsi-0:0:0:0-part6
andrew@Vault-13:/dev/disk/by-path$ ls -a
.   pci-0000:00:0b.1-usb-0:3:1.0-scsi-0:0:0:0        pci-0000:00:0d.0-scsi-0:0:0:0  pci-0000:00:0e.0-scsi-0:0:0:0-part1  pci-0000:00:0e.0-scsi-0:0:0:0-part5
..  pci-0000:00:0b.1-usb-0:3:1.0-scsi-0:0:0:0-part1  pci-0000:00:0e.0-scsi-0:0:0:0  pci-0000:00:0e.0-scsi-0:0:0:0-part2  pci-0000:00:0e.0-scsi-0:0:0:0-part6
andrew@Vault-13:/dev/disk/by-path$
```

Any clue what happened or if there's any hope of getting my pictures back?

---

### Post by egalvan on 2009-07-31
First, most manufacurer web sites have software that will help recover lost photos.
This is a common problem.

They are almost always MS-Windows versions, though.

Second, photorec

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

is a good program that recovers files.


PartedMagic is a good mini-disro that has photorec included...


ErnestG

Countdown: six to go
[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by Inane_Asylum on 2009-07-31
Thanks.  After removing and re-inserting the card, I got the following:

```
andrew@Vault-13:/media/disk$ ls -a
.             FSCK0037.REC  FSCK0076.REC  FSCK0115.REC  FSCK0154.REC
..            FSCK0038.REC  FSCK0077.REC  FSCK0116.REC  FSCK0155.REC
FSCK0000.REC  FSCK0039.REC  FSCK0078.REC  FSCK0117.REC  FSCK0156.REC
FSCK0001.REC  FSCK0040.REC  FSCK0079.REC  FSCK0118.REC  FSCK0157.REC
FSCK0002.REC  FSCK0041.REC  FSCK0080.REC  FSCK0119.REC  FSCK0158.REC
FSCK0003.REC  FSCK0042.REC  FSCK0081.REC  FSCK0120.REC  FSCK0159.REC
FSCK0004.REC  FSCK0043.REC  FSCK0082.REC  FSCK0121.REC  FSCK0160.REC
FSCK0005.REC  FSCK0044.REC  FSCK0083.REC  FSCK0122.REC  FSCK0161.REC
FSCK0006.REC  FSCK0045.REC  FSCK0084.REC  FSCK0123.REC  FSCK0162.REC
FSCK0007.REC  FSCK0046.REC  FSCK0085.REC  FSCK0124.REC  FSCK0163.REC
FSCK0008.REC  FSCK0047.REC  FSCK0086.REC  FSCK0125.REC  FSCK0164.REC
FSCK0009.REC  FSCK0048.REC  FSCK0087.REC  FSCK0126.REC  FSCK0165.REC
FSCK0010.REC  FSCK0049.REC  FSCK0088.REC  FSCK0127.REC  FSCK0166.REC
FSCK0011.REC  FSCK0050.REC  FSCK0089.REC  FSCK0128.REC  FSCK0167.REC
FSCK0012.REC  FSCK0051.REC  FSCK0090.REC  FSCK0129.REC  FSCK0168.REC
FSCK0013.REC  FSCK0052.REC  FSCK0091.REC  FSCK0130.REC  FSCK0169.REC
FSCK0014.REC  FSCK0053.REC  FSCK0092.REC  FSCK0131.REC  FSCK0170.REC
FSCK0015.REC  FSCK0054.REC  FSCK0093.REC  FSCK0132.REC  FSCK0171.REC
FSCK0016.REC  FSCK0055.REC  FSCK0094.REC  FSCK0133.REC  FSCK0172.REC
FSCK0017.REC  FSCK0056.REC  FSCK0095.REC  FSCK0134.REC  FSCK0173.REC
FSCK0018.REC  FSCK0057.REC  FSCK0096.REC  FSCK0135.REC  FSCK0174.REC
FSCK0019.REC  FSCK0058.REC  FSCK0097.REC  FSCK0136.REC  FSCK0175.REC
FSCK0020.REC  FSCK0059.REC  FSCK0098.REC  FSCK0137.REC  FSCK0176.REC
FSCK0021.REC  FSCK0060.REC  FSCK0099.REC  FSCK0138.REC  FSCK0177.REC
FSCK0022.REC  FSCK0061.REC  FSCK0100.REC  FSCK0139.REC  FSCK0178.REC
FSCK0023.REC  FSCK0062.REC  FSCK0101.REC  FSCK0140.REC  FSCK0179.REC
FSCK0024.REC  FSCK0063.REC  FSCK0102.REC  FSCK0141.REC  FSCK0180.REC
FSCK0025.REC  FSCK0064.REC  FSCK0103.REC  FSCK0142.REC  FSCK0181.REC
FSCK0026.REC  FSCK0065.REC  FSCK0104.REC  FSCK0143.REC  FSCK0182.REC
FSCK0027.REC  FSCK0066.REC  FSCK0105.REC  FSCK0144.REC  FSCK0183.REC
FSCK0028.REC  FSCK0067.REC  FSCK0106.REC  FSCK0145.REC  FSCK0184.REC
FSCK0029.REC  FSCK0068.REC  FSCK0107.REC  FSCK0146.REC  FSCK0185.REC
FSCK0030.REC  FSCK0069.REC  FSCK0108.REC  FSCK0147.REC  FSCK0186.REC
FSCK0031.REC  FSCK0070.REC  FSCK0109.REC  FSCK0148.REC  FSCK0187.REC
FSCK0032.REC  FSCK0071.REC  FSCK0110.REC  FSCK0149.REC  FSCK0188.REC
FSCK0033.REC  FSCK0072.REC  FSCK0111.REC  FSCK0150.REC  FSCK0189.REC
FSCK0034.REC  FSCK0073.REC  FSCK0112.REC  FSCK0151.REC
FSCK0035.REC  FSCK0074.REC  FSCK0113.REC  FSCK0152.REC
FSCK0036.REC  FSCK0075.REC  FSCK0114.REC  FSCK0153.REC
andrew@Vault-13:/media/disk$ 
```

They work in the picture viewer, too.

I also realized I was going to /dev/disk instead of /media/disk...

***insert facepalm here***

I've never seen .REC files before, and they won't open in F-Spot, so...something else to research...

---

