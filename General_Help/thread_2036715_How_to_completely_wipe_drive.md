---
title: "How to completely wipe drive?"
date: 2012-08-02
forum: General Help
---

### Post by Nickehh on 2012-08-02
Super ubuntu noob needs a fast way to completely wipe drive. I saw someones guide to using "wipe" but the eta is 9w 6d... :S

---

### Post by YankeePride13 on 2012-08-02
Easiest way for a noob is to just use the Ubuntu disk to format the drive.

---

### Post by Cheesemill on 2012-08-02
Just do:
```
sudo dd bs=4MB if=/dev/zero of=/dev/sdX
```where sdX is the drive you want to wipe.

[SIZE=2][COLOR=Red]PLEASE MAKE SURE YOU SPECIFY THE CORRECT DRIVE AS THIS WILL OVERWRITE THE DISK WITH 0's MAKING RECOVERY IMPOSSIBLE[/COLOR][/SIZE]

---

### Post by Cheesemill on 2012-08-02
> **YankeePride13 said:**
> Easiest way for a noob is to just use the Ubuntu disk to format the drive.

This doesn't wipe the drive, it just deletes the pointers to the files.
Data can be easily recovered using this method.

---

### Post by Nickehh on 2012-08-02
sudo dd bs=4MB if=/dev/zero of=/dev/sdX

So, the only part I have to change is /sdX?

---

### Post by zero2xiii on 2012-08-02
> **Nickehh said:**
> sudo dd bs=4MB if=/dev/zero of=/dev/sdX

So, the only part I have to change is /sdX?

Yep,

But as OP stated. This is inrecoverable. Make VERY sure about the device you are formatting. 

Unplug all the other drives and do this from a live CD. That way, you can not screw up :)

Cherz

---

### Post by audiomick on 2012-08-02
> **zero2xiii said:**
> 
Unplug all the other drives and do this from a live CD. That way, you can not screw up :)

Cherz

Good advice.

---

