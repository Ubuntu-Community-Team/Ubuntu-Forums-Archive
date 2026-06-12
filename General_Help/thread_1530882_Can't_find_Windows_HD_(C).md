---
title: "Can't find Windows HD (C)"
date: 2010-07-14
forum: General Help
---

### Post by 1Michael1 on 2010-07-14
Hello everyone, a friend of mine just installed Ubuntu side by side with his Windows XP (Dual-boot) and he can't seem to find the C disk. The only partition which is coming up is the E disk and the F disk which he got his Ubuntu system installed on.
He wants to move over his files on the C disk to the F disk and then later on delete the C partition so only got Ubuntu as an operating system.

Anyone familiar with this problem?

Thanks.

---

### Post by itachisxeyes on 2010-07-14
and its not under Places> X-number of GB Filesystem?
perhaps take a look at your partition table with gparted...you might have accidentally written over it.

---

### Post by Braik on 2010-07-14
Hi there,
 
First of all, some precisions, Linux systems do not use/name disks as letters, they mount the filesystem as a three, you will understand later maybe.
 
Your explanations (drive letters) do not help us so what you have to do is to open a terminal and type
```
fdisk -l
```
 
with an l lower case and not a one.
 
And show us the result

---

### Post by WorMzy on 2010-07-14
Is he sure that he installed them side by side, and didn't install Ubuntu as a Windows app? If he installed as a Windows app (Wubi) then his "C:\" will be located under /host.

---

### Post by 3rdalbum on 2010-07-14
> **Braik said:**
> 
Your explanations (drive letters) do not help us so what you have to do is to open a terminal and type
```
sudo fdisk -l
```

+1

Also +1 to the poster who mentioned about Wubi; your Windows drive may be available under /host if you have installed using Wubi.

---

### Post by 1Michael1 on 2010-07-14
Yeah he installed it with Wubi.
But it ain't under /home I mean, the C disk.
He choosed to install it on the F disk at Wubi.

---

### Post by WorMzy on 2010-07-14
/host, not /home.

But if he installed using Wubi, then he can't remove Windows and leave Ubuntu anyway -- Wubi depends on Windows. If you remove Windows, you remove Wubi.

Tell him to boot from the LiveCD, all the partitions should be visible from there.

---

### Post by 1Michael1 on 2010-07-14
Oh my bad, thanks a lot guys.
Solved.

---

