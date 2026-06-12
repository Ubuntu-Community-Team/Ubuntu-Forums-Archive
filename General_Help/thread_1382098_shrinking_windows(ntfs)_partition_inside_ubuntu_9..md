---
title: "shrinking windows(ntfs) partition inside ubuntu 9.10"
date: 2010-01-15
forum: General Help
---

### Post by drink_stir on 2010-01-15
ok. im trying to shrink my vista partition with gparted inside ubuntu. from what ive read they dont explain my exact problem so here goes.

I run gparted (and yes i have ntfsprogs) but when i select the ntfs partition and select move/resize it brings up free space preceding... new size... and free space following.

so when i input the new size the resize/move button greys out and when i change the freespace following it just puts back my original new size and back and forth.

from what i have read i need to run the gparted livecd and go from there. is this true?

i know how to do it with diskpart in windows, but i would like to learn how to in ubuntu and eventually get rid of windows.

my system is 64-bit. idk if that really matters. but if it does u now know.
[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by Mark Phelps on 2010-01-15
Quit doing what you're trying to do -- unless you want to ensure that the NTFS partition is corrupted and rendered unusable.

The proper way to shrink a Vista partition, which has been documented LOTS of times in this forum, is to boot into Vista and use the Disk Management utility.

If it won't shrink the amount you want, try turning off hibernation and removing that file, reboot, and try again.  If it still doesn't shrink the amount you want -- leave it alone! Trying to force it through GParted is going to corrupt your Vista partition and render the OS unbootable.

---

### Post by nexoncore on 2010-01-15
I had a similar problem to that, you will most likely find that the windows method's dont work either. The issue I had was the paging file was located near the end of the partition, which if thats the case you cant actually resize at all. The only solution is to backup your stuff, format the partition, resize and reinstall windows.

---

### Post by drink_stir on 2010-01-15
thanks for the replies. i was just wondering if i could do it from ubuntu. guess not. and another question i have is when i shrink the vista partition wont i have to move the linux partition and extend it? and wont that require a livecd?

---

### Post by Leppie on 2010-01-15
> **drink_stir said:**
> thanks for the replies. i was just wondering if i could do it from ubuntu. guess not. and another question i have is when i shrink the vista partition wont i have to move the linux partition and extend it?
depends on what you want to do with the free space and how much experience you have in linux. resizing the ubuntu system partition does not consist of only resizing the partition. you will have to change some settings (like fstab, update grub configuration).
but you can easily add another mount point for another partition to use as storage.

have a look at this page: [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by drink_stir on 2010-01-16
im really not that versed in linux. but i have decided to just do away with vista altogether. and learn everything i can. it seems to be more of a pain to have both especially beings since i dual booted i havent used windows at all. if i need anything from windows i can always just use a virtual machine. im learning. and i hope this thread helps someone who has the same questions i did. thanks for the replies.

---

