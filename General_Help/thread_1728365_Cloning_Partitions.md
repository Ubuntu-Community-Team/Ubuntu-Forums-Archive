---
title: "Cloning Partitions"
date: 2011-04-13
forum: General Help
---

### Post by MarkVS on 2011-04-13
I have a 200GB hard drive with 3 partitions on it. The first is a small 3.5GB Windows restore partition. Second is a 174 Windows NTFS partition. Lastly is a 19GB ext4 Ubuntu partition. When I fist got Ubuntu, I had no idea that I would fall in love with it and use it all the time, so I only gave it 19 gigs of space. Now, I am always running out of room on this partition. Since Windows doesn't need all 174 gigs (only using 60GB), I thought that I would even it out a bit. Unfortunately, its not just as simple as shrinking one and growing the other. The 3.5GB was first 6.4GB, but because it never changes I shrunk it to being completely full at 3.5GB. So now I have 2.9GB free between sda1 and sda2. Now, since there is this free space, and both drives are fragmented (Windows much more that Linux, since ext4 is very resistant to it), I thought I would clone both partitions onto my external hard drive and then copy them back into new partitions with the right sizes. Here is where I have options.

1. Just copy the files over then back.
2. Clone the partitions the edit the back.

I have no experience here, and any advice how to do this would be great. Also, my Ubuntu partition has only / on it, I don't have separate partitions for anything else. If this would be a good idea (like making a /home partition), can you describe how to do this when I copy the files back?

Whatever would get the job done the best would be great.

---

### Post by danjahner on 2011-04-13
I have been successful going the easy route and shrinking/expanding partitions. If you boot from a live disk, Gparted should have no problem shrinking and expanding it as you see fit. 

Note that if you move the start of the Ubuntu partition, you will need to reinstall Grub once the partitioning is done.

---

### Post by MarkVS on 2011-04-13
Thanks for responding. If you think that that would be faster, I could always defragment with another program. I have Grub2 installed in the MBR. Would I still have to reinstall Grub in sda3 because it just points to sda3, or will I not have to? And if I do, will it save all my configuration scrips or should I copy those? Thanks.

---

### Post by danjahner on 2011-04-13
Yes, if you move the partition to the left, you need to reinstall grub. It isn't a big deal though. 

1. Boot from live disk
2. mount Ubuntu root partition 
3. sudo grub-install --root-directory=/mnt/ubuntu-partition /dev/sda
4. sudo update-grub
5. reboot

---

### Post by debd on 2011-04-13
cloning solution :clonezilla.  [http://clonezilla.org/](http://clonezilla.org/)

its a free and great tool to use for cloning partitions.

---

### Post by seawolf167 on 2011-04-14
Here is what I'd do:

[LIST]
[*]Boot into Windows, use the Windows partition editor to expand the Windows partition into the 2.9GB free space
[*]Resize the Windows partition (again with the Windows partition editor) to ~65GB (or whatever you'd like), leaving free space at the end
[*]Boot off a LiveCD, fire up GParted and resize your / (or /home, etc.) partition into the free space at the end of the Windows partition
[*]Profit?
[/LIST]
Before you start, I recommend you make an entire disk image with [Clonezilla ]("http://www.clonezilla.org")so if something goes wrong you can restore the image and try again.

If you need to reinstall GRUB, [here ]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")is a how-to

---

### Post by MarkVS on 2011-04-14
Thanks for everyone for responding. Here are the steps I took to get it done.

1. Boot from my Ubuntu 10.10 Live CD
2. Mount my 2 partitions
2. Create a 10GB partition on my external hd to copy my /home folder to.
3. Use ```
sudo cp -a /media/Ubuntu/home/* /media/Backup
``` to copy the /home folder. (I actually forgot to do this step, I realized that I had forgotten too late, during step 5.)
4. Use GParted to clone my Windows XP partition to my external hd.
5. Use GParted to move and shrink my WinXP partition and move and grow my Ubuntu one.
6. Ran the code to reinstall Grub2 on my hd:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
7. Reboot

It rebooted fine, and I'm back to normal with much more space to run with. I did the sizes at about 50/50, so its fair now. I haven't booted WinXP yet, but I don't expect any problems; I can open the partition in nautilus fine. Thanks for helping me out!

---

