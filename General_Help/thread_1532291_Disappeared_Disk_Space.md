---
title: "Disappeared Disk Space"
date: 2010-07-16
forum: General Help
---

### Post by SuprDewd on 2010-07-16
I have a MySQL server running Ubuntu 8.04 and I have a 1TB disk mounted on /mnt/Disk2 which contains big database files.

The problem:

When I run "sudo du -h /mnt/Disk2" in the terminal, the last line is:

348G Disk2

This is OK, but when I run "df -ah" in the terminal, I get the following info about the disk:

FileSystem: /dev/sdb1/
Size: 946GB
Used: 663GB
Avail: 215G
Use%: 76%
Mounted on: /mnt/Disk2

Why does it say Used: 663GB when in fact, it should be Used: 348GB?

Other applications say:
GParted: 663GB
System Monitor (in file systems): 663GB
Disk Usage Analyser: 348GB
Nautilus (in properties): 348GB

I emptied /mnt/Disk2/.Trash and made sure there weren't any hidden files or folders inside.
Any ideas where my 315GBs went?

---

### Post by dcstar on 2010-07-16
> **SuprDewd said:**
> 
........
Any ideas where my 315GBs went?

Using sudo for one command and basic user privileges for the others means different answers.

---

### Post by SuprDewd on 2010-07-16
> **dcstar said:**
> Using sudo for one command and basic user privileges for the others means different answers.

This is not the case, as I can run "sudo df -ah" and results are still the same.

---

### Post by SuprDewd on 2010-07-16
By the way.

GParted (both sudo and non-sudo): 663GB
Disk Usage Analyser(both sudo and non-sudo): 348GB
Nautilus (in properties)(both sudo and non-sudo): 348GB

---

### Post by MasterProg on 2010-07-16
I can think of two other possible reasons for that:
[LIST=1]
[*]Bad sectors (but 300GB of bad sectors seem to be too much)
[*]File system metadata (if you have lots and lots or small files)
[/LIST]

---

### Post by SuprDewd on 2010-07-16
> **MasterProg said:**
> I can think of two other possible reasons for that:
[LIST=1]
[*]Bad sectors (but 300GB of bad sectors seem to be too much)
[*]File system metadata (if you have lots and lots or small files)
[/LIST]

1. How do I check for bad sectors? I know you can use fsck, but isn't that dangerous for mounted disks or something like that?
2. There are a total of 501 files on the disk. That's probably not 300GB of metadata?

---

### Post by r-senior on 2010-07-16
Don't know really, but this might help?

[http://www.walkernews.net/2007/07/13/df-and-du-command-show-different-used-disk-space/]("http://www.walkernews.net/2007/07/13/df-and-du-command-show-different-used-disk-space/")

[http://www.linuxquestions.org/questions/linux-general-1/du-vs-df-huge-difference%3B-disk-space-vanishing-539185/]("http://www.linuxquestions.org/questions/linux-general-1/du-vs-df-huge-difference%3B-disk-space-vanishing-539185/")

[http://sysunconfig.net/aixtips/df_du_diff_out.txt]("http://sysunconfig.net/aixtips/df_du_diff_out.txt")

It could be the way MySQL allocates space. I don't know much about MySQL internals but maybe it allocates space for rollback for example? I'd try shutting down MySQL and trying both commands. Restart it, see if it goes back to "normal".

---

### Post by MasterProg on 2010-07-16
Can you unmount it and use fsck?

---

### Post by SuprDewd on 2010-07-16
> **r-senior said:**
> Don't know really, but this might help?

[http://www.walkernews.net/2007/07/13/df-and-du-command-show-different-used-disk-space/]("http://www.walkernews.net/2007/07/13/df-and-du-command-show-different-used-disk-space/")

[http://www.linuxquestions.org/questions/linux-general-1/du-vs-df-huge-difference%3B-disk-space-vanishing-539185/]("http://www.linuxquestions.org/questions/linux-general-1/du-vs-df-huge-difference%3B-disk-space-vanishing-539185/")

[http://sysunconfig.net/aixtips/df_du_diff_out.txt]("http://sysunconfig.net/aixtips/df_du_diff_out.txt")

It could be the way MySQL allocates space. I don't know much about MySQL internals but maybe it allocates space for rollback for example? I'd try shutting down MySQL and trying both commands. Restart it, see if it goes back to "normal".

I went through the links and the first one was promising, but wasn't the problem. I'll try shutting MySQL down today and let you guys know if that's the problem.


> **MasterProg said:**
> Can you unmount it and use fsck?
I'll try later today and post the results.

---

### Post by SuprDewd on 2010-07-16
Turning MySQL off did not change anything.
I can't use the "badblocks" command because the disk is mounted.
I can't use fsck, also because the disk is mounted.

I'm going to backup the disk later and then unmount and check for bad sectors.

---

