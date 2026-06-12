---
title: "how to make a logical partition primary.."
date: 2010-04-08
forum: General Help
---

### Post by rudi009 on 2010-04-08
i'm trying to install windows 7 and after googling around found that marking the partition as primary would do the job.. so how to do it??? thanks in advance

---

### Post by Chame_Wizard on 2010-04-08
You can use the live CD/DVD or USB,to install Gparted.

After that,you can make a primary partition.:P

---

### Post by Mark Phelps on 2010-04-09
> **rudi009 said:**
> i'm trying to install windows 7 and after googling around found that marking the partition as primary would do the job.. so how to do it??? thanks in advance

Unless I misunderstand you, you're asking how to change a Logical partition into a Primary one.

You can't do that because a Logical partition exists inside an Extended partition, and a Primary partition can NOT do that.

You would have to Create a new Primary partition outside the Extended partition.

---

### Post by sisco311 on 2010-04-09
> **Mark Phelps said:**
> Unless I misunderstand you, you're asking how to change a Logical partition into a Primary one.

You can't do that because a Logical partition exists inside an Extended partition, and a Primary partition can NOT do that.

You would have to Create a new Primary partition outside the Extended partition.

It's possible, but it's risky & not recommended without a very good reason.

OP:

Please post the output of:
```
sudo fdisk -l
```

---

### Post by srs5694 on 2010-04-09
> **Mark Phelps said:**
> Unless I misunderstand you, you're asking how to change a Logical partition into a Primary one.

You can't do that because a Logical partition exists inside an Extended partition, and a Primary partition can NOT do that.

You would have to Create a new Primary partition outside the Extended partition.

It is possible *if* the partition to be converted is the first or last in the extended partition *and* if there's room for another primary partition. The data structure manipulation is pretty trivial, in fact, although any error could result in loss of data (in a worst-case scenario, all the logical partitions might become inaccessible). That said, I don't know offhand if GParted can do the job. I'm sure it could be done with sfdisk. It can also be done in a roundabout way with my GPT fdisk, but I don't recommend doing it this way if there are any other options.

---

