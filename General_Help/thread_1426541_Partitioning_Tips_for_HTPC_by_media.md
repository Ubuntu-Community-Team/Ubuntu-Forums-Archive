---
title: "Partitioning Tips for HTPC by media?"
date: 2010-03-10
forum: General Help
---

### Post by fluffywarthog on 2010-03-10
Intermediate user about to buy a HTPC for frontend-only use, and I've figured out most of the hardware hurdles, but I'm still hung up on how to partition my hard drives. Using:

WD Blue 160GB SATA
WD Black 1TB SATA

No RAID, nothing fancy, just the first small drive for Myth installation, different player installations, download cache, and local files. The Tera drive will be for media storage. I'll be collecting a bunch of media from my jumble of storage devices, and sorting it onto partitions to keep things clean. Probably using this much of each:

5 GB installation for Myth, extra room for non-default media programs
4 GB Swap
152 GB for downloads and local files
----
3 GB of photos
100 GB of audio files
Remainder 800+ GB for video files

Unfortunately, I don't have enough experience testing different filesystems, so I'm at a bit of a loss here. I can make the partitions fine, but a bit confused as to the advantages of one system over the other. I assume I should keep the media programs on the smaller drive (lower speed, but it's hard to find a high-speed drive with less than 500GB to warrant spending that much), but I don't want to have every different partition mounted and scanned unless I need it. 

Right now I'm looking at ext3 on almost everything, but I'm not sure what to do with the video partition. Getting NTFS for bigger files has turned out to be hell on my sanity, but I've never tried using XFS, and have heard about fsdisk problems and defrag issues.

Any advice would be very helpful. Thanks.

---

### Post by egalvan on 2010-03-10
Personally, me, myself and I all think that stability trumps speed when it comes to data *storage*.
So I use ext3 due to it`s long and stable history.
And I mirror the drive for backup,
and keep an extra backup somewhere else, (if the data is valuable enough but that is your call)

I use RAM to mitigate *slow* hard drives (seriously, SATA3 slow?)...
8GB of RAM...
No swapping for me!

Keep in mind that media is watched/listened to at 1x speed...
so what if the drive is *slow*?
Is any drive/interface/file system these days so slow that it can´t serve video fast enough to watch it?
Or serve music so slow that it can´t be listened to?

Other concurrent processes can inturrupt media streams and cause problems, but that is not related to drive speeds...

Keep the media player clean, no extra procceses running that slow things down... keep it media-related.

My own media machine does *nothing but* media...
Watch video and listen to audio... nothing else.
It has a small, fast hard drive for local storage,
and a gigabit LAN connection to the rest of the stuff.
(I`m experimenting with having only LAN, no local hard drive, 
to reduce noise and heat. Success so far)

I have other machines to do the rest of the stuff
(encode, decode, re-code, copy, etc)
and never suffer stutters or stops.

---

