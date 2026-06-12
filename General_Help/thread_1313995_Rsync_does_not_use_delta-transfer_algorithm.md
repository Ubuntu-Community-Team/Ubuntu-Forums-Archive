---
title: "Rsync does not use delta-transfer algorithm?"
date: 2009-11-04
forum: General Help
---

### Post by bovender on 2009-11-04
Hi all,

I am using rsync to back up my home directory to an external USB drive. My home directory contains a VirtualBox disk file which is about 10 GB. It appears that rsync always copied the whole file, which takes disproportionately long compared to the rest of the backup process.

Shouldn't rsync copy only those parts of a file that were changed? I can't imagine that Windows (which resides in that VDI file) always modifies the entire file when it is run, or does it?!

What can I do to make rsync copy this file faster?

TIA

lazy

---

### Post by sedawk on 2009-11-04
Keep in mind that rsync has to read both files at least
once to check if they differ - reading 20 GB takes time.

On the other hand it is possible that starting Windows
touches lots of files (or metadata of files) so there
might be lots of changes to the disk image after running
the virtual machine.

I'm using "--size-only" parameter of rsync for
"lazy" backups. So it only saves files if the size
changed. This is not a perfect backup, but it is
enough to backup new files and growing files.

---

### Post by bovender on 2009-11-04
Thanks, good idea to use --size-only!

---

### Post by wildweathel on 2009-11-04
I don't think that will work.  Actually, here's the issue: rsync isn't quite the right tool for this.  Rsync's delta-transfer isn't enabled for transfers entirely on the same host, because it wouldn't speed them up.  Basically, rsync delta-transfer only speeds up the situation where you have two CPUs joined by a slow network.

Zsync only requires CPU time on the receiving end, or rather, it can pre-compute and save the sender's checksums.  Unfortunately, your USB is the receiver, so that doesn't help.  Those are the two delta-transfer type programs I've used.  

Looking at a brief description of the rsync algorithm, it looks like it's possible to save precomputed *recipient* checksums, and maybe to use that to update your backup file in place (with the --inplace option).  But, that's not  implemented as a feature yet, in fact, it's still just a crazy floating idea. 

I don't see any way to copy the file faster.  You're limited by the speed of your disk drives, how quickly it can be read off of the main disk and written to the USB.  Adding a read and compare step isn't going to help.

**--size-only is dangerous.**  Basically, this will only transfer data when your virtual disk grows.  If Windows re-uses space on the disk and doesn't grow the disk, it wont be transfered.[B]  Once the virtual disk grows to its limit, it won't grow and won't be backed up at all.
[/B]
You should do incremental backup from inside Windows, with occasional backups of the VDI.  This is a case where rsync will provide benefit by skipping unchanged files on the disk.  The virtual network is very fast, so the extra disk and CPU usage of delta-transfer is not worth the savings in network usage.  Use -W to disable delta-transfer.

---

