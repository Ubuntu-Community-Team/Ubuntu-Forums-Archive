---
title: "how do i delete windows mbr parition with live cd?"
date: 2009-10-16
forum: General Help
---

### Post by damnidunno on 2009-10-16
Okay i have a drive that i keep all my important files on. This way i dont have to back them up everytime i reformat, i just install windows on my 320gb hard drive, and wipe that when ever i need.

However, i used to have windows on my spare hard drive, so it created the mbr  partition on it with the bootlader and everything back then, which is still there even now.

But its causing my problems. Now it became so currupt that i cant even boot or install windows with that drive connected, nor can i even boot linux. When the hard drive is connected, it keeps wanting to boot from the mbr parition on it, which doesnt work.

I realized it was currupt last night when i kept tryin ot install unbuntu but got grub errors, then it wouldnt even let me install windows, my computer would just freeze before it got to the boot screen.

So when i take that hard drive out (its my secondary by the way) everything works fine, and iwas able to install linux.

Anywayys. I need to find a program to use on a linux live cd, that i can use to delete the mbr partition only. I cant reformat the entire drive, it has too many important files on it, and i dont have enough blank discs, or anything to back them up, or else i'd do that.

It has to work on a live cd, because i cant boot into a normal OS with the drive attached because of the bootladers in the mbr  partition or whatever.

I tried to erase all the extra partition in the ubuntu live cd paritioner, but it either doesnt seem to find the mbr partition (should only be like 100mb or less), or it doesnt erase and format it properly. so i dunno whats going on.

So anyways, does anyone know of a easy way of doing this?

thanks!

---

### Post by PrePenguin on 2009-10-16
Are you wanting to use a single OS and what is it?

---

### Post by Bucky Ball on 2009-10-16
Try getting into the BIOS and making the disk with the correct boot partition first hard drive in the boot order. Get into System->Administration->Partition Editor and delete the partitions then re-partition the drive how you want it. You will need to unmount the drive to do this (if it is mounted). In a terminal:

```
sudo umount name_of_mount_point
```For instance:

```
sudo umount my_music
```... if 'my_music' was the name of the partition to unmount. (yes, it is 'umount' in the code).

---

### Post by aesis05401 on 2009-10-16
Hello,


You may need to move the channel that the hdd is on as well.  You want your data drives to not be occupying the 0 position on your disk channels due to difficulties that can introduce.

Additionally, there should be a boot order setting of some sort in your BIOS. On my HP machines you choose a hardware 'group' ie: cdrom/harddrive, then within that group you choose the device order.  On my dell machines it is a simple boot priority list.

Either way, I don't think an MBR on a secondary hdd should be hijacking your boot unless you have a bootloader set up to look there or it is selected as the primary boot device in BIOS.

Does this help?

---

### Post by prshah on 2009-10-17
> **damnidunno said:**
> I need to find a program to use on a linux live cd, that i can use to delete the mbr partition only. 

It has to work on a live cd, 

So anyways, does anyone know of a easy way of doing this?


You can boot off any live CD, ENSURE that your hard drive is unmounted, and then give the command```
sudo dd if=/dev/zero of=/dev/sdb bs=446 count=1
``` This will wipe the MBR only. If you make a mistake with the bs (blocksize) figure, it will instantly wipe out your partition information as well. Replace /dev/sdb with your actual hard drive device. However, you do this at your own risk. You might want to wait for confirmation advice from other sources before you take this step.

This is a direct answer to your question; however, there is a much easier and safer way; use ```
sudo fdisk /dev/sdb
``` and check for partitions marked bootable (marked with a "*") and simply remove the boot flag (fdisk command "a").

As the other posts suggest, I don't believe this to be an MBR problem, unless you have the BIOS set to boot off second HDD and/or use the second HDD as the primary HDD (The order can be changed in the BIOS).

Post back if you want more details.

---

