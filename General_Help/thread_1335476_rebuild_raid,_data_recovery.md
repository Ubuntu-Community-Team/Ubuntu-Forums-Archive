---
title: "rebuild raid, data recovery"
date: 2009-11-23
forum: General Help
---

### Post by piusvelte on 2009-11-23
I'm seeking help before I exhaust my savings to recover data from my file server.

I've a 5 disk, hardware RAID3 using a Netcell controller, amounting to about 1.6T of storage. One drive failed and the the controller did not fail gracefully, but instead reported 4 drives as unassigned, with the 5th as unattached. Following other online advise, I swapped the 5th drive, deleted the array and recreated it. Then I pulled the 5th drive, so the controller appeared as I expected it should, functioning array, in a degraded state.

I attached the 5th drive directly to the MB, so that I could confirm that the data wasn't changed on it. The 5th drive mounted and I could browse the data as though I had never set it up in a RAID array.

The RAID, however, did not return to the condition that I had hoped. The partition table was gone. Again, following advise found online, I used parted, to mklabel "msdos". This didn't change anything. I used ddrescue to image the whole array onto another drive. No errors were found by ddrescue. From now on, I've been working against the image of the raid (as I should have done from the beginning). Fsck.ext3 reports a bad superblock. I tried using a backup superblock, but the results are the same. I've run testdisk and parted rescue. They should find a ext3, swap and possibly another ext3 partition. I don't recall if I overrode LinuxMCE's default of using an additional partition for recovery. Testdisk finds 2 partitions:
```

Disk raid.iso - 1600 GB / 1490 GiB - CHS 194566 255 63
     Partition               Start        End    Size in sectors
D Linux                    0   1  1 96537 254 63 1550882907
D Linux                    9   2  1 96546 254 63 1550882844

```
If I try to list the files for either, it errors out with a segmentation fault.

parted finds several partitions, all about 900G, all started a couple kb apart.

My co-worker suggested that perhaps the drives have changed order, though I've not moved them. He said that it may be that the controller is reading the blocks in a different order.

I've run photorec and foremost. I ran them until they found a few files and the stopped them so I could check out what they found. They found a few text files, but the contents were scrambled a little bit. There weren't any odd characters, but they letters were mostly out of order.

I'm rerunning testdisk with different CHS geometries, but I think that I should image each of the 4 drives separately and try to rebuild from that. I'm trying to find the best software to do that.

I've gotten quotes from data recovery labs starting at $1500.00, and I'm several months behind on backups and must get this data back, but I'm beyond my technical knowledge in this area. Are there any other suggestions for how to proceed?

Thank you all very much, I know this was a long read.

---

### Post by piusvelte on 2009-11-25
I imaged the 4 drives individually and am trying out Raid Reconstructor, and then asrdata2/smart... Any other software that I should look at, or other advice to recover the raid? Thanks!

---

