---
title: "ext4 vs reiserfs"
date: 2010-05-16
forum: General Help
---

### Post by jee_bee on 2010-05-16
I just read about reiserfs bein way faster than ext4...
im instaling lubuntu 10.04 on a pentium 4 3.06 ht 512ram
ide 150g  this distro will be use ONLY for running a small counter strike source server
the system already ave ubuntu on ext4 and win7  ......
SOOO my question are..  1-Can in instal my distro on a reiserfs?
                        2-is it better ??
                       3-is this different fromother file system
             i mean can it be logical ?

any other info will be apreciate !!!! thk !!!!!! a+

---

### Post by abcuser on 2010-05-16
There is probably difficult to say that one file system is faster then other it just needs to be done some performance tests. But I see your computer is very old one and if you will not do any heavy I/O you will most probably benefit more if you buy more RAM. Try to execute "vmstat 1 1" from terminal and find out if I/O is a problem. Is there any swapping (then RAM is a problem)?

---

### Post by jee_bee on 2010-05-16
the machine ave pc3200 400mgz add is near the retirement house...
not a single penny will go on that...
will it be better for me to ave reiserfs  or instal my os on ext4 and create a small partition for all my gaming server stuff  ??
thx !!!!!

---

### Post by uRock on 2010-05-16
512 RAM is plenty for Lubuntu. As far as the files system, I am not sure.

---

### Post by jee_bee on 2010-05-16
I'M looking at my lubuntu instaler and waitin for a awnser..........

---

### Post by uRock on 2010-05-16
> **jee_bee said:**
> I'M looking at my lubuntu instaler and waitin for a awnser..........
Just pick one and go. I personally prefer to stick with the defaults. Otherwise you may be looking at that screen for a while.

---

### Post by Man From Dirt on 2010-05-16
In my own experience, I find reiser to be slower than ext4. But I've heard good things about btrfs.

---

### Post by cascade9 on 2010-05-16
For a gaming server, its not going to make much differnce, if any at all, if the filesystem is a little faster.

BTW, any speed you might gain from a faster filesystem will be lost if you dual-boot and put ubuntu on the end of the drive.

---

### Post by jee_bee on 2010-05-16
thxX!! il go with ext4 as usual...   GO HabS GO FRM MTL
      


    in love with my new [COLOR="Blue"]wrt610n[/COLOR]

---

### Post by jackhe22 on 2010-05-16
Good lord, I haven't used ReiserFS since Linspire!

---

