---
title: "root file system filling itself up"
date: 2010-01-04
forum: General Help
---

### Post by mckechan on 2010-01-04
Hi,

This morning I cleared out some unwanted files from my home directory leaving 12G under /

I return to my copmuter to find my root file system is full up. This is not because I put the files in the trash bin I checked the space with df -h.

I am quite concerend as to why the file system filled 12G this morning and I have no idea why.

Is this a known problem and how can I work out where the files are coming from?

Thanks,

Dave

---

### Post by MooPi on 2010-01-04
I've heard of this once before and recently. Seems a script was in a loop on the other instance and kept running perpetually.
[http://ubuntuforums.org/showthread.php?t=1324789&highlight=Hard+drive+filling](http://ubuntuforums.org/showthread.php?t=1324789&highlight=Hard+drive+filling)

---

### Post by Shippou on 2010-01-04
Happened also to this #! (Crunchbang) computer. Solved by rebooting.

Maybe the temp directory got full?

---

### Post by mcduck on 2010-01-04
If you deleted the files while running with root permissions they were moved to root's trash directory (located in /root, so it's on your / partition)instead of your own.

Apart from that, the  first thing to check would be the sizes log files in /var/log. If there's some bug or hardware problem that floods some log file with error messages the logs could grow to quite insane sizes..

Anyway, the key here is simply using "df" and "du" commands to find out where the disk space is being used. Just run "du" on your root, check the largest directory, run "du" inside it and so on until you find where your 12GB is. Or use the Disk Usage Analyzer (Applications/Accessories from Gnome menu).

---

### Post by mckechan on 2010-01-05
not really sure what was going on. I've cleared some more space and it isn't refilling after a reboot. It seems that it may have been confused when I added some files to a mounted drive under media, not too sure.

One thing I do know is i wish i had never upgraded to Karmic, still having audio problems.

Thanks for the du command, i only knew of dh.

---

