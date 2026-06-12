---
title: "How to remove unused swap files."
date: 2010-07-12
forum: General Help
---

### Post by LiamCH on 2010-07-12
According to System Monitor, my hard disc has a total size of 107.2 GiB, of which 6.7 GiB is "Free" and 1.3 GiB is available. I'm not sure if this is normal or not, though I know at least part of this wasted space is taken up by at least two failed attempts at creating Swap Files. Ubuntu says I have no Swap space whatsoever, so is there any way I can delete all these failed and unconnected Swap Files so that I could free up some space, and hopefully create one working one?

Thanks,

Liam.

---

### Post by TechBeastie on 2010-07-12
If full-blown "files" were actually created during that process, you might try something like ```
 du -a / | sort -n 
``` which should show you a list of all the files on your system, ordered by size.  Either way, this approach might help you find other large files that you can scrap.  

Also keep in mind that journaling file systems use some small percent of any given disk for index storage and so forth, so that *might* be another factor contributing to the disparity you're seeing in use statistics.  That's really just a guess, however, since I'm definitely not an expert on journaling filesystems.

---

### Post by LiamCH on 2010-07-12
Thanks for that. To be honest, I'd rather not go deleting files - no matter how large - without knowing their purpose. Does anyone know which folder I would find the files in, and possibly what they're called?

Thanks very much for that command though; I'm sure that will be very useful in clearing out my computer someday soon!

---

### Post by ibrabeicker on 2010-07-12
download gparted, burn it into a cd, reboot and extend your partition to these failed swap areas

although this is risky

---

### Post by ibrabeicker on 2010-07-12
download gparted, burn it into a cd, reboot and extend your partition to these failed swap areas

although this is risky

---

