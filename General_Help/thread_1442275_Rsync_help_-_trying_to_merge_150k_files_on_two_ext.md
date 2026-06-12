---
title: "Rsync help - trying to merge 150k files on two external HDs"
date: 2010-03-29
forum: General Help
---

### Post by Dr. Cox611 on 2010-03-29
I have 2 500gb external HD's that have been getting flaky.  I bought a new 2tb external HD to hold the data from the other drives.  Here's where Murphy's Law stepped in.  I started the transfer via rsync commands in terminal.  The file structure on the 2 drives was the same so I did a merge/transfer.

```
rsync -avxr /volumes/wd500/documents /volumes/seagate500/documents /volumes/wd2tb/documents --progress

```  
About an hour or so in my spouse thought the system was too slow so she rebooted.  I now have some of the data from the 2 500gb drive in the 2tb drive

The data structure is something like /folder/subfolder/sub-subfolder/files...(it is what it is)

Now I am looking for an easy way to finish moving the data.  However, there are some folders that are empty but remain on the old drives.  Similarly, there are some subfolders that are empty.  Finally if the sub-subfolder contained 15 files, in some cases 5 remain.

I admit I only know enough about cli to do the basics.  How do I do a 1 way rsync to ensure that all the data from [wd500] is on [wd2tb]?  Ditto for [seagate500] to [wd2tb]?

Thanks!

---

