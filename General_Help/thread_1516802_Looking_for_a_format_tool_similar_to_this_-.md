---
title: "Looking for a format tool similar to this - ?"
date: 2010-06-24
forum: General Help
---

### Post by aaronmarsh632 on 2010-06-24
Hi,

I use this tool on windows [http://hddguru.com/software/2006.04.12-HDD-Low-Level-Format-Tool/](http://hddguru.com/software/2006.04.12-HDD-Low-Level-Format-Tool/) for low level formatting hard drives.

I have been looking for a tool like this for ubuntu but having now luck.

I read on another thread that I can use this command - sudo dd if=/dev/zero of=/dev/sdx

will that work aswell? if so is there a front-end available for it?

Thanks

---

### Post by dabl on 2010-06-24
The "dd" command is probably what you need.

[http://kubuntuforums.net/forums/index.php?topic=3090824.0](http://kubuntuforums.net/forums/index.php?topic=3090824.0)

I don't know of a GUI frontend for it.

If you use "dd" to wipe the MBR, then a very handy tool to make a new partition table and new partition(s) is the Parted Magic Live CD, from here:  [http://partedmagic.com/download.html](http://partedmagic.com/download.html)

---

### Post by MCVenom on 2010-06-24
The dd command is what I always use; but make sure you add 'BS=1MB' to the end of that command, otherwise it takes thrice as long.

For repartitioning you can use a dedicated GParted LiveCD, or use GParted from the Ubuntu Desktop LiveCDs. Of course, personally I like to do the formatting and repartitioning using a Knoppix LiveDVD, its useful for nearly anything. :D

---

### Post by aaronmarsh632 on 2010-06-24
Thanks guys.
Just 1 question - what does the 1mb at the end mean? and will for example putting 2mb, 3mb do a more thourugh job? I understand that this would take longer

thanks

---

### Post by dabl on 2010-06-24
"bs" = block size in bytes.  You really need to study the command and make sure you know what you're doing before you launch it.  The alternative name for "dd" is "Data Destroyer".  ;)

---

### Post by aaronmarsh632 on 2010-06-24
I see, thanks for the info, you've both been very helpful

---

### Post by MCVenom on 2010-06-24
As has been said, it means block size. All I can really say is that the default is 512 KB, and when I made the mistake of accidentally leaving out the 'BS=1MB'... it took most of the day to finish. :P

---

