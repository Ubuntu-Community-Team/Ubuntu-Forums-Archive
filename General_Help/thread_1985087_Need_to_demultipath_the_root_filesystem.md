---
title: "Need to demultipath the root filesystem"
date: 2012-05-22
forum: General Help
---

### Post by echomirage on 2012-05-22
I'm new to Ubuntu over the last 5 months and I'm now working to figure out how to multipath a couple of SAN LUNs on two systems, both running 12.04. While I've managed to get the LUNs multipathed on one system, I've inadvertently multipathed the root filesystem:

Filesystem                                           Size  Used Avail Use% Mounted on
/dev/mapper/3600508b1001030384531373344300300-part1   89G  6.9G   78G   9% /

Is there a way to undo this without rebuilding the system? I've been poking around and considered editing the grub configuration and the /dev/disk/by-uuid symlinks back to their original sda devices, but I wasn't sure if that was complete and/or safe.

FWIW, I added 'devnode "^sda"' to the blacklist on one system but not the other, which I think is why this happened once I got the LUNs mp'ed. Additionally, I've added a block to the multipath block on both systems, e.g.

    multipath {
        wwid 3600143800648d7e40000700002310000
        alias hp-hsv300-1
    }

but that's not working on one of them. Not sure what else I'm missing. The Ubuntu docs are pretty good but even after using them and eugooglizing all day I'm still at a loss.

Any help would be appreciated!

---

