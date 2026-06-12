---
title: "Unformat howto?"
date: 2011-07-07
forum: General Help
---

### Post by uqbar on 2011-07-07
My USB drive used to be formatted in XFS on a single partition.
A coworker accidentally re-formatted it in VFAT.
No other write has happened to the disk so far.
I'm currently triying "xfs_repair -n" first but it's going to take loong time.

Is there a way to "unformat" it back to XFS?

Thanks in advance.

---

### Post by FormatSeize on 2011-07-07
Plug it in, then right click on the icon for it when it shows up. On the menu that pops up after right clicking it, click format. In that menu, you will find options of what type of file system you would like to format it to be. Pick the one you need, then format.
 
This works in Linux and in Windows. This happened to me yesterday at work. Someone had somehow reformated a USB to FAT16, and being that I was at work using Windows, I had to ask someone what to do. Turns out, its the same thing I would have done at home in pretty much any OS I have.

---

### Post by seawolf167 on 2011-07-07
You can either reformat the drive to your target format, or attempt to use [TestDisk ]("http://www.cgsecurity.org/wiki/TestDisk")to recover your old partition.

---

