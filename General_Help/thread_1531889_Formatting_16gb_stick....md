---
title: "Formatting 16gb stick...???"
date: 2010-07-15
forum: General Help
---

### Post by robertcoulson on 2010-07-15
Hi...Used "testdisk" to remove all my valuable pictures and data from my 16gb stick....Could not access it in Linux or Windows...Now how do I "reformat" it.... Every time I try to get to it or right/left mouse it comes up with the error (see attached)...Does anyone have any solutions...???
Thanks
Robert

---

### Post by bodhi.zazen on 2010-07-15
I format from the command line

```
mkfs.ext4 /dev/sdb1
```

Use gparted if you want a graphical interface.

To see if you can determine the nature of that error, run fsck

```
fsck /dev/sdb1
```

---

### Post by robertcoulson on 2010-07-15
I did try "fsck /dev/sdb1 " many times and got no where...Will gparted work to format the stick....??
Robert

---

### Post by bodhi.zazen on 2010-07-15
> **robertcoulson said:**
> I did try "fsck /dev/sdb1 " many times and got no where...Will gparted work to format the stick....??
Robert

I do not know, perhaps if you described the problem or posted the output.

What is wrong with the stick ? It may be a hardware problem.

---

### Post by robertcoulson on 2010-07-15
Dom't think it is a hardware problem with my computer...tried Ubuntu, Windows and a different Ubuntu machine...Get the same error...Maybe Gparted might work..Will try it..Thanks
Robert

---

### Post by bodhi.zazen on 2010-07-15
> **robertcoulson said:**
> Dom't think it is a hardware problem with my computer...tried Ubuntu, Windows and a different Ubuntu machine...Get the same error...Maybe Gparted might work..Will try it..Thanks
Robert

Hardware problem meaning your flash drive has died and needs to be replaced.

---

### Post by robertcoulson on 2010-07-15
Oh...Ya, you could be right....Oh well, too small to make it a boat anchor (ha,ha).
Thanks
Robert

---

