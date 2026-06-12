---
title: "Portable Hard drive"
date: 2006-03-01
forum: General Help
---

### Post by thexaspect on 2006-03-01
Ok guys, HUGE problem. I swapped the hard drives in my desktop and my portable hard drive enclosure, after backing everything up to the desktop hard drive. Theoretically, all of my information would be on the hard in the enclosure then, and I could then copy everything to my desktop. But now my desktop can't read the portable hard drive. It has Kubuntu 5.10 Breezy installed, with ext3fs, same as the current desktop. Neither can my laptop, in both XP and Ubuntu Breezy. At first I thought maybe it was a different filesystem, didnt have the right software, etc, but I've tried everything I can think of, and it wont let me in. Any suggestions?

---

### Post by soce_32 on 2006-03-01
Did you check the jumpers on the drive?  Do you see anything about /dev/sda when you do dmesg right after attaching the drive?  Can you fdisk the drive and check that the partitions are there?

If the drive isn't showing up at all, pull it out and check the jumper near the power plug and try setting it to master, or cable select.

---

### Post by thexaspect on 2006-03-01
I'm not home right now so I can't look at it, but it shows up in Konqueror and loads saying media:sd5 something or other not available I believe. I cant risk just formatting or anything because it has all of my files backed up on it. Worst case I can put it back into the computer I pulled it out of to get the files off some other way, but I'm trying to avoid that as it's very time consuming with my specific low profile case. The jumpers are set as the master, though.

---

