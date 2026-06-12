---
title: "Unmounted drive information"
date: 2009-07-21
forum: General Help
---

### Post by speedkreature on 2009-07-21
Is there a way to get information about a drive/file system before mounting it?  I know that when you open Gparted, it gives you all kinds of good information about the drives while they remain unmounted, but how does one do this from the CLI?

Google is turning up irrelevant results when I search.

---

### Post by merlinus on 2009-07-21
You might try

```
sudo parted -l
```and/or

```
sudo fdisk -l
```

---

### Post by bacil on 2009-07-21
fdisk

it will give information about all partition on you hdd

---

### Post by speedkreature on 2009-07-21
Wow, you guys are fast!

Funny I was just about to reply I had figured it out and I didn't even have 5 minutes to do that.  I had practically answered my own question.  Some times I forget that nearly every GUI in Linux has a CLI back end.

Thanks for the quick reply.

I did notice though that parted -l does not give any information on the hardware RAID5 SAN attached to the server I am querying on.  Just trying to trouble shoot an issue.  The 7.5TB SAN formated with NTFS shows up as unallocated--that's a lot of data to have "disappear".

I think this question has been effectively answered.

NOTE: fdisk is, in some ways, more useful than parted.  For the example above, it was only fdisk that told me the 7.5TB file system I was hoping to mount was a GPT partition.

---

