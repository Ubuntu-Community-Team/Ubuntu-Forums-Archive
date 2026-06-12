---
title: "Ubuntu formatted My Hard Drive"
date: 2010-09-26
forum: General Help
---

### Post by Pjstaab on 2010-09-26
I had set up space to install ubuntu 10.10 beta on but must have missed have missed the option to save that space.  Is there any way I can recover my stuff?  I don't have anything important missing, just have to rerip all my music, and download my steam games, and download gigabytes of oblivion mods.

---

### Post by efflandt on 2010-09-26
Unless you manually created/selected and checked whether to format partition(s) you wanted to install 10.10 on, you are at the mercy of whatever automatic selection you made.  In some cases testdisk can recover files or partitions, but if a new OS was installed over your data, it would be impossible to recover anything that was actually overwritten.

---

### Post by Dex73 on 2010-09-26
Sorry, if you installed an OS over the entire computer not just a partition, the data is long gone. Luckily it sounds like nothing important was lost. If anything is left it should show up as what looks like an external hard drive in the Places menu when running ubuntu off of the install cd. Just choose the try it out option. 

Does anybody know if you can also see another partition from there on an actual install? If I'm not mistaken you can.

---

### Post by Pjstaab on 2010-09-26
> **Dex73 said:**
> Sorry, if you installed an OS over the entire computer not just a partition, the data is long gone. Luckily it sounds like nothing important was lost. If anything is left it should show up as what looks like an external hard drive in the Places menu when running ubuntu off of the install cd. Just choose the try it out option. 

Does anybody know if you can also see another partition from there on an actual install? If I'm not mistaken you can.
 
Yeah all my important stuff went out with my boot drive that failed yesterday.  I was making an ubuntu partition to get by until my new drive shows up wednesday or thursday.  I wanted to listen to my music but i've been messing around with testdisk and can't manage to get anything back.  I know all my steam stuff was at the end of the drive so I should maybe be able to get that right?

---

### Post by Dex73 on 2010-09-29
> **Pjstaab said:**
> I know all my steam stuff was at the end of the drive so I should maybe be able to get that right?

Not if it has been installed over. Do you have any way of using g-parted off the install disk to see if there is a partition at the end, but it sound like it time to start re-ripping your CDs. (is re-ripping a real word?) I do wish I had better news.

---

### Post by Old *ix Geek on 2010-09-29
> **Pjstaab said:**
> I had set up space to install ubuntu 10.10 beta on but must have missed the option to save that space.Do you mean you partitioned off an area? If so, use gParted to view the partitions. It's possible that during the install you failed to assign a mount point to the partition in question, so it appears to be missing. After checking with gParted let us know what you've found.

---

