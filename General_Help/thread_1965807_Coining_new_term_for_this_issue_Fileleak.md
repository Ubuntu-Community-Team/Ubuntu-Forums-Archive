---
title: "Coining new term for this issue: Fileleak"
date: 2012-04-26
forum: General Help
---

### Post by s_aldinger on 2012-04-26
Yes, like a memory leak but on the hard drive... 

OK, I am using 2 SSDs 30GB on a **hardware** raid 1 formatted with ext4

```
fstab: 
UUID=ebed5996-4efe-4b21-b3e5-7038ad07da7c       /                                               ext4    noatime,discard,errors=remount-ro               0       1
```Total disk use for** ALL** files on the drive is ~30GB. Typically with in 1 or 2 days something happens overnight that causes the whole drive to fill up **100%**

```
 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              99G   94G     0 100% /


```_***NOW LET ME MAKE THIS VERY VERY CLEAR. THERE ARE NO NEW FILES, OR OLD ONES ANY LARGER!***_

Deleting an ISO ~4GB in size to make some room df -h will report

```
df -h                                                                                                                                                                                                              
Filesystem            Size  Used Avail Use% Mounted on                                                                                                                                                                                             
/dev/sdb1              99G   94G  8.0K 100% /                  
```K, wtf...?

So I load up Filelight to see what ***is*** taking up all that space. At root filelight says "/" is 100% used. OK good. All is as expected. Diving down into the actual file-scan to see what is using that space, reports that only ~30GB is being used. That's only 1/2 of the space!

Are we confused yet? It gets better!

If I reboot the system, it clears the error, and I have magically regained all my free space back!!!

And no, the system isn't usable when this happens.

```
touch test
touch: cannot touch `test': No space left on device 

```So if you will excuse me, I need to go reboot.

Fellow geeks, please have at it!  :popcorn:

---

### Post by pqwoerituytrueiwoq on 2012-04-26
i don't think trim works when in a raid array and the drive is probably thinking it is full as a result
i read about a trick for this you can lean the machine sitting in the bios so there is no activity on the ssd and it will trim itself (read this in a newegg review the other day)

if that is not the cause i would suggest checking your /var/log folder for multi gig files

---

### Post by s_aldinger on 2012-04-26
> **pqwoerituytrueiwoq said:**
> i don't think trim works when in a raid array and the drive is probably thinking it is full as a result
i read about a trick for this you can lean the machine sitting in the bios so there is no activity on the ssd and it will trim itself (read this in a newegg review the other day)

if that is not the cause i would suggest checking your /var/log folder for multi gig files




Yes, it does look like that is the case. It appears like the latest kernel has a [patch]("https://lkml.org/lkml/2012/3/11/261") as of Mon, 12 Mar 2012. 

All my cache and tmp files are written to a RAM drive. So what the heck is there to trim?
Something is causing 30GB of disk changes. Anything writing **that** often to the hard disk would kill any drive in a matter of months... It would be a really big problem for **everyone**. 

Does anyone know of a good way to profile the i/o use to a hard drive for all process over the course of say 12 hours?

---

