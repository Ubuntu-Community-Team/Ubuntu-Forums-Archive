---
title: "Trouble Partitioning Disk (qtparted)"
date: 2006-02-11
forum: General Help
---

### Post by jeff-- on 2006-02-11
Hey everybody.  I'm trying to divide my SATA 186 gb hdd into 3 partitions, 2 ext3's for Ubuntu only and 1 fat32 so I can use it for windows and ubuntu.  I'm using QTPartEd, and I delete the current partition after getting anything important off of it, and then divide it up like I want.  But when I say commit, it says it is complete, but then under that has an error [color=red]There was a problem with mkfs.ext3.[/color]  Then it just has the windows fat32 partition and the rest of the drive is unpartitioned.

When I say commit it says make sure all drives are unmounted, and I didn't have any linux partitions of this drive before, it was all for windows, so I don't know why I'm getting an error.  Thanks for any help in advance :)

---

### Post by Pausanias on 2006-02-12
Are you running qtparted from a live cd or from ubuntu itself?

---

### Post by cotcot on 2006-02-12
I had the same. I then deleted the partition with the mkfs error, rebooted the live CD and tried again; this time with succes.

---

### Post by jeff-- on 2006-02-12
No, I'm not running a live CD.  Ubuntu is installed.

---

