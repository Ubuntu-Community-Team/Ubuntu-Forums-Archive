---
title: "Best filesystem to recover data from?"
date: 2011-08-28
forum: General Help
---

### Post by layr on 2011-08-28
As i managed to wipe off my /home folder a moth ago, i set up few scripts that create backups of vital data.
One page stated ext4 is tough filesystem for data recovery, which i have to agree, since most of the data wasn't recoverable.

Would it be better to create a different partition for storing backup tarballs and what filesystem should it incorporate? Data recovery-wise that is.

---

### Post by SavageWolf on 2011-08-28
Generally if you have a partition dedicated to backups only, you shouldn't use a certain filesystem because it has a good chance of recovering data; you don't need any data recovery, if the data goes poof, then you just need to back it up again. But it WOULD be a good idea to have a separate partition for backups, ideally you'd want an separate hard disk or even a separate computer, but a partition is better than nothing.

You should also never use a "backup" system that involves recovering files from a dead hard disk, in the "If it breaks I can just recover files from it" frame of mind. You could also use Ubuntu One for backups.

---

### Post by layr on 2011-08-28
> **SavageWolf said:**
> You could also use Ubuntu One for backups.
Trying to implement that. There's one problem though - if one happened to delete backed up file, it gets deleted on the Ubuntu One account also.
> **SavageWolf said:**
> Generally if you have a partition dedicated to backups only, you shouldn't use a certain filesystem because it has a good chance of recovering data; you don't need any data recovery, if the data goes poof, then you just need to back it up again

Indeed. It's obviously too late - logic is degrading :D

---

### Post by Slim Odds on 2011-08-28
I think we are a little confused by your original question. Maybe you could explain a little better.

If you really want to protect your data, you need to look into RAID and a good external backup as well.

---

### Post by thi3000 on 2011-08-28
I just recovered everything from a failed desktop load, meaning that whenever I booted it wouldn't load the desktop. but i did that to myself. anyway you can recover anything from an ext4 file system.  Likewise if you made a back up with a windows ntfs , it still would be recoverable but the process is long and difficult if you were unable to boot.

---

### Post by Wim Sturkenboom on 2011-08-28
> **Slim Odds said:**
> I think we are a little confused by your original question. Maybe you could explain a little better.

If you really want to protect your data, you need to look into RAID and a good external backup as well.I doubt very much that RAID will help against the type of accidents that we're talking about :)

Backups are the fastest way to restore a system.

---

### Post by layr on 2011-08-29
> **thi3000 said:**
> I just recovered everything from a failed desktop load, meaning that whenever I booted it wouldn't load the desktop. but i did that to myself. anyway you can recover anything from an ext4 file system. Likewise if you made a back up with a windows ntfs , it still would be recoverable but the process is long and difficult if you were unable to boot.

Is this true? Again, a single source recommended using NTFS instead of ext* filesystem, as they're almost always recoverable. Though that source wasn't really reliable. Maybe SavageWolf is correct and there is slim chance i wipe out both partitions:D

Other HDDs and externals are out of option, as i'm on a lappy and external backups means i'd have to remember to plug it in and back up on it. I believe automated script is way superior (ok, it could be done so the backup is created automatically when external is inserted, but it still leaves me having to use it regularly)

---

### Post by Slim Odds on 2011-08-29
> **Wim Sturkenboom said:**
> I doubt very much that RAID will help against the type of accidents that we're talking about :)

Backups are the fastest way to restore a system.

I guess I should have capitalized and bolded the AND for you.

> If you really want to protect your data, you need to look into RAID **AND **a good external backup as well.Yes a backup solution is a must. I added RAID because he seems to be interested in data protection AND recovery.

RAID is much faster and easier to recover in the event of minor hardware failure. But, of course, backup is always the ultimate solution.

---

### Post by Slim Odds on 2011-08-29
> **layr said:**
> Is this true? Again, a single source recommended using NTFS instead of ext* filesystem, as they're almost always recoverable. Though that source wasn't really reliable. Maybe SavageWolf is correct and there is slim chance i wipe out both partitions:D

Other HDDs and externals are out of option, as i'm on a lappy and external backups means i'd have to remember to plug it in and back up on it. I believe automated script is way superior (ok, it could be done so the backup is created automatically when external is inserted, but it still leaves me having to use it regularly)

Any drive that is always connected can be wiped out with your important data. If you really want protection, you need to make a "dis-connectable" backup to take off-line.

---

