---
title: "Corrupted USB Drive, need help fixing..."
date: 2009-11-23
forum: General Help
---

### Post by ViralTitan on 2009-11-23
I have a flash drive that was corrupted while the power went out while trying to partition and install files to it. I have tried many, many ways to fix it both in Windows and Linux and I cannot find a single way to solve this. Here is a list of things that appear (or don't appear) when trying to fix the drive.

Windows:
- Appears as "Removable Media"
- No Size or File System
- Does not appear in chkdsk or disk management
- When "Remove Safely" is clicked, there is an error
- The drive cannot be opened

Linux:
- Drive cannot be mounted
- Drive cannot be opened/explored
- Size unknown and unknown file system
- Error when partitioned
- fdisk returns "unable to open /dev/sdf" (sdf is the drive)
- Does not register in the GParted  application

The drive trashed beyond partitioning with any software I can find. I do not care about any of the software what's on it, I just need the drive fixed.

---

### Post by rbc on 2009-11-24
Two suggestions:
Open Synaptic and install Testdisk. Once that is done, go to terminal and type:
sudo testdisk

You will be walked through the steps of trying to recover the appropriate partition. Just make sure you are pointing it to the correct one. If that doesn't work, and you truly do not care about the data, open terminal and type:
sudo dd if=/dev/zero of=/dev/sdf

That will write zeros to the whole drive. Again, make sure that /dev/sdf is, in fact, the flash drive. Then run GParted and reformat/partition

---

### Post by Don1500 on 2009-11-24
PQi (a USB drive manufacturer) has a Free Download that has resurected a few USB thumb drives for me. Or are you talking about a Large SS drive that plugs into your USB?

I had thought it was called Ur-Smart but it looks like Ir-Dumb because that aint it. The software is on the site but I don't remember what it was called. I would know.....if I were home where my computer is, with the program installed.

---

### Post by teward on 2009-11-24
Well, I used a 32GB USB Flash Drive that died due to the Input/Output system on it failing due to not safely removing the drive on Linux.  Similar problem to the poster.  Checked with manufacturer, they said that there's no way to fix it.  So I bought another one, and now I safely remove it every time.  :P

---

