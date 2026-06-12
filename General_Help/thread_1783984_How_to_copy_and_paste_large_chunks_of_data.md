---
title: "How to copy and paste large chunks of data ?"
date: 2011-06-16
forum: General Help
---

### Post by leegold on 2011-06-16
Hi,

I have a home personal Ubuntu 10.04 server. I want to copy about 40GB -  to a partiton. There are two hard drives in my box one won't boot but I can aaccess it and mount partitions and I aim to move data from it to a new bootable hard drive.

Doing a simple cp copy command may not be the best way to copy and paste such a large chunk?

Also I want to backup the data I plan to copy/paste using a USB hard drive to backup. But I could also paste data from the backup to the new drive instead of from old internal hd to new hd. - that's another option.

Would a tar type command be the best way for me to accomplish this? Or just cp?

Thanks,

Lee G.

---

### Post by seawolf167 on 2011-06-16
Take a look at *rsync*

```
man rsync
```

and example command would be

```
rsync -ruv --delete-before /path/to/source /path/to/destination
```

---

