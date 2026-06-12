---
title: "i have no swap file"
date: 2011-05-01
forum: General Help
---

### Post by Gianmaria on 2011-05-01
Hi

i installed ubuntu in an hard disk with windows xp present

i did notice i have not a swap file

can i reduce my ubuntu partition  , and create a small partition for swap file ?
how can i do?
is there a partition manager in ubuntu 10.10 with a gui

with a program with gui 

thanks

---

### Post by hawthornso23 on 2011-05-01
Is this a wubi install or a proper install?

---

### Post by 3rdalbum on 2011-05-01
How much RAM have you got? If it's 2 GiB or more, you probably won't need a swap partition or swap file.

If you used one of the guided partition options (as in, NOT the manual partitioning screen where you set mount points and stuff) then the installer should have created a swap partition for you. Have you checked using the command:

```
swapon -s
```

That should tell you if there are any swaps in use. You can also try:

```
sudo fdisk -l
```

which will list partitions, and you can see if there's one formatted as "Linux swap".

---

### Post by Gianmaria on 2011-05-01
> **3rdalbum said:**
> How much RAM have you got? If it's 2 GiB or more, you probably won't need a swap partition or swap file.

If you used one of the guided partition options (as in, NOT the manual partitioning screen where you set mount points and stuff) then the installer should have created a swap partition for you. Have you checked using the command:

```
swapon -s
```That should tell you if there are any swaps in use. You can also try:

```
sudo fdisk -l
```which will list partitions, and you can see if there's one formatted as "Linux swap".
i got 4gb 32bit 
but i have not a partition for swap file
i used the cd to install ubuntu 
at the comand i get 

> Filename                Type        Size    Used    Priority

sudo fdisk -l
sadly i haven't a partition formatting for swap


thanks

---

### Post by Gianmaria on 2011-05-01
> **hawthornso23 said:**
> Is this a wubi install or a proper install?
no 
i installed via cd
thanks

---

### Post by Cotopaxi on 2011-05-01
Two comments:

1)
If you have 4GB of RAM, I think you DO NOT need a Swap file. If you did choose "automatic partitioning", as opposed to creating the partitions manually, most probably the system detected your 4 GB of RAM and did not create a Swap partition.

I am not a Linux expert, so here I am begging for feedback from other, more experienced users!

--------------

2)
There are two partition managers, both in the repositories:
1 - Gparted &
2 - Partitionmanager

If you are using Ubuntu, you will find Gparted in your Repository. However, use them with extreme care and back up your home folder, before doing anything with your partitions!

Also here, consult with more experienced users!

I hope, I helped a bit.

---

### Post by oldos2er on 2011-05-01
If you really want a swap *file* (as opposed to a partition), see [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) 'For Adding a 512MB swap'

---

### Post by hawthornso23 on 2011-05-01
> **Gianmaria said:**
> no 
i installed via cd
thanks

That really doesn't answer the question as you can do both kinds of install via CD. The question is, is your ubuntu installed on a proper separate partition, or is it simply installed on a file in windows? If the latter, then you really don't want to be mucking around with partitions as you'll hose your system.

---

### Post by Gianmaria on 2011-05-02
> **oldos2er said:**
> If you really want a swap *file* (as opposed to a partition), see [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) 'For Adding a 512MB swap'

thanks
but this makes the swap file without create a new partition , doesn't it?

---

### Post by cheapie on 2011-05-02
Yes.

---

