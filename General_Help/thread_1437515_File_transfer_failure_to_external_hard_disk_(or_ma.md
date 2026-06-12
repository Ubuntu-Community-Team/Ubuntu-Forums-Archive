---
title: "File transfer failure to external hard disk (or maybe a crash)"
date: 2010-03-24
forum: General Help
---

### Post by parkurm on 2010-03-24
This is really a problem that will kill me.:cry:

I was transferring photos from a 16GB CF card (used in Nikon Camera) to my external 500GB hard disk. I was using a CF card reader, and both the CF card reader and the external hard disk are connected to my laptop via USB port. I am in Ubuntu 9.10.

I cut the photo folder in the CF card, and pasted it into the hard disk. After the transfer is completed, I took a look at the destination folder, and all the photos are actually there, meaning the transfer was successful.

Then I pulled out both CF card reader and external hard disk, and shut down the computer. Then when I restarted my laptop, I entered Windows Vista system, and when I checked that photo folder, there were no photos!

I though it might be a problem of different operating system, so I restarted to Ubuntu, and navigated to that folder. The folder has nothing inside either. Then I noticed that the folder has a size of 0. Here's what it looks like:
```

park@ubuntu:/media/PIC&MUSIC$ ls -l
drwx------ 3 park park 32768 2010-03-22 06:13 100322 Roosvelt 
drwx------ 0 park park     0 2010-03-23 23:31 100322 UCLA   ## The folder that I cut from CF card.
```The name of the folder I cut from CF card was initially 104ND700, and I later renamed it to 100322 UCLA. I checked the photos after I renamed it, and they were good, so renaming shall not be the cause of the problem. Question is why the folder size is 0?? Even I create an empty folder, it won't be zero. The file permission is also not a problem, since I can see all the photos in 100322 Roosvelt folder. The hard link number is 0 here, how could this happen?

Does anybody know why this is happening? The photos are really important, and I don't want to lose it simply because of a transfer.

---

### Post by Stavro on 2010-04-14
Did you ever get a solution to this problem? Perhaps you can recover the files on the memory card using deletion recovery software?

---

