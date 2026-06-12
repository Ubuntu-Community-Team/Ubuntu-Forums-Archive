---
title: "how to expand virtual box drive?"
date: 2012-05-28
forum: General Help
---

### Post by qwertyjjj on 2012-05-28
I have a VB drive that is 10Gb, it sayd ynamically extended but I have never seen them go past 10Gb.
Does it happen automatically? When does the system decide it needs to be expanded.
I have 1Gb left and it is doing nothing yet...

---

### Post by Cheesemill on 2012-05-28
I don't think you quite understand correctly, when you create a dynamic drive of 10GB, it starts off taking up 0GB of space on your HD and will expand up to a size of 10GB as you fill it.

When you create a dynamic drive for a VM you should give the maximum size that you ever wish it to reach as a value, it will start off taking up no space and then expanding to a maximum of the size that you specified.

---

### Post by qwertyjjj on 2012-05-28
> **Cheesemill said:**
> I don't think you quite understand correctly, when you create a dynamic drive of 10GB, it starts off taking up 0GB of space on your HD and will expand up to a size of 10GB as you fill it.

10GB is the maximum size that the drive will reach.

Ah, ok.
So, I use VBoxManage to resize to 20Gb.
Does this leave an unallocated partition in the Windows guest after?

---

### Post by Cheesemill on 2012-05-28
> **qwertyjjj said:**
> Ah, ok.
So, I use VBoxManage to resize to 20Gb.
Does this leave an unallocated partition in the Windows guest after?
Yep, that's correct.

You can then either use the built-in Windows disk management tools or boot the VM from a gparted or Ubuntu Live CD if you want to increase the size of the Windows partition on the virtual disk.

---

