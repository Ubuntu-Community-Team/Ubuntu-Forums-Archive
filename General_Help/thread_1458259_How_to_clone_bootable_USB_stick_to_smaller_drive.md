---
title: "How to clone bootable USB stick to smaller drive"
date: 2010-04-19
forum: General Help
---

### Post by seangee on 2010-04-19
Today I wanted to back up my 4Gb boot drive and the new drive I had was slightly smaller. Couldn't find any info on here and precious little on the internet but I have previously used this technique to clone an 8Gb disk onto a 4Gb one.  Since I have gained a lot of useful info from this forum over the years its probably time I contributed something :).

I used my netbook but this would work equally well from a live CD. Note the disk has to be unmounted so you can't use the live system.

Firstly your USB stick probably has 2 partitions one for "/" and one for swap. The first step is to reduce the "/" partition on the source drive to a size smaller than your target drive. I used gparted for this.

Next create a partition on your target drive that is the same size or bigger than your newly shrunken partition. I formatted this although I'm not sure this is neccessary. Personally I just used the whole drive and used a file on a hard disk as swap.

Next you have to use dd to copy the partition. Please note that dd is a potentially dangerous tool so please do some research on this and be very careful to specify the correct source and destination. (Your research will give you the correct syntax so I won't). What is important is that you are copying the partition not the drive. So your source would be /dev/sdx1 and target /dev/sdy1 (you will need to find your own values for x&y).  Once again be very careful that you get these the right way around or you will destroy your souce disk. Even better do it in two stages - copy your source to a file and then the file to the target.

Now you have a replica of your original disk but it is not bootable. If you are planning to use a swap partition you may as well create it now. Remember you will probably have to change /etc/fstab to read the new swap - at least on my system this was referenced by UUID. No need to change anything for the replicated partition as the UUID came over with everything else.

Finally you need to install grub on your newly created disk. I set the bootable flag in gparted (again not sure if this is neccessary). I used [this reference:]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") 

Insert your new disk and boot your (old) system from it.
[ ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by dcstar on 2010-04-20
> **seangee said:**
> Today I wanted to back up my 4Gb boot drive and the new drive I had was slightly smaller. Couldn't find any info on here and precious little on the internet but I have previously used this technique to clone an 8Gb disk onto a 4Gb one.  Since I have gained a lot of useful info from this forum over the years its probably time I contributed something :).

I used my netbook but this would work equally well from a live CD. Note the disk has to be unmounted so you can't use the live system.

Firstly your USB stick probably has 2 partitions one for "/" and one for swap. The first step is to reduce the "/" partition on the source drive to a size smaller than your target drive. I used gparted for this.
.........

And gparted will also allow you to "Copy" and "Paste" any partition you like - provided there is enough space - so there is no need whatsoever to manually use dd commands.

---

### Post by Pyrosopher on 2011-01-22
I created a compressed image of my usb drive as a backup. It has multiple partitions so dd is perfect for copying the MBR info, I can just go and have a cup of tea while it puts everything back. However, I have a concern. 

I just tried to reconstitute the information on another drive - same brand, same size. However I get an error saying the disk was full. The report said that one fewer records were copied than were on the original. Should I be concerned? Aren't the last records going to be empty? The filesystem on the last partition is EXT4. I set bs=4096 in case that is important to know.

Thanks for the advice.

---

