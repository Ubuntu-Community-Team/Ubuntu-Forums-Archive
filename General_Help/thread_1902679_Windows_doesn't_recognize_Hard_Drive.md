---
title: "Windows doesn't recognize Hard Drive"
date: 2011-12-31
forum: General Help
---

### Post by Michalzeszen on 2011-12-31
Hi there,

After two days trying several solutions found on Windows/Linux forums, I decided to ask for help to my specific problem. Whenever I boot from my Windows 7 CD and reach the step where I have to decide where I would like to install my OS, Windows can't find any hard drive. As I've tried several solutions on the internet, and frequently faced erros between the steps, I will not tell any details concerning the tutorials I have already tried.

- My hard disk is exactly this one: ST31000528AS Barracuda 7200.12 SATA 3Gb/s 1TB

and my current partitions are these:
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x22c13b74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2046   328124415   164061185    5  Extended
/dev/sda2       328127625  1638389024   655130700    7  HPFS/NTFS/exFAT
/dev/sda4   *  1638400000  1953523119   157561560   42  SFS
/dev/sda5            2048     5859327     2928640   82  Linux swap / Solaris
/dev/sda6         5861376    35155967    14647296   83  Linux
/dev/sda7        35158016   328124415   146483200   83  Linux

```* /dev/sda2 is the place where I'd like to install Windows, but after try so many times - with my back up on hands - I would be happy even formatting the whole HD and reinstalling the whole thing, Ubuntu and Windows 7

Does anyone faced this problem already? Whats the solution?

ps.: I'm sorry for the poor grammar, I'm from Brazil.

---

### Post by Quackers on 2011-12-31
Welcome to UF :-)

I'm not 100% sure on what your problem is but I can see a couple of possibilities. The first is that sda4 is shown as an SFS partition type. This might indicate that at some time you have exceeded the maximum number of primary partitions available (which is 4 ).When this happens Windows will change the partition type to SFS, which is a dynamic disk, rather than basic. This makes installing other operating systems impossible.
I should try to format sda4 as NTFS and see if that helps.

The second point is that Windows likes to think it is the only system on the drive and therefore likes to be in the first partition on that drive. Whether this will cause a problem when installing, I'm not sure.

Try formatting sda4 to NTFS first and see if the installer will then recognise it.

---

### Post by Mark Phelps on 2011-12-31
Also, it looks like you might have five primary partitions on your drive -- in which case, you will NOT be able to convert the SFS partition to NTFS because you have exceeded the limit of four primary partitions.

You also can't combine the three Linux partitions inside an Extended partition because you already have one.

You best bet would be to erase the drive and reinstall, this time, putting ALL the Linux partitions inside a single Extended partition.  That way, you can still create a Primary partition for installing Windows.

---

