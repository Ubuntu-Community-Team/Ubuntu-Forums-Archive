---
title: "Lost aMule files after power outage"
date: 2010-04-12
forum: General Help
---

### Post by JohnHomos on 2010-04-12
I recently had two unexpected power outages while aMule was downloading some files.
In both cases I lost many files (more than 4 GB). Some files were even lost without a trace; both '.part' and '.met' files in the temp directory were lost.

Although this is happening with aMule I'm suspecting this is actually an Ubuntu issue, since killing aMule doesn't cause file loss.

Running fsck didn't recover anything :( and using R-linux from Windows didn't seem to return much (it did return a few file that I deleted, but not ones that I actually lost)

I'm using Ubuntu Karmic 9.10 and my disk is formated using ext3, which is a journaling system that is supposed to be resilient to those types of errors; yet I'm expriencing them quite frequently.

Needless to say, this is quite frustrating as I never experienced such file loss in Windows.
So, is this expected? Is there a way to recover my files?
And how can I prevent this from happening again?

---

### Post by lovinglinux on 2010-04-12
Use BitTorrent. EDonkey type of p2p is a thing of the past.

I experience several power outages here, including while downloading torrents, and the worst thing that ever happened was a couple of pieces missing from a file that was active during the outage. Just needed to re-check the torrent to get the missing pieces.

BTW, I all my partitions are ext4.

See [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

---

