---
title: "Can't unmount external hard drive w/o root, not being detected by GParted"
date: 2011-05-26
forum: General Help
---

### Post by Brushstroke on 2011-05-26
I have Seagate Freeagent Go 500GB external hard drive that I use for backup. I wanted to resize the partition so I used GParted to shrink the 500GB NTFS partition to 400GB. The other 100 I wanted to encrypt and use for some other more important files. For some reason, the shrink failed and I disconnected the hard drive and reconnected it. I didn't see the icon appear on the desktop. I went into the Disk Utility to discover that GParted's shrink error deleted all of the partitions on my hard drive. So I created a new 400GB NTFS partition and put back all of my files. The other 100 is unallocated currently. 

Now, I have another problem. It will normally mount automatically and show up on the desktop but the hard drive won't mount without me going into the Disk Utility and mounting it through there. I can't even mount it from the Terminal with root privileges. It gives me this: 

> sudo mount /media/My\ Data
mount: can't find /media/My Data in /etc/fstab or /etc/mtabNow, I can unmount with root privileges and I can unmount it from the Disk Utility. I can browse and edit the files within. But I can't unmount it from within Nautilus or on the desktop (the Safely Remove Drive option is not there). 

The new 400GB partition also isn't detected by GParted. It just shows the whole drive as unallocated. 

I have no idea what's going on here, and was hoping you guys could give a little insight. 

Thanks, 
Phil

---

### Post by Brushstroke on 2011-05-26
You can mark this solved. Somehow, it was fixed by going into GParted and recreating the partition table. It's not a big deal because I just recreated the partition and can easily put my data back on there. I'm quite a bit confused about why all of that happened, but nonetheless it works just fine now.

---

### Post by wildmanne39 on 2011-05-27
> **Brushstroke said:**
> You can mark this solved. Somehow, it was fixed by going into GParted and recreating the partition table. It's not a big deal because I just recreated the partition and can easily put my data back on there. I'm quite a bit confused about why all of that happened, but nonetheless it works just fine now.Hi, I think you are the only one that can mark it solved because you opened it.Would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.

---

