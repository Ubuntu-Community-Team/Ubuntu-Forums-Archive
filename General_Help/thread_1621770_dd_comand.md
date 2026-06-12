---
title: "dd comand"
date: 2010-11-14
forum: General Help
---

### Post by ibod on 2010-11-14
Hi all

I want to backup a partition i am having trouble with the partition is sda2 on the system drive i also have a usb drive on which i have created a folder homebackup

the problem with the partition looks like it has lost its uuid and before i creat a new uuid i would like to take a backup with dd to the usb drive whilst booted from the live cd

is the following correct, if done in the terminal having changed directory (CD) to the folder homebackup in the usb drive

ie does dd put its out file in the current directory that i am in

```

sudo dd if=/dev/sda2 of=sda2image.img

```

---

### Post by dcstar on 2010-11-15
> **ibod said:**
> 
..........
ie does dd put its out file in the current directory that i am in

```

sudo dd if=/dev/sda2 of=sda2image.img

```

Like every single other Linux command, yes.

---

