---
title: "how to identify the correct device?"
date: 2011-04-17
forum: General Help
---

### Post by ustulation on 2011-04-17
i'v 2 unmounted partitions **/dev/sda8** , **/dev/sda9** ... i do the following:

#assume sudo where applicable
mkdir /media/myMtPt
#mount sda8
mount /dev/sda8 /media/myMtPt
#mount sda9
mount /dev/sda9 /media/myMtPt
#list the mounted devices
df

if i write anything to **/media/myMtPt** it'll go to **/dev/sda9**..but both /dev/sda8 and /dev/sda9 show same mount point **/media/myMtPt**.. so if somebody else has to find out (without checking the history) to which one will the o/p go if written to /media/myMtPt then what is the way out?

---

### Post by TeoBigusGeekus on 2011-04-17
> **ustulation said:**
> i'v 2 unmounted partitions **/dev/sda8** , **/dev/sda9** ... i do the following:

#assume sudo where applicable
mkdir /media/myMtPt
#mount sda8
mount /dev/sda8 /media/myMtPt
#mount sda9
mount /dev/sda9 /media/myMtPt
#list the mounted devices
df

if i write anything to **/media/myMtPt** it'll go to **/dev/sda9**..but both /dev/sda8 and /dev/sda9 show same mount point **/media/myMtPt**.. so if somebody else has to find out (without checking the history) to which one will the o/p go if written to /media/myMtPt then what is the way out?

I think to the last mounted device (sda9 in your case).
You can't mount 2 devices on the same mountpoint - not with ext3/4 at least.

---

### Post by ustulation on 2011-04-17
> **TeoBigusGeekus said:**
> I think to the last mounted device (sda9 in your case).
ya that's the question...how do i find out that

> You can't mount 2 devices on the same mountpoint - not with ext3/4 at least.
nope..it's very possible
edit: ok i tried it with NTFS..didnt give ext3/4 a try.

---

