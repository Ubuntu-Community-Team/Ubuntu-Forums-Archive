---
title: "Can't dual boot"
date: 2012-06-05
forum: General Help
---

### Post by Chpunk on 2012-06-05
Everytime I try to install the newest version of ubuntu desktop I never get the option for installing along side windows 7. Also in the GParted disk program it says "ubuntu unable to satisfy all constraints on the partition". I have an Asus laptop and there's 4 hard drive partitions. In order of biggest to smallest drive (d) os(c) recovery and healthy. I deleted the data one and shrunk the C drive which was combined with the d drive. There's about 120 gb unallocated. So what should I do? If any more details are needed let me know.

---

### Post by madverb on 2012-06-05
If there are already 4 primary partitions you can't add any more. You need one of the 4 to be an extended partition.

---

### Post by Chpunk on 2012-06-05
I deleted one already

---

### Post by wilee-nilee on 2012-06-05
> **Chpunk said:**
> Everytime I try to install the newest version of ubuntu desktop I never get the option for installing along side windows 7. Also in the GPR disk program it says "ubuntu unable to satisfy all constraints on the partition". I have an Asus laptop and there's 4 hard drive partitions. In order of biggest to smallest drive (d) os(c) recovery and healthy. I deleted the data one and shrunk the C drive which was combined with the d drive. There's about 120 gb unallocated. So what should I do? If any more details are needed let me know.

GPR or GPT, can you explain GPR if it is.

---

### Post by madverb on 2012-06-05
Are you sure one of the other partitions isn't an extended partition?

---

### Post by Chpunk on 2012-06-05
Right now the partitions are efi system partition 200mb, recovery 24.41 gb. OS(C:) 323.84 gb which is using some of the space previously used the Data partition. There's 117gb unallocated because I deleted the Data partition and used some of it for the OS partition

---

### Post by oldfred on 2012-06-05
If you have gpt and are booting in UEFI mode, you do not have extended partition nor logical partitions. All gpt partitions are primary.

But if gpt and UEFI booting Windows you need to install Ubuntu in UEFI mode. You have to partition in advance (and backup efi partition) and use UEFI to boot efi mode from liveCD or USB. 

Backup efi partition as there was a bug where grub2's installer overwrite the efi partition. I think it has been fixed but better to be safe. And it may depend on exactly which version you install whether you have all the fixes.

---

### Post by Chpunk on 2012-06-05
Sorry there was a typo, GPR was supposed to be GParted. So far I've opened up Gparted on the LiveCD demo, and it gave me that error about not satisfying constraints.

---

### Post by oldfred on 2012-06-06
Post this:

sudo parted /dev/sda unit s print
sudo blkid -c /dev/null -o list

---

