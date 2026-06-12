---
title: "Suddenly empty folders after error"
date: 2010-10-31
forum: General Help
---

### Post by Novacrazy on 2010-10-31
I have an old, semi-corrupted computer with a main NTFS file system on the largest partition. Windows was infected a long time ago on my comp and I have started using ubuntu. I tried installing it onto the drive, and the same time trying to repartition the drive to give Ubuntu more space. I made sure there was only empty space that was changed. However, there was an error, and the NTFS partition was made corrupted even more. Windows will now not load, for the main WINDOWS folder is empty randomly now. I have reason to believe the directly was corrupted, because the free space on the drive has not changed. I was planning on reformatting the hard drive now. Except, when I plugged in an external drive(That already had ALL my backup on it), it gave me a Input/output error and corrupted the partition of the external drive that had ALL my backups on it. So I reformatted that partition to FAT32, now I am copying all my files from my internal drive onto the external drive. I just discovered that the "My documents" folder is empty. Although I know for a fact it had about 10 GB of data within it. Data I need. As with the WINDOWS folder, even though it shows empty, the free space hasnt changed, so I'm assuming the directory was corrupted. I need that data. Anyone who can possibly help me, please. Btw, I have tried repairing the NTFS partition many times, it is unsuccessful.

---

### Post by Vigh on 2010-10-31
sounds like some sort of windows based self-replicating worm, that has gotten its way around at destroying your hard-drives, not sure, you've probably lost your data, did you have any of your critical data on the ubuntu partition? my advice is to back up critical data from ubuntu partition if possible, format the external to ext4 rather than ntfs, load critical data onto external HDD from ubuntu, format the entire internal disk, and just load a fresh install of ubuntu on the entire disk, if you need windows, get a 2nd internal HDD for windows, and when you want to boot into ubuntu or windows, just select the appropriate boot device from the bios, no problems with bootloader stuff-ups then, also if the windows drive gets a virus, ubuntu should remain in-tact, only problem with ext4 file system is your external will only work on ubuntu then, however I do believe it is possible to get a windows system to read an ext4 file system as well, hope this helps at least a bit

---

### Post by Novacrazy on 2010-11-01
I think you may have been correct about the worm. I did manage to recover my files though. I used a puppy linux Live CD to get into my hard drive. The really weird thing is, it worked the first time, but not the second. Turns out, the NTFS partition on the internal drive was corrupted in a way where no third party NTFS "driver-ish" things could load it, but if a specific shutdown error occurred, it would load the default NTFS "Driver-ish" thing from the hard drive, allowing it to be read in read-only mode. So yeah, after I got all my data, I reformatted the drive, repartitioned it, and installed Ubuntu 10.10. Everything works out perfectly.

---

