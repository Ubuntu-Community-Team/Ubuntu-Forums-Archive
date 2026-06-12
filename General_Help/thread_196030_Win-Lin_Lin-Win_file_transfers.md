---
title: "Win-Lin Lin-Win file transfers"
date: 2006-06-13
forum: General Help
---

### Post by Fred Doolie on 2006-06-13
For what it's worth, here's a noobee's adventure into two-way file transfers addressed to other noobees. Hopefully some experts will clarify the parts that are not phrased correctly.

I (like most of you I'd guess) wanted to transfer files back and forth between Ubuntu and Winblows while I get my system set up and am not quite ready to delete Winslows off my system. Here's the three ways I tried and what happened. I set up a "Common" partiton to transfer files since I am NOT dumb enough to allow either OS to write into the other's partiton.

1) Common as NTFS:
Windows can work with it fine.
Ubuntu can not.
Can only copy to Ubuntu partition; not move.
Files are messed up permission-wise in Ubuntu. The copied files can be read but not edited, deleted, renamed.....nothing. They have a lock on the icon.
No good.

2)Common as Ext3 with Ext3driver installed in Windows so Ext3 is a native format:
What a mess.
Files can be read/written/whatever with Ubuntu.
Files can be read/written/whatever with Windows.
Ubuntu can access the files that Win wrote....sometimes.
Windows can access the files that Ubuntu wrote.....sometimes.
Permission problems as with using NTFS.
Filenames get messed up. A file saved  as "My Wedding" in Ubuntu will show up as "My?W?edd!?!ingy737376//6234" (or something like that) in Windows and of course not be accessable. It works fine in Ubuntu though.

I'm SO glad I didn't access my Ubuntu partiton from the Windows side.

3) Common as FAT32:
No problems. That's the way to do it. FAT32 doesn't know about permissions.


Experts, care to explain why #1 and# 2 do that?

---

### Post by mindwarp on 2006-06-13
#1. NTFS write support isn't known as being featureful or reliable.  That very reason is why you wanted a common partition in the first place

#2. Ext3 suffers from the same "ghetto effect" as #1

#3.  Fat32 has it's roots in the FAT filesystem which dates back to 1977.  Almost 30 years gives a bit to being able to support it properly.

---

