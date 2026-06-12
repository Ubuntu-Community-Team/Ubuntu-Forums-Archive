---
title: "GParted confusion (w/ pics)"
date: 2010-03-16
forum: General Help
---

### Post by jamesofthedead on 2010-03-16
I have a messed up system, or so I think. I have all sorts of partition issues that I just don't understand. I may have installed Ubuntu multipe times (GRUB show 5+ copys) along side my copy of W7. GParted show two Unused partition spaces, one massive on that it cant read completely (ntfs), a LinuxSwap, something called (ext4) and something called (extended).

What is going on? I recently deleted a virtual machine, but it looked like this even before this. How can I allocate all of my space only to W7 and one Ubuntu OS?

Pic of GParted is attached... im sort of a beginner, and beleive myself to be in over my head.

---

### Post by 2hot6ft2 on 2010-03-16
To fix all but the little 1MB of unallocated space at the beginning you first have to choose what you want to do with the 41.5GB large unallocated space between win 7 and ubuntu.
Do you want it to be part of win 7, part of ubuntu or another partition all together?

P.S. The ext4 is your ubuntu.

---

### Post by 2hot6ft2 on 2010-03-16
> **jamesofthedead said:**
> I may have installed Ubuntu multipe times (GRUB show 5+ copys) along side my copy of W7.
Those are kernels not multiple installations of Ubuntu, and it is recommended to keep the 2 most current kernels (those with the highest numbers) that way if something doesn't work right with the newest one you can still boot to the last known working one.

Below is what you would do if the 2 newest kernels were 2.6.31-20 and 2.6.31-19 which would be the ones at the top of the grub list.
Keeping in mind that there is a Recovery Mode for each kernel so those would be the top 4 listed.

To remove the others go to synaptic
System > Administration > Synaptic Package Manager
and search for
> linux-image-2.6.31
and
linux-headers-2.6.31
mark the ones with the lowest numbers that are like 2.6.31-?? for complete removal.

For each kernel there are 3 files that are needed. like below.
These are needed for kernel 2.6.31-20:
> linux-headers-2.6.31-20
linux-headers-2.6.31-20-generic
linux-image-2.6.31-20-generic
and for kernel 2.6.31-19 these are needed:
> linux-headers-2.6.31-19
linux-headers-2.6.31-19-generic
linux-image-2.6.31-19-generic
Be careful when removing kernels not to remove all of them or removing any of the 3 needed files as shown above.
Otherwise you will most likely not be able to boot into Ubuntu.
Once you have the ones marked that you wish to remove click on Apply.

---

### Post by jamesofthedead on 2010-03-16
Thanks, now lets say I want to add the big chunk to W7 (sorry Ubuntu) what do I do? And how do I know its not important?

---

### Post by jamesofthedead on 2010-03-16
oh, and am I correct in assuming that both ntfs and extended are Windows7, and that Linux swap is nessisary? where is GRUB btw? 

so many questions, thanks for the help

---

### Post by 2hot6ft2 on 2010-03-16
> **jamesofthedead said:**
> Thanks, now lets say I want to add the big chunk to W7 (sorry Ubuntu) what do I do? And how do I know its not important?
ok
> **jamesofthedead said:**
> oh, and am I correct in assuming that both ntfs and extended are Windows7,
No, the NTFS is win 7. The extended partition has the unclaimed 41.5GB, Ubuntu and the linux swap inside it.
> **jamesofthedead said:**
> and that Linux swap is nessisary?
You can run without a swap but it may have a detrimental effect on performance depending on how much RAM you have and what you're doing and you wont be able to suspend or hibernate without it.
> **jamesofthedead said:**
> where is GRUB btw?
At the very beginning of the drive in the MBR Master Boot Record unless you did something else during install.
> **jamesofthedead said:**
> thanks for the help
You're welcome.

Give me a few minutes to type out what you need to do to let win7 have the empty space.

---

### Post by lordskid on 2010-03-16
you may want to install ntfsprogs first to enable your gparted to modify/create/delete ntfs partitions.

go to system->administration->synaptic package manager
search for ntfsprogs and install.

> 
h, and am I correct in assuming that both ntfs and extended are Windows7, 

ntfs and extended are both primary partitions.
ntfs is your windows 7
extended is a container for the empty partition, 
ext4 (your linux) and swap.

> 
and that Linux swap is nessisary?
 

while not really necessary, it helps make your linux work faster. some suggests to make swap at least twice your system memory.

> 
 where is GRUB btw?

the modules and most of grub files will have to be in your ext4 partition.

when you boot your computer do you see a "starting grub..." or a windows loader?
if it is the grub then your grub boot loader will reside in your ntfs if not it is in ext4

---

### Post by 2hot6ft2 on 2010-03-16
You'll need to boot to the livecd to do this. So boot the livecd and go to
System > Administration > GParted or Partition Editor whichever it has.

Right click on the linux swap partition (sda6) and select swapoff.
Right click on the extended partition (sda2) and select unmount.
Left click on the extended partition (sda2) and select Move/Resize.

Grab the left hand slider and slide it to the right until it just contacts the left edge of the ext4 partition (sda5).

Click on Apply (the green checkmark) and wait for it to finish.

When it finishes you will not have an extended partition around the unclaimed 41.5GB.

Now there are 2 ways to expand the windows partition to fill the unclaimed space (you will have to choose which way you want to do it).

1st way: While still running the livecd select the windows NTFS partition and select Resize/Move.
Grab the right hand slider and move it to the right until there is 0 MB of free space after it.
Click on Apply (the green checkmark) and wait for it to finish. This will take some time.

When it finishes close the partition editor and reboot removing the livecd in the process.
The first time you boot into windows it will do a checkdisk, let it do it's thing.

2nd way: Windows like to handle it's own partitions and letting it is the best way to keep from messing up the windows partition so I'm including that option.

Reboot into windows removing the livecd in the process.
Once in windows go to Disk Management.
Right click on My Computer and select Manage then select Disk Management
Then select the windows partition and Resize and set it to fill the unclaimed space with 0 MB after.
Click on Apply (the computer will say it needs to reboot, let it) when it starts up choose windows and it will start making the changes so sit back and wait for it to finish. This will take some time.

That's it.

---

### Post by 2hot6ft2 on 2010-03-16
> **lordskid said:**
> you may want to install ntfsprogs first to enable your gparted to modify/create/delete ntfs partitions.
The livecd can handle it and installing it then running the livecd will not be any help.
> **lordskid said:**
> 
while not really necessary, it helps make your linux work faster. some suggests to make swap at least twice your system memory.

While I don't agree with the twice your RAM idea if you want to be able to suspend or hibernate it should be at least the same as your RAM or a little bigger.

---

