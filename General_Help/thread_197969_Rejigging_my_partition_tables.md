---
title: "Rejigging my partition tables"
date: 2006-06-16
forum: General Help
---

### Post by anti-dan on 2006-06-16
I installed my dual boot Xubuntu/Windows XP system thinking that captive-ntfs would be fine and dandy for realtime sharing of my files, so I could use bittorrent, watch movies and the like from either system and they would both be in sync. I was wrong :( captive-ntfs is so slow it can hardly put the information across fast enough for xine to serve it to the screen! So I've decided to make a new fat32 partition which is shared by both Xubuntu and XP but I've run into a couple of problems...

I've resized the ntfs to a fraction of itself fine using gparted, then run XP so that it does its own chkdisk thing to keep everything in order, and it's all great, but I'm now left with *two* big pieces of empty space rather than one cohesive lump to make my new partition in. gparted *says* it can move partitions, but I've not seen any evidence of this, it just offers me resizing. Qtparted has been no help either!

There's got to be a way to do this sort of thing. I remember doing it in partition magic many years ago, but that's not really an option at the moment, so any help or pointers to alternative programmes would be greatly appreciated.

Cheers!

---

### Post by gerbman on 2006-06-16
[QUOTE=anti-dan]I installed my dual boot Xubuntu/Windows XP system thinking that captive-ntfs would be fine and dandy for realtime sharing of my files, so I could use bittorrent, watch movies and the like from either system and they would both be in sync. I was wrong :( captive-ntfs is so slow it can hardly put the information across fast enough for xine to serve it to the screen! So I've decided to make a new fat32 partition which is shared by both Xubuntu and XP but I've run into a couple of problems...

I've resized the ntfs to a fraction of itself fine using gparted, then run XP so that it does its own chkdisk thing to keep everything in order, and it's all great, but I'm now left with *two* big pieces of empty space rather than one cohesive lump to make my new partition in. gparted *says* it can move partitions, but I've not seen any evidence of this, it just offers me resizing. Qtparted has been no help either!

There's got to be a way to do this sort of thing. I remember doing it in partition magic many years ago, but that's not really an option at the moment, so any help or pointers to alternative programmes would be greatly appreciated.

Cheers![/QUOTE]From the looks of things, GParted cannot move NTFS partitions. You'll need to do this with Partition Magic or something similar. To see what GParted can do, go to GParted->File Systems. The little curved arrow _should_ be an X indicating that GParted cannot perform that operation.

---

