---
title: "command line alternative for &quot;Safely Remove Drive&quot; for encrypted hard drive"
date: 2012-03-03
forum: General Help
---

### Post by sparhawkthesecond on 2012-03-03
Hi,

I've created an encrypted external USB hard drive as per the instructions [here]("https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage"). Previously, I was able to "Safely Remove" the external hard drive via the command line using [these instructions]("http://ubuntuforums.org/showthread.php?t=1821645"), which would unmount and then power down the hard drive. This worked fine previously:
```
udisks --unmount /dev/sdb1 && udisks --detach /dev/sdb
```

Now, I can unmount the (unencrypted) partition with "udisks --unmount /dev/dm-0", but I need to "Lock Volume" within the "Disk Utility" GUI before I use "udisks --detach /dev/sdb".

Is there a way to "Lock Volume" via the command line?

---

### Post by Khayyam on 2012-03-03
> **sparhawkthesecond said:**
> [...]Now, I can unmount the (unencrypted) partition with "udisks --unmount /dev/dm-0", but I need to "Lock Volume" within the "Disk Utility" GUI before I use "udisks --detach /dev/sdb".

I'm not familiar with 'udisk' but I imagine that all Disk Utilitiy is doing that --umount doesn' is close the dm-crypt. So ...

```
cryptsetup** luksClose <name>
```

Where '<name>' is whatever you called the mapped device. You should then be able to run --detatch.

HTH ... khay

---

### Post by sparhawkthesecond on 2012-03-06
Yes, sorry, perhaps I should have been more explicit. From the Disk Utility GUI, it does seem that step 1 (i.e. "udisks --unmount /dev/dm-0") is equivalent to "Unmount Volume" in Disk Utility, and part 2 would be the "Lock Volume" of Disk Utility. If I use the GUI for part 2, then I can "Safely Remove" either by the GUI or through --detach.

You are correct though, "cryptsetup luksClose <name>" fixed the problem for me! It was a bit confusing actually, because I had seen this command previously, but it had always returned the error "Device <name> is not active." I was never sure what to put in as <name>. I tried the label of the unencrypted volume, and other permutations, but the answer is actually to use "/dev/dm-0", which hardly seems like a "name" to me! And it's certainly not what I called it (despite what the man page suggests). Anyway, the final sequence is ```
udisks --unmount /dev/dm-0 && sudo cryptsetup luksClose /dev/dm-0 && udisks --detach /dev/sdc
```Thanks very much for your help! Also, this script might be useful for others, for backups. I turn on and attach the external HD, then run this script ```
#!/usr/bin/env bash
# Backup using backintime, then "safely remove" disk (i.e. unmount and power down).
# replace [UUID1] and [UUID2] below for your devices

# Do the backup. Alternatively, select profile with --profile
sudo backintime -b

# Find the diskid. e.g. dm-0 for lukid; sdb, sdc for drive
# identify the UUIDs you wish to find using $ ls -l /dev/disk/by-uuid/
luksid=`ls -l /dev/disk/by-uuid/[UUID1] | sed -r 's/^.* -> ..\/..\/(....)$/\1/'`
hdid=`ls -l /dev/disk/by-uuid/[UUID2] | sed -r 's/^.* -> ..\/..\/(...).$/\1/'`

# Send a notification
notify-send "Back In Time" "Backup is complete. Ejecting disk." -i gtk-save

# Unmount the LUKS partition, and the disk and power it down.
udisks --unmount /dev/${luksid} && sudo cryptsetup luksClose /dev/${luksid} && udisks --detach /dev/${hdid}

```When I hear the disk spinning down, I know it's complete. Thanks again!

---

### Post by Khayyam on 2012-03-06
> **sparhawkthesecond said:**
> You are correct though, "cryptsetup luksClose <name>" fixed the problem for me! It was a bit confusing actually, because I had seen this command previously, but it had always returned the error "Device <name> is not active." I was never sure what to put in as <name>. I tried the label of the unencrypted volume, and other permutations, but the answer is actually to use "/dev/dm-0", which hardly seems like a "name" to me! And it's certainly not what I called it (despite what the man page suggests)

Thats a new one for me, I've always used the <name> .. and not the device map. I'm not sure why this might happen, I know that device-mapper was merged with LVM2 and so prehaps that method was depreciated.

> **sparhawkthesecond said:**
> Thanks again!

Your welcome ... you should now [mark this thread as [SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

best ... khay

---

### Post by sparhawkthesecond on 2012-03-06
> **Khayyam said:**
> Thats a new one for me, I've always used the <name> .. and not the device map. I'm not sure why this might happen, I know that device-mapper was merged with LVM2 and so prehaps that method was depreciated.
Using the device map actually makes more sense to me, since I've unmounted the unencrypted volume, and hence the associated label is not "active" anymore.

> **Khayyam said:**
> 
Your welcome ... you should now [mark this thread as [SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")
I thought I had, but perhaps I did it wrong? Anyway, I'll click it again.

Cheers.

---

### Post by sparhawkthesecond on 2012-03-06
> **sparhawkthesecond said:**
> 
Anyway, I'll click it again.

Oops, I can't. It must have been marked as solved already. Let me know if it's showing up different to you.

Cheers.

---

