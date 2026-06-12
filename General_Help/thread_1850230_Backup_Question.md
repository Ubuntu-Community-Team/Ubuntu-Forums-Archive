---
title: "Backup Question"
date: 2011-09-26
forum: General Help
---

### Post by GuiGuy on 2011-09-26
I have about 3.7T of data on a RAID5 setup. I'd like to back this up to a couple of 2T HDDs that I can plug into an eSATA docking station.

Is there an uncomplicated backup software option for Linux/ Ubuntu that would back up and stop to prompt for the second drive when the first is full or near full?

My alternative is to use Acronis via Windows over the network, which would be slow and, in any case, a linux solution would be nice. 

Thanks

---

### Post by dcstar on 2011-09-27
> **GuiGuy said:**
> I have about 3.7T of data on a RAID5 setup. I'd like to back this up to a couple of 2T HDDs that I can plug into an eSATA docking station.

Is there an uncomplicated backup software option for Linux/ Ubuntu that would back up and stop to prompt for the second drive when the first is full or near full?

My alternative is to use Acronis via Windows over the network, which would be slow and, in any case, a linux solution would be nice. 

Thanks

You should be able use the **Unison** package to back up specified data to one drive, and then the rest to the other drive - but you will have to manually kick off the second backup.

---

