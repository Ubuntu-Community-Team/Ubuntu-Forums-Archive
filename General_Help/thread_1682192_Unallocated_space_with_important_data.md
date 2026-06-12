---
title: "Unallocated space with important data"
date: 2011-02-05
forum: General Help
---

### Post by Chethan S on 2011-02-05
I used GParted to convert a primary partition to extended one after  copying the data to another partition. After having the extended  partition I moved the data back. To my utter shock after a restart I  found out that the new extended partition did convert into "unallocated  space". I tried installing testdisk. Testdisk could  identify the partition as a primary partition and not the newly created  extended partition. So what should I do now? I badly want the data back.

---

### Post by spaceboy909 on 2011-02-06
I'll bump this for you.  Nothing worse than massive data loss.

So when you moved the data back to the extended partition, you didn't receive any errors?  It seemed to go ok?

I'm not an expert, but I've done my share of partitioning, and something sounds fishy here.

IIRC, (I could be wrong on this), you must first delete an old partition, which automatically converts it to unallocated space, after which, you then manually convert the unallocated space to an extended partition.

Do you recall going through that exact process?  If not, what were the exact steps that you took.  Also note that gparted uses a 'queue' process for executing commands, such that executing a command is a 2 step process, first selecting the desired operation, then applying it.  If one is unaware of this, it's possible to believe you executed a command when you did not.

The system wouldn't allow data to be copied to unallocated, and unmounted space (barring a serious bug), but yet it 'seems' to have done that...... Have you double checked the secondary location to make sure that it didn't fail the transfer, thereby restoring the data back to the temp location?  Triple check that!

This might sound like a long shot, but, barring a partitioning bug, it is possible, based on what you've posted, that your gparted commands never actually processed, therefore leaving you with an unmodified primary partition...........which means your data is safe.........somewhere.

Please post with more info, and also think back if you went through any process more than once.  Sometimes with computers you have to 'push it through' to get something to stick.........but partitioning is too dangerous to just 'take another whack at it' without finding out what went wrong the first time around.

---

### Post by Chethan S on 2011-02-06
I did not receive any errors anytime. In fact I had completed all the queued tasks regarding deleting the primary partition which turns to unallocated and then extending the extended partition to include this unallocated space. It was only after I created a new logical partition in this space that I was allowed to go ahead with copying the data. Anyway now I have used > testdisk and with great difficulty could get the data I had lost intact.:p

---

### Post by spaceboy909 on 2011-02-06
> **Chethan S said:**
> Anyway now I have used  and with great difficulty could get the data I had lost intact.:p
Glad to hear it!  :)

---

