---
title: "Need to make a shared partition"
date: 2006-04-09
forum: General Help
---

### Post by joewhite on 2006-04-09
I want to make a shared partition for Windows and Linux. I have tried using ext2fs in Windows but it freezes when trying to copy over big files likes videos to the Windows partition. So I decided to make a fat32 partition. However Gparted tells me that I can only have 4 primary partitions. Does this mean I have to delete my second ntfs partition? (See attatched screenshot). I really can't be bothered with the backing up.

---

### Post by Ramses de Norre on 2006-04-09
What's that first partition of 1MB? You can move the ext partition and enlarge the extended, then you can make a fat partition inside the extended next to your swap partition.

---

### Post by joewhite on 2006-04-09
I'm not sure what that is, probably the Windows XP installer miscalculated. When I right click on the ext partition in GParted I don't see any options to move or resize it. Should I do this from the console?

---

### Post by Ramses de Norre on 2006-04-09
You need to unmount it first, and since it's your / partition you'll need to use knoppix or the live cd.

---

### Post by catlett on 2006-04-09
You can only have 4 primary partitions but you can have many logical partitions( I believe it goes by 4s.Every primary partition can have an extended partition that can be divided into 4 logical partitions). Just make the unallocated space a logical partition. I haven't used gparted (except when it runs on install). I use Partition Magic from within windows and it has a little wizard that runs and guides you through the partition. One section has a drop down box with the choices of primary or logical. See if gparted gives you the option, If not you can always go to CNet downloads and get a 30 day copy  of Partition Magic to do it for you.

---

### Post by joewhite on 2006-04-09
I tried making a logical drive in the free space with partition magic but after looking like it was succesfully moving the other partitions it came up with these errors. 

free inodes count wrong
ext2 superblock contains illegal information

However I chose the recommended option of installing at the very end next to the swap partition rather than in between the / and swap partitions. Will there be any difference if I put the logical partition in between / and swap?

---

### Post by joewhite on 2006-04-09
Thanks for all the sound advice. My setup now looks like this. I'm probably just being nitpicky but should I move the swap above the fat32 partition so it has faster access or will this make little difference? Also is there anyway to do this?

---

### Post by catlett on 2006-04-10
I don't know if it makes a difference or not. My guess is that the speed difference in normal use is negligable. There is something about how partitions are created that makes them like to put extended/logical partitions at the end. PM always wants my extended partitions at the end and like you when I wanted to move primaries with Operaring systems on them I encountered errors. Now I let PM do what it wants as the default and I never have problems.

---

