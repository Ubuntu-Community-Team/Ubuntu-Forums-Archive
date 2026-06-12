---
title: "My ubuntu 10.10 won't boot any more. Need help"
date: 2011-03-07
forum: General Help
---

### Post by toolbox1234 on 2011-03-07
I have Win 7 (1st partition), ubuntu 10 (2nd partition), 1GB swap (3rd partition) and data (4th partition). I cloned the original disk to a larger drive using Acronis under Win 7. Windows 7 starts fine and able to access the data partition. However, I can't boot into ubuntu anymore. It complains something about uuid not found. Need some hints how to get to my ubuntu installation. Thanks.

---

### Post by wilee-nilee on 2011-03-08
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by Hedgehog1 on 2011-03-08
> **toolbox1234 said:**
> I have Win 7 (1st partition), ubuntu 10 (2nd partition), 1GB swap (3rd partition) and data (4th partition). I cloned the original disk to a larger drive **_using Acronis under Win 7_**. Windows 7 starts fine and able to access the data partition. However, I can't boot into ubuntu anymore. It complains something about uuid not found. Need some hints how to get to my ubuntu installation. Thanks.

toolbox1234,

**Please don't touch the old drive yet (don't reformat it yet).**

You may need to recover your Ubuntu partitions from it.

We will know more when you post your results from the script wilee-nilee asked you to run.

***The Hedge***

---

### Post by toolbox1234 on 2011-03-08
--- deleted ---

---

### Post by wilee-nilee on 2011-03-08
Looks like your missing grub in the master boot record windows is there so from a live cd run these two commands.
```
sudo mount /dev/sda2 /mnt
```
then
```
sudo grub-install --root-directory=/mnt /dev/sda
```
reboot to the Ubuntu install and run in the terminal.
```
sudo update-grub
```

---

### Post by toolbox1234 on 2011-03-08
If I do that, will grub become by boot loader instead of Windows boot loader? I like to keep the Windows boot loader as my primary boot loader.

---

### Post by wilee-nilee on 2011-03-08
> **toolbox1234 said:**
> If I do that, will grub become by boot loader instead of Windows boot loader? I like to keep the Windows boot loader as my primary boot loader.

Yeah that makes grub the bootloader, can't help you with any other method.

I think you should consider grub2 though it is reliable and either grub or the MS bootloader can be loaded to the MBR with just a couple of commands.

---

### Post by toolbox1234 on 2011-03-08
I resolved the issue by using clonezilla to clone the ubuntu partition from my old drive to the new drive again. I guess when Acronis cloned the disk, a new uuid was created and caused grub not able to boot ubuntu. By using clonezilla, uuid is copied to the new drive and grub has no issue boot my ubuntu.

---

### Post by Hedgehog1 on 2011-03-09
toolbox1234,

Good job on recovering the partition with the original UUID.

There are often so many ways to do things... A few ways even work now and again...

***The Hedge***

:KS

p.s. wilee-nilee's solution is what I would have done, myself.  But as long as you have the boot loader you like, all is well.

---

