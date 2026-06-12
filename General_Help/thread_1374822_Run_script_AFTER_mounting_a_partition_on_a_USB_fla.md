---
title: "Run script AFTER mounting a partition on a USB flash drive"
date: 2010-01-07
forum: General Help
---

### Post by mosär on 2010-01-07
Hi,

I would like to run a script that syncs my thumb drive and my documents afterwards a specific partition on my thumb drive is mounted (by automount).
I know about udev, but that's not what I want, I want to run the script AFTERWARDS the partition was mounted automatically.
It would be sufficient to run a script afterwards anything was mounted, I could test if it was the one I'm interested in.

I run Karmic amd64.

Thanks a lot,
Martin

---

### Post by chewearn on 2010-01-07
Well, no reason to abandon udev.  You could have your script launched by udev, go to sleep for a few seconds, then check for the mounted drive.  Retry several times until the drive is actually mounted and do the backup.

---

### Post by mosär on 2010-01-07
I think sleeping and waiting for stuff in scripts is not clean, you know. ;)
Additionally I don't feel like running my home folder backups as root.

I am working on a python script that can run in background and do the job, I'll post it when it's done.

---

### Post by chewearn on 2010-01-08
Sleeping and waiting for a few seconds is not clean. :-k
BUT, python script waiting in background indefinitely is better. :confused:

Well, it's your PC. ;)

---

