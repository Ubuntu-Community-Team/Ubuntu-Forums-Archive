---
title: "basic system failing to boot"
date: 2009-08-02
forum: General Help
---

### Post by BMK792 on 2009-08-02
Running 32bit 9.04 with basic apps and wine. I booted the computer and it ran a scheduled filecheck and froze on /dev/sda1. ive tried running on all the versions and recovery modes but it freezes at 44% of the filecheck every time. just wondering if there is a way around the filecheck boot or if i need to reinstall.

thanks for any help

---

### Post by merlinus on 2009-08-02
IIRC, you can press Esc to bypass the automatic filesystem check.  If that does not work, try booting into recovery mode and run fsck on sda1, if it is a linux filesystem.

If ntfs, you can install ntfs-progs to troubleshoot it.

---

### Post by BMK792 on 2009-08-02
sorry I forgot to mention that when I default boot it starts and "Unclean shutdown check" which also freezes at 44% then goes to command line and prompts me to run a manual fsck which also freezes at 44%

---

### Post by merlinus on 2009-08-02
What filesystem is sda1?

---

### Post by BMK792 on 2009-08-02
when it goes to the cmd screen after the fail of the unclean shutdown driver check it says that it was a check of the root filesystem that failed, so im guessing its in root

---

### Post by merlinus on 2009-08-02
```
sudo fdisk -l
```

---

### Post by BMK792 on 2009-08-02
> **merlinus said:**
> ```
sudo fdisk -l
```


didnt work, just gave me a big table of options to do with partitions.

---

### Post by merlinus on 2009-08-02
l is a lowercase L, not the number one.

---

### Post by BMK792 on 2009-08-02
device      
/dev/sda1 

     boot        *

start 1

end 9327

blocks 74919096

ID 83

system linux

---

### Post by merlinus on 2009-08-02
Can you boot into recovery mode from the grub menu?  fsck hanging, though, is not a good sign.

---

### Post by BMK792 on 2009-08-02
When I try to boot into recovery mode it begins a force check of /dev/sda1 which also freezes at 44.3% and  then starts repeating a block of text over and over again.

---

### Post by merlinus on 2009-08-02
If you run ```
sudo fsck -V /dev/sda1
``` you might get specific errors listed.

---

