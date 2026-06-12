---
title: "Mount Journaled HFS+ as writable?"
date: 2009-12-04
forum: General Help
---

### Post by raydowe on 2009-12-04
I have a netbook, on which I installed Windows 7, Ubuntu, Mac OS X (iDeneb 1.3), and then repaired GRUB2. I can no longer boot into Mac OS X and I'm looking for a way to access the files on that partition.

I can mount the partition, but it is ready only. I have installed the hfsplus module, but maybe I'm utilizing it wrong as it doesn't seem to make a difference.

Is there a way to mount a Journaled HFS+ drive as writable? Can't seem to find any solutions so any help would be appreciated. I'm relatively new to linux and unix.

---

### Post by bodhi.zazen on 2009-12-04
I believe permissions are set at the time of mounting. Use the options umask, dir_umas, and / or file_unmask

For example, umask=777

---

### Post by coffeecat on 2009-12-04
> **raydowe said:**
> Is there a way to mount a Journaled HFS+ drive as writable?

I don't believe that is possible. From my own experiments and from what I've read elsewhere, the Linux hfs+ driver only supports read on a journalled hfs+ filesystem, but does support read/write on a non-journalled hfs+ filesystem.

So - my only suggestion.

Open a root nautilus window from a terminal with:

```
gksudo nautilus
```Even though you will still only be  able to read, you should now be able to browse through the hfs+ filesystem without permission denied errors and copy your files to the Linux partition. The problem with that is that they will be owned by root on the Linux partition and you will need to do a bit of 'sudo chown'-ing. Or you could use the root nautilus file browser to copy the hfs+ files to an external HD formatted either NTFS or FAT32. Being Microsoft filesystems they'll cheerfully lose the Unix permissions for you. One of the rare occasions when a MS filesystem can be a positive advantage. :wink:

---

### Post by raydowe on 2009-12-04
I see, I was afraid of that...

Thanks for you suggestions but I actually need to be able to write to the HFS+ partition (which is why I'm seeking write permissions). Maybe I can do it through the OSX install disk somehow.

Thanks again for your contributions.

---

