---
title: "rsync to flashdrive is slow"
date: 2011-11-12
forum: General Help
---

### Post by motoperpetuo on 2011-11-12
i run my backups through a script that uses rsync. if i have my flashdrive mounted, this line of code backs my Documents directory up to it:

```

rsync -azvi --delete ~/Documents/ /media/$flashdrive/Documents

```

the Documents directory is about 750mb. the first few times i ran this, the backup took less than 30 seconds to complete. now it takes over ten minutes, about as long as it used to take when i used to use cp to just copy the entire Documents directory to the flashdrive (before i discovered rsync). 

i'm not changing significantly more files than i was before or anything like that. my understanding is that rsync should only copy data from the source that has been changed to the destination. does anyone have any idea why this backup suddenly started to take so long?

---

### Post by Paddy Landau on 2011-11-14
You don't want to use -z, which compresses data on transfer. This is useful over a network, but on the same computer it causes overhead as it both compresses and decompresses the data unnecessarily.

You are correct that rsync copies only changed data.

I am unsure as to why it should suddenly go so slowly. If there is little free space on the USB flash, it could be struggling to save the data (flash disks have an interesting method of saving data in order to prolong their lifespan). Check how much space you have left on the USB flash.

---

