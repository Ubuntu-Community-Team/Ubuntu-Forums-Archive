---
title: "Using testdisk to recover partition - bad structure"
date: 2011-11-24
forum: General Help
---

### Post by rustyD on 2011-11-24
Hi All,
 
In a monent of madness I accidently deleted the wrong parition on my HD and deleted a partition with windows 7 boot files on. I had copied these files before I installed Ubuntu 11.
 
After restarting and wanting to go into Windows I then realised what I had done. I got gpart whcih couldn't find anything to restore and then testdisk.
 
I followed example from testdisk site to recover the deleted partition. Havin done a deep search all the partitions I want to write are found - there are four in total but when I select all four testdisk tells me it's a bad structure, also when I go to look at the files on the partition I want to recover testdisk says the data is corrupt. Also from the information it looks like the parttion I want doesnt end in the right place (I can provide screenshots when I get home)
 
Any help is very welcomed.
 
Also, would it be possible that if I reformat the partition and put the boot files back in that I use windows 7 disk to fix the partition?
 
I really want avoid having to reinstall indows and all my programs.
 
Thanks,
 
Rusty

---

### Post by maverickaddicted on 2011-11-24
Use this tool

[http://www.hirensbootcd.org/download/](http://www.hirensbootcd.org/download/)

It allows you to boot into mini windows xp or linux mode and is having lots of partition recovery tools.

---

### Post by rustyD on 2011-11-26
I have marked my windows 7 partition as active and been able to use the windows 7 dvd to fix the windows installation. 
However, I don't have the windows 7 bootloader option at the grub screen, THe windows 7 loader is on /dev/sda2.

How do I amend grub to add the option back?

Thanks,

---

### Post by oldfred on 2011-11-26
If it now is a bootable Windows.

```

sudo update-grub
```

---

### Post by rustyD on 2011-11-26
I had found what I needed but thanks for the reply

---

