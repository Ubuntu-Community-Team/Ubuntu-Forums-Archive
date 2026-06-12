---
title: "How to repair external NTFS drive?"
date: 2010-10-25
forum: General Help
---

### Post by phredbull on 2010-10-25
I have a Seagate FreeAgent XTreme 500gb external hard drive that I'd like to partition and install another OS on. It is currently NTFS formatted, and has around 80 gb of data that I don't want to wipe. In GParted, there's a :!: next to the partition name, and when I select "Resize/Move partition", the dialog box pops up but doesn't let me make any changes. When I view "Information" on the volume, I see the errors shown in the attached screen cap. When I select "Check", it starts to check the disk and shows an error, but before I can see what it is, the computer becomes unuseably slow and I have to reboot. In Disk Utility, it says the drive is healthy, and passes all tests.

Any help getting my disk partitioned and bootable without wiping existing data would be greatly appreciated!

---

### Post by sikander3786 on 2010-10-25
Try ntfsfix,

```
sudo ntfsfix /dev/sdXY
```

Where sdXY is your drive identifier you can find it from

```
sudo fdisk -l
```

---

### Post by phredbull on 2010-10-25
I tried this:
```
phredbull@phredbull-laptop:~$ sudo ntfsfix /dev/sdb1
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sdb1 was processed successfully.
```
but GParted still won't let me alter the volume.

---

### Post by psusi on 2010-10-25
NTFS is the Windows fs, so you need to have Windows chkdsk it.

---

### Post by efflandt on 2010-10-26
Do what gparted tells you to do.  Run **chkdsk /f** on it from Windows.

That fixed a laptop hard drive with bad sectors in a USB enclosure, so when it was back in the laptop, WinXP was able to boot.  Before that WinXP had refused to even boot in safe mode.  Because of the bad sectors clonezilla did not work, so I put it back in the USB enclosure and used the WD version of Acronis to image the drive for the warranty replacement (which worked fine on that).

---

### Post by dcstar on 2010-10-26
> **phredbull said:**
> 
........
In Disk Utility, it says the drive is healthy, and passes all tests.


A drive is not a partition. A partition is something that exists on a drive.

Stop mucking around with gparted, move the data off that partition and then delete it and create a fresh partition.

---

### Post by phredbull on 2010-11-05
Uh oh. I connected the drive in WinXP and ran chkdsk /f, but after an hour or 2, it stopped at step 4. I rebooted, and chkdsk started automatically. I let it go, and soon, I saw errors stating, "Unreadable sector #xxxxx", (I forgot the exact phrasing); around 2000 such errors, all consecutive numbers. After listing all of the errors, it started going through them all, stating, "Attempting to repair sector #xxxxx - failed". At the rate it was going, I estimated it would take around 36 hours to finish, and it wasn't fixing anything anyway, so I attempted to abort. "Esc" or "Ctrl+Alt+Del" didn't work, so I did a hard shut down.

Now, I can't see my drive in Linux or WinXP. It doesn't show up in Drive Utility, GParted, or any of the Win utilities.

What are the chances of any of my data still being recoverable?

And regardless, how can I re-format my drive?

:confused:

---

### Post by sikander3786 on 2010-11-05
That doesn't sound good at all.

At first, try to scan your drive by using the tools from the manufacturer's website (most of them provide those tools).

If it is not being detected at all, I fear the drive might be dead.

I feel like your HDD had got some bad sectors, and many times, I have seen drives failing when you attempt to scan or recover those bad sectors. Can you feel your drive spinning when you power on your system?

If you get your drive detected somehow, you can try these options.

Testdisk is a powerful tool to recover lost partitions and data.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Also see this one.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

But first of all, I will recommend to scan the drive using the manufacturer tools.

Hope for the best. Good Luck.

---

