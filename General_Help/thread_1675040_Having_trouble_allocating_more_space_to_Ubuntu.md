---
title: "Having trouble allocating more space to Ubuntu"
date: 2011-01-24
forum: General Help
---

### Post by TheFreakster on 2011-01-24
I do apologize if this has been asked before. I've searched through numerous similar threads, but can't find the exact solution I need.

I had Windows 7 on a single partition until I wanted to try out Ubuntu a week ago (I'm loving it so far). I used the Ubuntu installation disk to reduce Windows 7 partition and create the Ubuntu one. I just ran out of space and would like to allocate more by taking more away from Windows 7. I have two screenshots attached. The first shows how it is now, and the second shows what happens after I lower the size of Windows 7, thus creating unallocated space. I am then not able to resize Ubuntu into the unallocated space.

Can anyone help me out with this please? And of course, I'm running GParted off of the Ubuntu cd, so the drives aren't mounted.

---

### Post by Smart Viking on 2011-01-24
Hello, you cannot resize the linux partition while you are booting from it. You must run the live CD, and rezise it from there.

---

### Post by TheFreakster on 2011-01-24
I booted from the Ubuntu CD I used to install the system. Is that not the live CD? I thought if I booted from this CD it won't mount the partition?

Thanks.

---

### Post by Krytarik on 2011-01-24
You have to resize the "Extended Partition" (sda2) before you can resize the Linux partition. And that is only possible, if you unmount all partition in it, thus disable the "Swap" partition (sda6). Right-click at it and choose "swapoff" or similar. After that you can proceed.

---

### Post by Quackers on 2011-01-24
Firstly, you should use Windows disk management to shrink the Windows partition (after defragmenting it!). W7 can be very finicky about it. I would make sure that Windows still boots ok. You could have chopped some data from it and it may want a chkdsk running.
If that checks out ok, you should then boot from the live cd and use gparted. The first thing to do is right-click on the swap partition and select "swapoff".
Then, as /dev/sda5 is a logical partition within /dev/sda2 (an extended partition) you would first need to extend /dev/sda2 into the unallocated space. Click the green arrow in the toolbar to apply the change.
Then you can extend /dev/sda5 to fill the resized /dev/sda2. Click the green arrow again to apply.
When that's finished you can right-click on the swap partition and select "swapon" and reboot.
Once rebooted the size of the file system may be reported incorrectly. If it is, have a look at this thread
[http://ubuntuforums.org/showthread.php?t=1242394&highlight=resize2fs](http://ubuntuforums.org/showthread.php?t=1242394&highlight=resize2fs)

---

### Post by Krytarik on 2011-01-24
+1 for Windows tool to resize its partition, haven't thought of that

@Quackers: Is it really necessary to do "swapon", if you reboot after this anyway?

---

### Post by Quackers on 2011-01-24
> **Krytarik said:**
> +1 for Windows tool to resize its partition, haven't thought of that

@Quackers: Is it really necessary to do "swapon", if you reboot after this anyway?

I wouldn't have thought so :-) I'm probably being a bit too careful there, but it only takes a second or two :-)

---

### Post by armyofgayunicorns on 2011-01-25
notice that there is only one green box surrounding the windows partition. all you need to do to shrink that partition is to drag the far right edge of the green box to the left, ensuring you are leaving enough free space for windows to still work.
around your linux partition there is a light blue box, then a dark blue box around the ubuntu partition and a red box around the swap partition.
after creating the unallocated space, you need to drag the outer, light blue box to the left, then press apply.
after this, you will now have unallocated space within the light blue box.
you then need to drag the edge of the dark blue box to the left, filling the unallocated space.
this is the point of the process that will take the longest time, as each previous step has only dealt with changing the formatting of empty space, at this point it is now moving data from one part of your hard drive to another. 
it shouldn't matter whether swap is on or off, this is only important if you want to move your swap partition or change the size of it.

---

### Post by TheFreakster on 2011-01-27
> **Krytarik said:**
> You have to resize the "Extended Partition" (sda2) before you can resize the Linux partition. And that is only possible, if you unmount all partition in it, thus disable the "Swap" partition (sda6). Right-click at it and choose "swapoff" or similar. After that you can proceed.

Thanks everyone for your advice! The swapoff thing that Krytarik mentioned was the key to my troubles. Thanks!

---

