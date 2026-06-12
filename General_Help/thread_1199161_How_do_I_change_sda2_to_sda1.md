---
title: "How do I change sda2 to sda1?"
date: 2009-06-28
forum: General Help
---

### Post by Flash858 on 2009-06-28
I initially had 4 partitions on a drive, with 9.04 on sda2. From a live Gparted CD, I deleted sda1 and sda3 (NTFS), and gave Ubuntu the entire disc, save sda4, which is a 4GB Linux swap.

Is there a way to change the Partition to sda1?

In the fstab, the partitions are listed by the uuids, and everything boots fine, and additionally, there is a commented out line stating that upon install, the partitions were what they are now (sda2, and sda4 for the swap).

Please advise, as it is making me kind of crazy...

Thanks in advance...

---

### Post by moster on 2009-06-28
If I understan correctly, you want to move linux installation to first partition on HDD. hm, well it can be done of course, but I gave up on that and do another clean installation.

That is just my choice, you can wait here or try to find solution, but it is not that easy.

---

### Post by michy99 on 2009-06-28
I think you would have to edit the partition table, but I don't know how to do it.

---

### Post by lloyd_b on 2009-06-28
You can do this via the "fdisk" program.  Start the fdisk program ("sudo fdisk /dev/sda", hit "x" to enable "expert" commands, type "f" to "fix" (renumber) your partitions, and then "w" to write them.

Note that I've never tried this - I'd *strongly* recommend that you have a backup of any important data first...

Lloyd B.

---

### Post by Flash858 on 2009-06-28
Maybe I wasn't clear. I had 4 partitions, I deleted 1 and 3, so I am left with 2 and 4, with 2 taking the space left by 1 and 3.

Sooooo....Currently, I have an sda2 and an sda4. I simply want to change them to sda1 and sda2 respectively. That's it, no moving of data involved here, I already did that. Just want to rename the partitions so they are orderly.

Thanks.

---

### Post by lloyd_b on 2009-06-28
> **Flash858 said:**
> Maybe I wasn't clear. I had 4 partitions, I deleted 1 and 3, so I am left with 2 and 4, with 2 taking the space left by 1 and 3.

Sooooo....Currently, I have an sda2 and an sda4. I simply want to change them to sda1 and sda2 respectively. That's it, no moving of data involved here, I already did that. Just want to rename the partitions so they are orderly.

Thanks.

The instructions I gave were for doing exactly that.  "Fixing" the partitions just changes them so that you would have "sda1" and "sda2", rather than "sda2" and "sda4".  It does not (or rather, *should* not) affect the sizes/locations of the partitions in any way, it just resets the "partition numbers", which is what causes them to show up as "sda2" and "sda4".

Lloyd B.

---

### Post by Flash858 on 2009-06-28
I had already tried that Lloyd - It just gave me the "nothing to do" output, saying the partitions were already ordered correctly. That's why I thought maybe it had something to do with the fstab...<P>
There has GOT to be a way to do this...

---

### Post by merlinus on 2009-06-28
Post results of:

```

sudo fdisk -l
df -h
cat /etc/fstab

```

---

### Post by Flash858 on 2009-06-28
Fixed it with gparted by adding another partition. Puppy is now on sda1, but at least things are orderly now...

---

### Post by fashizzlepop on 2010-02-24
Sorry if this is a necro, but I had this problem until I googled it and this was the first page to come up so I believe it's useful.

One possibility it to use gparted to "copy" it to a new partition, then delete the original and move it to the front. It automatically names it sda1.

---

