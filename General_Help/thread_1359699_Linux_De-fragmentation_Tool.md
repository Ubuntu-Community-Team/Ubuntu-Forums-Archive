---
title: "Linux De-fragmentation Tool?"
date: 2009-12-20
forum: General Help
---

### Post by beastrace91 on 2009-12-20
Howdy All,

I maintain a fat32 partition on my system so I can easily share files between Karmic and Seven - Are there any decent tools out there I can use to defrag this partition while running Ubuntu?

Thanks in advance,
~Jeff

---

### Post by lukeiamyourfather on 2009-12-20
The safest and easiest way to go would be to defragment the disk while running Windows. Chances are though if you ever leave the system in Windows for more than a few hours it'll defragment the disk itself since Windows Vista and newer have scheduled defragmenting out of the box. Cheers!

---

### Post by Treeh on 2009-12-20
What about for non-Windows users?

---

### Post by lukeiamyourfather on 2009-12-20
> **Treeh said:**
> What about for non-Windows users?

Playing the Devil's advocate or are you serious? If you don't use Windows then you probably don't need FAT32 (or NTFS) because you'd be using ext3 or ext4.

---

### Post by Treeh on 2009-12-20
> **lukeiamyourfather said:**
> Playing the Devil's advocate or are you serious? If you don't use Windows then you probably don't need FAT32 (or NTFS) because you'd be using ext3 or ext4.

Well, going into Windows is a tad inconvenient. I have a Windows partition that I rarely use, but as a result, a NTFS drive--so maybe a little serious.

---

### Post by lukeiamyourfather on 2009-12-20
> **Treeh said:**
> Well, going into Windows is a tad inconvenient. I have a Windows partition that I rarely use, but as a result, a NTFS drive--so maybe a little serious.

As far as I know there aren't any defragmenters for FAT32 or NTFS in Linux (Google apparently doesn't know either). If anyone knows of one I guess I'd like to know out of curiosity but even still if there's anything on the disk I cared about, using the defragmenter in Windows is still the safest option.

---

### Post by dcstar on 2009-12-20
> **beastrace91 said:**
> Howdy All,

I maintain a fat32 partition on my system so I can easily share files between Karmic and Seven - Are there any decent tools out there I can use to defrag this partition while running Ubuntu?


"Sharing files" is hardly an application that needs or will benefit from de-fragmentation, so doing this is basically a TWOT (Total Waste Of Time).

---

### Post by stinger30au on 2009-12-20
why use fat32???
get windows to format the partition to ntfs

---

### Post by beastrace91 on 2009-12-20
> **stinger30au said:**
> why use fat32???
get windows to format the partition to ntfs

The ntfs drive Ubuntu uses does not play nicely with Wine - meaning I cannot play my games from a ntfs drive on both Windows & Ubuntu but fat32 works fine.

Also - yes it is getting fragmented just being used for games like this. I guess I'll just use 7 to defrag it.

Cheers,
~Jeff

---

