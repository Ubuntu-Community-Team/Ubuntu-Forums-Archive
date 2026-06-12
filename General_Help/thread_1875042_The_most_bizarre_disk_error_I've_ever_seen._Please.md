---
title: "The most bizarre disk error I've ever seen. Please help!"
date: 2011-11-04
forum: General Help
---

### Post by dizzysoul on 2011-11-04
I have a friend come to me with a computer problem; Windows would no longer boot for him due to a corrupted partition. This isn't the first time this happened, so I assumed the disk was going bad. The disk is a Seagate 3500320NR and it's 500GB.

I have a copy of Spinrite 6, so I ran it on the disk to try and fix any bad sectors. Spinrite would crash while trying to fix the dirve, a problem I've never had before with Spinrite.

So I decided to use an Ubuntu 11.04 Live CD and the latest version of ddrescue to copy the drive to a 320gb spare I had lying around. At first, ddrescue was chugging along, but then it stopped and complained about running out of space (on the LiveCD, not the spare drive). I thought maybe the logfile for ddrescue grew bigger than the available memory for the LiveCD, so I restarted ubuntu to purge the logfiles and finish where things left off.

After I rebooted, ubuntu was able to mount the windows partition! I guess all the work ddrescue did fixed the corruption, and I could see all the files. 

So then I fired up gparted to copy the partitions over to the 320gb spare drive and resize things to fit the drive. While gparted was resizing the partitions, it failed and said there was an error. Now this is where things get really bizarre.

After this error happened, the drive would no longer mount. It was unrecognizable by the BIOS and everything else. Whenever I tried to search for devices in ubuntu, I would get an error along the lines of "Can't mount xxx, partition extends beyond disk".

In a last ditch effort, I got the latest version of SeaTools, which was able to find the drive... but the name has changed. Originally, the drive was mounted under the name "ST3500320NS" which is the model number of the drive. However, after the error happened with gparted, the name of the drive has completely changed. It's now named "HDD:4M-External Disk 0"

After using SeaTools, the drive magically came back and the BIOS can now see it again. However, I still can't mount it in ubuntu.

I tried using TestDisk to recover the windows partitions, and I can find and write both of them(System Reserved and the OS partition). The "System Reserved" partition will mount fine, but the OS partition will not. I keep seeing errors about the partition extending off the disk, but I double checked the mount points and everything is correct. When I use "List Files" on the windows partition, the only file that I can see is "Perflogs" and that's it.

[LIST]
[*]Why did the name of the drive magically change? How can gparted do that?
[*]Why is the computer complaining about partitions extending beyond the drive? The mount points and geometry are all correct.
[*]If the windows partition is messed up, why am I able to list files? And why is only perflogs show up? Doesn't make sense!
[/LIST]

I know the data is still on the drive, and there must be some way to recover it.. but I am stumped on why the drive was so strangely altered after the gparted error. I'm not sure what to do!

I looked up the geometry settings for the drive and checked then in TestDisk, and everything is what it's supposed to be. What else can I do? Please help! Thank you!

---

### Post by BillyBoa on 2011-11-04
From all this, I didn't understand if you used another hard drive to boot and your failed drive to be connected as slave. Or just use an adapter and the failed drive as a USB external drive. I feel that you already know that you have only the slightest opportunity to recover some of your data and trying to create new partitions and so on, is causing the drive to die permanently....

---

### Post by iponeverything on 2011-11-04
+1 for Billy

you had window that you failed to take advantage of, if data recovery was the goal.

---

### Post by dizzysoul on 2011-11-04
> **BillyBoa said:**
> From all this, I didn't understand if you used another hard drive to boot and your failed drive to be connected as slave. Or just use an adapter and the failed drive as a USB external drive. I feel that you already know that you have only the slightest opportunity to recover some of your data and trying to create new partitions and so on, is causing the drive to die permanently....

I hooked the failing drive and the spare drive directly to the motherboard using SATA, and then used an Ubuntu LiveCD to do the recovery. I figured this was the fastest way to transfer the data between drives. I never created any new partitions. I'm not sure where you got that from. I was copying the partitions directly to a spare drive, and using gparted since I don't think ddrescue can handle resizing to fit smaller disks.



> **iponeverything said:**
> +1 for Billy

you had window that you failed to take advantage of, if data recovery was the goal.

Can you please elaborate? My steps were:

1. Use spinrite to recover corrupted partition table.
2. Since spinrite failed, used ddrescue instead to copy failed drive directly to spare drive while also fixing the corrupted partition table.
3. Since ddrescue failed to transfer, but partitions were recovered, use gparted to directly transfer partitions to spare drive.
4. Since gparted failed, used Seatools and Testdisk to make the drive mountable again.

What did I fail to take advantage of, exactly? The disk is corrupted in a way where every recovery program crashes attempting to transfer the data or fix the bad sectors. Are you implying there is a more obvious and better path than fixing the partition tables and doing a direct disk-to-disk transfer to smaller disk?

---

### Post by iponeverything on 2011-11-04
> After I rebooted, ubuntu was able to mount the windows partition! I guess all the work ddrescue did fixed the corruption, and I could see all the files.

So then I fired up gparted to copy the partitions over to the 320gb spare drive and resize things to fit the drive. While gparted was resizing the partitions, it failed and said there was an error. Now this is where things get really bizarre. 

I may have misunderstood the above, I was under the impression that the creation of a tar from from the home/ on the failing drive to backup drive was possibility after it was successfully mounted. 

Attempting to "fix" a failing drive or copy whole partions should not been attempted until after whatever important data that was on the failing drive had been copied.

---

### Post by dizzysoul on 2011-11-04
> **iponeverything said:**
> I may have misunderstood the above, I was under the impression that the creation of a tar from from the home/ on the failing drive to backup drive was possibility after it was successfully mounted. 

Attempting to "fix" a failing drive or copy whole partions should not been attempted until after whatever important data that was on the failing drive had been copied.

The important data was already backed up before the drive failed. I'm doing this to recover the windows installation and save time from having to re-install everything from scratch.

I managed to get the drive back to normal by plugging it into a different SATA port. Now it has the correct name, and I can access it through ddrescue again. I'm using ddrescue on SystemRecoveryCD instead, which seems to behave much better. It's still in the recovery process, but so far it's gone through 500GB of blocks and hasn't complained about it going to a 320gb drive.

---

### Post by oldfred on 2011-11-04
Your dd will crash. If copying from 500GB, it has to have 500GB to copy to. It does a bit for bit or byte for byte copy even empty space, so you have to have at least 500GB to copy to.

Testdisk and Windows both have been known to rewrite partition tables where the end of the last partition is beyond the end of the drive.
Post this:
```
sudo fdisk -lu
```

Ubuntu & gparted will usually not mount a NTFS partition that needs chkdsk. That is to prevent causing damage that chkdsk would then not be able to repair. If NTFS with Windows chkdsk is often the first thing you should do. If a file is corrupted it will move it to a chkdsk directory and otherwise fixup partition. You can only run chkdsk from Windows or a Windows repairCd or USB.

---

