---
title: "Increasing partition size"
date: 2011-05-10
forum: General Help
---

### Post by Scunnered on 2011-05-10
I am dual booting windows 7 and Lucid and find that I have only a little over 1.6 Gb avail in Windows.  I have been attempting to increase the windows partition but it seems no matter what I try I am unable to do so.

When I view the partitions via GParted I see two items NTFS formatted, one of 100 Mb which I assume is the restore for windows the other being 25 Gb.  My ext4 partition is some 119 Gb.  

How do I say double up the NTFS to say 50 Gb. using GParted Live or the Ubuntu Live CD?

Thanking you in anticipation

---

### Post by indytim on 2011-05-10
Probably, the best course of action is to create unallocated space directly to the right of your NTFS Windows partition.  Once created, expand you Windows partition to occupy this space.

-IndyTim / DataMan

---

### Post by tredegar on 2011-05-10
You need to boot from a live CD. You cannot resize a mounted partition.
Then unmount all your HDD partitions.
Resize the ext4 partition with **gparted** in such a way that you can then grow the windows partition into the resulting free space.
Be warned: This can sometimes take hours.

---

### Post by Ghost|BTFH on 2011-05-10
The steps are as follows:

Step 1: Fire up a Live CD because you WILL NEVER BE ABLE TO UNMOUNT THE UBUNTU EXT4 PARTITION IF YOU ARE IN IT.

Step 2: Open up Gparted and get to the drive in question.

Step 3: Right click on the Ubuntu partition.  Select "Resize/Move" from the drop down list.

Step 4: In the next window that pops up, shrink its size down by dragging the LEFT SIDE over to the RIGHT until you have enough free space for what you want for Windows.  NOTE: DO NOT TAKE 99% of the drive's free space from Ubuntu unless you'd enjoy not having it boot anymore...it WILL cause issues.  Make sure it's got plenty of room to grow - I generally split the drive space evenly between two OSes when I dual boot.

Step 5: Right click on the Windows partition and select "Resize/Move" and drag the RIGHT side over to the RIGHT taking up the free space.

When you click Apply the following things will occur:

1) It will shift all the data in the Ubuntu partition over and resize it.
2) It will then grow the Windows partition to fill up the empty space left from the first action.

This can take a few hours depending on the drives, the amount of data, etc.  Don't be impatient.

When it is done, reboot.  If everything went well, you should now have a much larger Windows partition ready for whatever junk you need to throw on there (My guess is games, but then I'm bitter and cynical and think the only reason people dual boot is gaming.)

Cheers,
Ghost|BTFH

---

### Post by Scunnered on 2011-05-11
My thanks to you all for your input.  I will give this a go shortly and see if things improve.

Contrary to **Ghost|BTFH** views I only use doz for downloading audiobooks to my iPod.  I am currently having problems accessing my partners systems from Lucid so wish to add space to doz in order that I can backup her data without having either chase her round the house or throw her off the system.

---

### Post by coffeecat on 2011-05-11
@Scunnered, a couple of points. Your 100MB partition is your Windows boot partition. It will probably have the label "System". Don't be tempted to remove it otherwise Windows won't boot. I've seen threads where the OP has deleted the partition. :-s

The other thing is that once you've resized your Linux partition with Gparted in the live CD to make some space for your main Windows partition, it might be safer to use Windows' own Disk Management utility to enlarge the Windows one. Both Vista and 7 sometimes react badly to being resized by Gparted.

---

### Post by Scunnered on 2011-05-11
Many thanks **coffeecat**

I was aware that I had to keep well away from the NTFS partitions but appreciate your remark about using windows.

So far I reduced the size of my ext4 partition to free up space for doz but find that I am unable to either alter of remove the unallocated partition space that follows the NTFS working partition.

Can you advise how I can eliminate the unallocated space as any attempt to extend the NTFS fails miserably.

Many thanks

Edit:  Went into Microsoft disk management utility which showed the 32 GiB free space. Attempted to remove it but was informed that there was not enough space to do so.  It will also not let me enlarge the NTFS partition either.

Am somewhat stuck at the moment.

---

### Post by coffeecat on 2011-05-11
I wonder if your ext4 partition was a logical one so that the freed space is now in the extended partition. Which would mean that Windows - which is on a primary partition - would not be able to extend into it. If I'm right, you'd also need to shrink the extended partition.

Post a screenshot of the Gparted window and also the output of:

```
sudo fdisk -lu
```Be careful how you interpret the Windows Disk Management window. It gets confused with logical partitions formatted with Linux filesystems and calls them primary. That's **really** confused! :) That's why a screenshot of Gparted is to be preferred even though you will be using Windows Disk Management to resize the NTFS partition.

---

### Post by Scunnered on 2011-05-11
Thanks again coffeecat

The requested output is 

""Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c199f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *      206848    52279295    26036224    7  HPFS/NTFS
/dev/sda3        52281342   312580095   130149377    5  Extended
/dev/sda5       120680280   301909544    90614632+  83  Linux
/dev/sda6       301924352   312580095     5327872   82  Linux swap / Solaris""

When I was messing about with an old system I was informed that if I deleted Ubuntu from the system when I reinstalled it Grub would automatically revert to showing Windows.

Would this be an easier proposition that exterminating partitions?

---

### Post by coffeecat on 2011-05-11
> **Scunnered said:**
> When I was messing about with an old system I was informed that if I deleted Ubuntu from the system when I reinstalled it Grub would automatically revert to showing Windows.

That's more or less true. If you have a Windows/Ubuntu dual-boot and you delete the Ubuntu root partition, you get a grub error when you try to boot up. The grub code in the mbr looks for the (now) non-existent bits of itself in /boot/grub of the Ubuntu root partition, goes "Uh-oh!" and throws out an error message. If you re-install Ubuntu, grub gets automatically installed and will detect the presence of Windows and will set up an entry in the new grub menu for it.

> **Scunnered said:**
> Would this be an easier proposition that exterminating partitions?

Not really, because you are not exterminating partitions, simply shuffling them about a bit. :)

