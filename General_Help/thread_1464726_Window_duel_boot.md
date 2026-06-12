---
title: "Window duel boot"
date: 2010-04-28
forum: General Help
---

### Post by zolf42 on 2010-04-28
So I wanted a break from windows so I downloaded the latest ubuntu put on DVD and installed for a windows/ubuntu duel boot, and every thing was fine until I raged quit and got rid of windows all together. After a week of trying to get it back I have given up and come to the forum. I have got a recovery disk and a DVD with windows on it. When recovery disk is booted it get to a point when choosing a partition, I'm given on options and when I click forward it says doing this will delete all partitions then it starts, gets to o% and come up with error 3. When  booting the windows disk, nothing happens and there is a normal boot. I have used G parted to create a unallocated partition... were do I go from there?

---

### Post by pqwoerituytrueiwoq on 2010-04-28
Have you tried the windows disk when there was a unallocated partition?

---

### Post by Mark Phelps on 2010-04-29
> **zolf42 said:**
> ... were do I go from there?

Start by providing some details ... like ... WHICH version of MS Windows?

Was the Windows OS preinstalled on the PC, or did you install it yourself?

If it was preinstalled, did the Recovery Disk come with the PC or did you create/burn it yourself?

IF it came with the PC, most probably what it did was boot into WinPE and then go searching for the restore image on the PC.  I don't know what "error 3" means, but my guess is that it was unable to find the recovery image on the drive.

As to why it won't install, don't know offhand. It generally wants to install to unformatted space. If you created an empty partition with GParted, I would remove that and see if it will install to that space.

---

### Post by houshdaran on 2010-04-30
Do you need the windows itself or the data in the deleted partitions?

---

