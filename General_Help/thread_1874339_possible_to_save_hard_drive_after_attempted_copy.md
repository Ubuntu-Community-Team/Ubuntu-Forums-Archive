---
title: "possible to save hard drive after attempted copy??"
date: 2011-11-02
forum: General Help
---

### Post by goodbye-windows(tm) on 2011-11-02
Hi All,

I bought a 250 GB hard drive and installed it as a slave drive (old P4, IDE drive, MSI motherboard). 

I then used:

sudo dd if=/dev/sda of=/dev/sdb bs=1024k conv=noerror 

and copied the entire primary hard drive over to the new 250 GB drive without errors.

But, I rebooted instead of removing the copied drive, and ended up with a bunch of errors-I think the there were conflicts.

I meant to remove and archive the copied drive, but wasn't thinking and ended up rebooting instead.

My primary drive survived, but the brand new 250 GB drive developed a problem, likely as a result of my error.

I'd like to save the 250 GB drive if possible. But, gparted does not detect it and the drive activity LED stays illuminated. Trying to boot with the drive hangs the computer, with the red LED constantly on. I can boot normally with the old (primary) drive, but the newer 250 GB back up drive is the problem.

How do I rescue the drive??? I can't imagine there is any mechanical issue, so I'm hoping to use software to save the drive. 

Is the drive trash, or is there hope for it?

TIA

Art

---

### Post by as2000 on 2011-11-02
Have you tried disk utility? Does not sound like the drive is toast, just messed up on the boot sector. I have always had luck with disk utility and the few rare times that it failed, I would then go the fdisk route. I think that is in the repositories still

---

### Post by goodbye-windows(tm) on 2011-11-03
I downloaded disk utility after booting from the live CD.

The program did detect the drive. It gave me the option to format the drive and to format the volume. 

Neither operation was successful, the errors are shown below.

format volume:Error creating file system: helper exited with exit code 1: Error calling fsync(2) on /dev/sda: Input/output error

format drive:Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on /dev/sda: Input/output error

I did choose different formats to try, but no matter what I did, the result was the errors shown above.

Any other suggestions?

TIA.

Art

---

### Post by gsmanners on 2011-11-03
> **goodbye-windows(tm) said:**
> ... gparted does not detect it and the drive activity LED stays illuminated. Trying to boot with the drive hangs the computer, with the red LED constantly on. I can boot normally with the old (primary) drive, but the newer 250 GB back up drive is the problem.

How do I rescue the drive???

Have you checked the master/slave settings on the drive?

---

### Post by goodbye-windows(tm) on 2011-11-03
Hi gs,

It's an older P4, with an IDE interface and uses cable select. I have the proper cables and the jumper is set to use cable select.

Before I ran the test, I unplugged the old drive and plugged that connector (the master drive connector) into the 250 GB drive that has some sort of problem. During the repair attempt, the original drive was completely disconnected.

I built the system myself and throughout the years, I have lots of experience running multiple drives. 

Am I missing something regarding the master/slave setup?

Regards,

Art

---

### Post by gsmanners on 2011-11-03
It could be that the BIOS simply needs a master, and that cable select only works in some kind of tandem with a master (or something like that).

---

