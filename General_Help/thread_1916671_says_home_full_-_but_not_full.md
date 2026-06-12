---
title: "says home full - but not full"
date: 2012-01-28
forum: General Help
---

### Post by pnguine on 2012-01-28
Hi all.

11.04 started saying my home folder is full (184.1 G) so I transferred half of it to a storage drive. Now a couple of weeks later it says it is full again but it's not (as far as I can see). When I run disk analyzer and add up the totals it's no where near 184 G and I haven't downloaded anything or even used it for anything except Firefox and Chrome.

Any ideas?

Thanks

---

### Post by drs305 on 2012-01-28
Unemptied trash (yours and possibly root's if it exists in your HOME directory) or a backup made to the wrong partition come to mind. 

Here is a guide I wrote to troubleshooting this issue:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by pnguine on 2012-01-28
Thanks. I've tried everything in your guide and the trash guide but still no luck. DiskAnalyzer and ncdu both say my home folder is full.

Here's some command output:
```
phil@harvest:~$ df -Th | grep -v "fs" | sort
/dev/sdb5     ext4     46G  7.4G   37G  17% /
/dev/sdb6     ext4    195G  185G  4.0K 100% /home
/dev/sr1   iso9660    178M  178M     0 100% /media/RCTYCOON
Filesystem    Type    Size  Used Avail Use% Mounted on
phil@harvest:~$ df -Th | grep -v "fs" | sort > diskfull.txt
sort: fflush failed: standard output: No space left on device
sort: write error

```

When I add up the sizes shown by both tools it comes to about 50G but they both say 185G. I've emptied all the trash, checked the log files, emptied the apt cache. I was thinking maybe drive error but / looks fine so it looks like it's only my user (phil) home folder that's doing this.

---

### Post by hansdown on 2012-01-29
Hi, pnguine.

Your home folder is at 100%.

Try drs305's guide, to fix the home directory.

---

### Post by pnguine on 2012-01-29
I just tried the ```
sudo touch /forcefsck
``` mentioned in one of the guides and that seems to have sorted it out. But I'm going to wait for a while before I call it solved.

---

### Post by varunendra on 2012-01-29
On a side note, your 195GB /home partition has 5% space reserved for root (default), which is equal to 9.75GB. (that's why it appears as '100%' with 185GB data on it)
> **pnguine said:**
> 
/dev/sdb6     ext4    195G  185G  4.0K 100% /home

Even though I don't usually recommend to reduce this reserved space (because so much full a partition may severely affect overall system performance, especially if it is root or /home), you can get some more space by setting it to a lower percentage of the total space using *tune2fs *command. For example, the following command would set it to 1% (1.95 GB):
```
sudo tune2fs -m 1 /dev/sdb6
```

But it is highly recommended to instead make some extra space on it to avoid performance loss.

---

