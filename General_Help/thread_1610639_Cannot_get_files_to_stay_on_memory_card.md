---
title: "Cannot get files to stay on memory card"
date: 2010-10-31
forum: General Help
---

### Post by prybar on 2010-10-31
Hi All.

Finally did it, ditched windows for good and have Ubuntu full time.

Lots of hiccups at first, but this forum and google in general has been helpful, but this particular problem, i can't find the right wording to get help on.

I have a cheapo tf USB reader, for my son's edge cartridge.  Ubuntu sees it just fine, but when i try and make any changes to the files, it appears to work, but upon re-insertion, nothing has changed.

I've changed the permission in Storage Device Manager, they don't stick.  I've done it thru a Root Terminal, still no good.  When I right click on the mounted system, it says the permissions could not be determined.

I've tried ejecting, safely removing, yanking the thing out of there, emptying trash, not emptying trash, as root, as user.  Nothing makes the changes stay (removed or new files added).

Any guidance from the gurus (or non gurus, i'm not picky :D) is greatly appreciated.

thanks in advance

pry

---

### Post by MooPi on 2010-10-31
Save the data on the card elsewhere then delete the partition on the card and reformat. I had to do this once before and can't remember the reason , just that I had to wipe it out and start fresh.

---

### Post by prybar on 2010-11-01
Thanks, but it's not working.  I tried formatting and messing around on my bosses windows Xp system, and it wouldn't let me format or add or delete files.  Bring it home to ubuntu, and if i try and delete the partition, or format, it fails with this:


Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdc, start=0, size=1977614336, type=0x0c
Entering MS-DOS parser (offset=0, size=1977614336)
MSDOS_MAGIC found
looking at part 0 (offset 69120, size 1975546368, type 0x06)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
got disk
new partition
added partition start=512 size=68608
committed to disk
Error calling fsync(2) on /dev/sdc: Input/output error
Cannot scrub filesystem signatures at offset=512 and size=68608

Am I to assume to memory card is pooched?  Can I "force" a format? last i recall, i added a file to the card using this reader in Backtrack 4, and it hasn't worked properly since then.

Thanks for the quick reply!

pry

---

