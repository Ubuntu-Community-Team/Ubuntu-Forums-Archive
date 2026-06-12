---
title: "dosfsck &quot;Unable to create unique name&quot;"
date: 2010-09-05
forum: General Help
---

### Post by zorblek on 2010-09-05
I have an Archos 605 media player that seems to have become corrupted, so I'm trying to run fsck on it. It mounts as a FAT32 hard drive, so I ran ```
sudo dosfsck -a
``` and this is what I got:

```
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:03/00
  Not automatically fixing this.
Unable to create unique name
```

I suspect this means I'm screwed, but I'd appreciate any additional insight from someone who knows more about dosfsck than I do.

---

### Post by Keilaron on 2010-09-25
I had that issue just now trying to get my own media player from being put into read-only mode:
```
# fsck.vfat -r -f -v /dev/sdb1
dosfsck 3.0.7 (24 Dec 2009)
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
Checking we can access the last sector of the filesystem
Boot sector contents: [... snip ...]
Cluster 429 out of range (199905107 > 1830012). Setting to EOF.
[... snip tons of these ...]
Cluster 509 out of range (207337444 > 1830012). Setting to EOF.
/Music/Games/Mario & Zelda Big Band Live/12 Theme of The DOLPHIC TOWN (NINTENDO GAMECUBE - ''SUPER MARIO SUNSHINE'').mp3
  File size is 6561796 bytes, cluster chain length is 16384 bytes.
  Truncating file to 16384 bytes.
Reclaiming unconnected clusters.
Unable to create unique name
```
Turns out that you have to run fsck with ONLY the -r option, nothing else. After the "Truncating file to 16384 bytes." line I got:
```
Reclaimed 479 unused clusters (7847936 bytes).
Free cluster summary wrong (636575 vs. really 637054)
1) Correct
2) Don't correct
? 1
Perform changes ? (y/n) y
/dev/sdb1: 6213 files, 1192957/1830011 clusters
```
(Naturally, the 1 and y were my own answers.)

EDIT: And y'know, it *did* tell you that it wouldn't automatically fix it for you. You have to use the -r option in that case.

---

### Post by zorblek on 2010-09-25
I eventually figured that out, too.

---

### Post by dcstar on 2010-09-26
> **zorblek said:**
> I eventually figured that out, too.

So you **Solved** this then? (read below).

---

### Post by Keilaron on 2011-01-30
In my case it did, so I figured in his it did too. Hopefully he or a mod can mark it as such.

---

