---
title: "partition help"
date: 2009-07-23
forum: General Help
---

### Post by smapdi636 on 2009-07-23
I've got 12gb of unallocated space I'd like to split between my home and root partitions.

Is there a safe way to do this considering my current setup?  (see attached GParted screenshot)

---

### Post by zzzBrett on 2009-07-23
You can use that space, however you would have to resize all of the partitions between the unallocated space and your /home and root partitions (sda3 & sda5).

Make sure you have everything backed up, because there is a definite chance something could go wrong!

---

### Post by synapsys on 2009-07-23
You may be able to grow your extended partition into the unallocated space, then grow your home partition. You will not be able to grow your root partition as it does not border the unallocated space.

---

### Post by zzzBrett on 2009-07-23
> **synapsys said:**
> You may be able to grow your extended partition into the unallocated space, then grow your home partition. You will not be able to grow your root partition as it does not border the unallocated space.

Couldn't the OP resize partitions individually, eventually getting to the root partition?

---

### Post by mthalis on 2009-07-23
I have unallocated partition in my hard drive, I want to add that my Ubuntu system, I have only **/** and **swap** partitions, How can I do it without data loss.

---

### Post by egalvan on 2009-07-23
You can MOVE your extended partition to the "left" to butt up against sda2.
that would leave the unallocated space between the partitons you want to RESIZE.

then RE-SIZE each partition in turn.

I don't remember if it is possible to RESIZE an extended partition while still contains logical partitions.

If not, you can delete the swap, grow /sda4 and temporarily move /home into sda4,
 grow the extended, then return /home to the extended,
and re-create swap.

just remember that deleting and re-creating partitions WILL replace their current UUID.

You either want to save the UUID's, then re-write them,
 or go to the hassle of updating GRUB and fstab with the new UUID's.

What you want to do is do-able, it will just take some careful planning.

And remember that MOVING a partition can be a *very* time-consuming operation.

And one last thing...

these operations are generally safe, but

**BACK UP ANY DATA YOU DO NOT WANT TO LOSE**

---

### Post by smapdi636 on 2009-07-23
Sounds like I have my work cut out for me.

Thanks for the help!

---

