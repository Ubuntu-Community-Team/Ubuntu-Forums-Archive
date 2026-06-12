---
title: "Drive Space Error Message - Plenty of Room Left"
date: 2011-01-27
forum: General Help
---

### Post by fullmoonguru on 2011-01-27
I'm getting an error message that there is only 1.8 GB, or whatever, left on our servers data partition.  When I look at gparted though, there are about 95 GB showing as unused.  The error shows on the workstations and the server itself.  Any ideas?

---

### Post by fullmoonguru on 2011-01-29
Bump - Ithought this would be an easy one!

---

### Post by tredegar on 2011-01-29
> Bump - Ithought this would be an easy one!
You don't say the size of the partition, or even the filesystem being used, so most people just move on to a better question.

But ext filesystems normally reserve 5% for root's exclusive use.

See **man tune2fs**
*reserved-blocks-percentage* is probably the bit you should read carefully.

---

### Post by Rubi1200 on 2011-01-29
What does ```
df -Th
``` show you?

---

### Post by fullmoonguru on 2011-01-29
It's the sda6 partition

Output of df -Th:

```
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda4     ext4     20G  7.3G   12G  40% /
none      devtmpfs    1.6G  280K  1.6G   1% /dev
none         tmpfs    1.6G   88K  1.6G   1% /dev/shm
none         tmpfs    1.6G  412K  1.6G   1% /var/run
none         tmpfs    1.6G     0  1.6G   0% /var/lock
none         tmpfs    1.6G     0  1.6G   0% /lib/init/rw
/dev/sda6     ext4    1.7T  1.6T   31G  99% /media/Data
```

---

### Post by Rubi1200 on 2011-01-29
The output shows only 31GB free, so clearly either something is not right or you need to do something like adding a disk, houseclean, backup data to another medium etc.

---

### Post by tredegar on 2011-01-29
**/media/Data** is 1.7 TB (I guessed approx 2TB from your first post)
95 GB is about 5% of this.

So re-read post #3

You can list your reserved block allocation with
```
sudo sh -c 'tune2fs -l /dev/sda6 | grep  Reserved'
```

---

### Post by fullmoonguru on 2011-01-31
So the terminal showed 31 GB, but gParted showed 118.  Is the terminal showing the space with the reserved blocks out & gParted is leaving them in, or should they be showing the same thing?

Is there a reason I need 95 GB reserved for root access on a storage partition? (just data)

It looks like I can run tunefs -m to adjust the amount to reserve?

Well meanwhile I moved some partitions around using gParted.  Based on previous experience I figured it would take a while, but was shocked when it said 55 hrs!  I didn't want to stop it so now I'm stuck until it's done & it's taking even longer than estimated so it looks like sometime Tues. night or Wed. morning.  Crazy.  gParted is really a great tool, but you would think a message of estimated time before it started would be warranted.

From what I read, I should be using LVM to manage a disk this big.  I haven't looked at it yet.  Fortunately I can restore the data I need from CrashPlan to get some work done over the next couple of days!

---

### Post by tredegar on 2011-01-31
The terminal ( df -h) shows the space available to a normal user, and does not count root's reserved blocks as "available". This is correct behaviour.

**gparted** is primarily a partition tool, and doesn't really care how you use the space, so it reports the real "available" space. Again, this is correct behaviour.

You probably do not need reserved space on a data drive, and you can adjust it with **tune2fs** (it does not matter if you are running ext3 or ext4, **tune2fs** still works).

You should have (about) 5% reserved blocks on your / partition. Otherwise, if / becomes full, not even root will be able to login to a terminal to clean things up, and you will be completely locked out of your computer. That is why the space is reserved for root's exclusive use. The reserved space is a legacy from the days before "Live CDs", which can now be used to fix things up after all sorts of stupid mistakes.

---

### Post by fullmoonguru on 2011-01-31
Good info, thanks!

---

