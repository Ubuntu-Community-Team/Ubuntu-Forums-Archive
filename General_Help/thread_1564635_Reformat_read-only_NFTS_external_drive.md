---
title: "Reformat read-only NFTS external drive"
date: 2010-08-30
forum: General Help
---

### Post by bostonaholic on 2010-08-30
**Short version:**
How do I reformat an external hard-drive (read-only, NFTS) so that I can rw to it.

**Long version:**
I had a self-built Ubuntu *desktop* that is now dead.  I have pulled out the hard-drives and have bought one of the connector's to convert the SATA cable to USB so I can put the data on my Mac.  Unfortunately, my Mac is not able to read the hard-drive for some reason...  So, I've decided to boot my old Ubuntu *laptop* to pull the files from the SATA drive to an external drive then hopefully connect that external drive to transfer the files to the Mac.  The external drive is currently formatted as NFTS and I'm unable to reformat it with gparted--I'm guessing that's because it's read-only mode...?

This might help

Ubuntu ext3 SATA  -> connector -> Mac OS X

or

Ubuntu ext3 SATA -> connector -> Ubuntu ext3 laptop -> external NFTS HD -> Mac OS X

Any suggestions?

---

### Post by Autodidact on 2010-08-30
Did you unmount the volume first?

Formatting problems like these can often be solved by removing all partitions. Then create one new partition and format it as desired.

You are using Mac by default? 

Then do the following in OSX:
- Connect HD
- Open Disk Utility
- Select the disk (left side)
- Go to the partition tab
- Set volume scheme to 1 partition 
- Type name
- Select desired format
- Apply

---

### Post by bostonaholic on 2010-08-30
> **Autodidact said:**
> Did you unmount the volume first?

Formatting problems like these can often be solved by removing all partitions. Then create one new partition and format it as desired.

You are using Mac by default? 

Then do the following in OSX:
- Connect HD
- Open Disk Utility
- Select the disk (left side)
- Go to the partition tab
- Set volume scheme to 1 partition 
- Type name
- Select desired format
- Apply

Damn, never thought of reformatting the drive with my Mac...  That worked perfectly (although I had to format it as FAT so Ubuntu could rw to it.

Thanks.

---

### Post by Autodidact on 2010-08-30
Great it worked!

Btw, now you should be able to format it to any (native) file system using gparted.

---

