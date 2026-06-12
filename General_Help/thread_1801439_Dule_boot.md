---
title: "Dule boot"
date: 2011-07-10
forum: General Help
---

### Post by Missi0n on 2011-07-10
I have had Xubuntu installed on my notebook for a while. i decided i needed to use XP to run some programs i used a while back

I've partitioned the drive and used half of it for XP, however when i boot up it just goes strait into xp

I know there's probably an obvious solution but i have no idea how to get some sort of grub up which will give me the options to choose which i boot into?

---

### Post by Missi0n on 2011-07-10
Can any one help me? :confused:

---

### Post by Rubi1200 on 2011-07-10
You probably need to reinstall GRUB to the MBR from the sounds of it:
[https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files](https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files)

Make sure to install to the MBR of the main drive e.g. sda and to use the "boot" install command not the "root" command if you are using 11.04

---

### Post by Missi0n on 2011-07-10
okay i followed the instructions.

```

/usr/sbin/grub-setup: warn: Embedding is not possble. GRUB can only be installed in this setup using blocklists. However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists

```

How am i meant to install it if i cant use blocklists?

---

### Post by Missi0n on 2011-07-10
Can any one help?

---

### Post by Missi0n on 2011-07-10
can some one help please?

---

### Post by Rubi1200 on 2011-07-10
That message means you are trying to install to the partition and not the drive (which I did say you should not do).

I cannot guess as to where your Ubuntu installation is so please provide the following information from the LiveCD:

```
sudo fdisk -l
```

(lowercase L not 1)

This will show us where the partitions are and then I can give you the specific commands to reinstall.

---

### Post by Missi0n on 2011-07-11
> **Rubi1200 said:**
> That message means you are trying to install to the partition and not the drive (which I did say you should not do).

I cannot guess as to where your Ubuntu installation is so please provide the following information from the LiveCD:

```
sudo fdisk -l
```

(lowercase L not 1)

This will show us where the partitions are and then I can give you the specific commands to reinstall.


No i was alwayes selecting the right partition which was

```

/dev/sda1

```

After fresh installing ubuntu over the original partition i found that in the Gpart there was a "boot" flag next to the Windows partition and not the Xubuntu partition, i edited the Xubuntu partition's tag to Boot and now the computer displays the Xubuntu Grub screen on bootup with the option to boot into XP

---