Anyway, to your present situation...

My guess was correct - the 32.6GiB unallocated space is within the extended partition, sda3, which is why you cannot yet enlarge the Windows sda2 partition to use it. If you look at your Gparted screenshot, this is shown fairly clearly.

The answer is fairly straightforward. Boot up the live CD and open Gparted. You'll see that both the extended partition and the sda6 swap partition are locked. Right-click on sda6 and choose "swapoff". This will unlock the extended partition. You can now shrink it by moving its start point up to the beginning of sda5. Ghost|BTFH gives a nice description of how to do that, but shrink the sda3 extended partition.

Once the 32.6GiB space is outside the extended partition, you should be able to use the Windows Disk Utility to expand the Windows C: partition.

Warning! :) As always, backup everything you can before messing with partitions. Things go wrong only rarely, but when they do they tend to go wrong spectacularly.

Good luck!

---

### Post by Scunnered on 2011-05-11
Woe is me. Despite removing the lock as instructed no matter what I do nothing will change the unallocated 32 GiB item. Right clicking on the item will not offer any options other than information.

I was using the LIVE CD with which I installed Lucid. Gave up on that and downloaded the current GParted LIVE CD - still nothing.

I can if I wish delete the NTFS partition or the Ubuntu one but no matter what I try I am totally unable to work with the unallocated space.  I tried re-sizing the NTFS one but when asked to effect the change I was given an error message.

Other than shooting myself where do I go from here?

---

### Post by coffeecat on 2011-05-11
> **Scunnered said:**
> Woe is me. Despite removing the lock as instructed no matter what I do nothing will change the unallocated 32 GiB item. Right clicking on the item will not offer any options other than information.

No, no. Right-click on the sda3 extended partition and shrink that. You can do absolutely nothing with the unallocated space until you shrink the extended partition. Don't right-click on the line that says "unallocated". Right-click on the line that says "/dev/sda3".

---

### Post by Scunnered on 2011-05-11
> **coffeecat said:**
> Things go wrong only rarely, but when they do they tend to go wrong spectacularly.

I had visions when I looked at your remark that this was going to be one of these times.  However having revisited GParted from the Live CD and trying to get sda3 to re-size it appeared that nothing was happening.  The progress bar swiped once over and back and claimed that all operations successfully completed.  As there was no obvious change in view after a couple of more attempts I took that as read.

Re-booted and went into Win7 only to find that I could now work with the disk utility.  Returned to Lucid and low and behold alls well that ends well.

My sincere thanks for all your kind assistance and patience with me.

---

### Post by coffeecat on 2011-05-11
I'm glad it's worked.

Yes, resizing an extended partition can be disconcertingly swift. Resizing a primary or logical partition with a filesystem on it can take ages because the filesystem needs resizing as well as the partition. There's not much to do when an extended partition is resized.

Good luck! :)

---

### Post by Scunnered on 2011-05-11
Again my thanks coffeecat.

It was the speed that totally confused me. I had reduced the Ubuntu partition and even when I had backed up most of the stuff to an external drive it took over 3 hours to adjust. When the next option was in the blink of an eye I could not believe it and kept looking for more.

Linux is confusing but with the help of the forum things get done and I learn more and more.  Beats being told time and time again that you can't do this or that because M$ says so.

---

