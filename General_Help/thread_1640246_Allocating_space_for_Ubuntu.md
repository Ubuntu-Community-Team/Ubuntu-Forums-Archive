---
title: "Allocating space for Ubuntu"
date: 2010-12-07
forum: General Help
---

### Post by Maaku on 2010-12-07
During the installation, I only gave Ubuntu 4 GB of space to work with. Now, I have started to get used to Ubuntu and have started to put work on it because I can rely on it not really breaking all the time, I feel I need to give it some more space.

How do I do this? I have done some searching, but I am not entirely sure how this whole thing works. Does Ubuntu have it's own partition? If so, how do I give more space to it?

I am dual-booting with Windows Vista and installed Ubuntu through a live CD. I am using Ubuntu 10.04 Lucid Lynx.

---

### Post by pizza-is-good on 2010-12-07
Yes, Ubuntu has its own partition. 

Go to Windows. Defrag.

Then boot live CD. Open GParted (System>>Administration>>GParted).
Click on your windows partition. Resize it to whatever you want. Then click on Ubuntu's partition, drag it to the left.
Click the green check mark atop the program to apply. You are done! Boot into Ubuntu and enjoy the extra space.

Oh, and by the way, BACKUP! Always, before you mess with partitions, you need to do a backup of everything you would regret loosing, both in windows and in ubuntu.

If you need help along the way, just ask.

~pizza

---

### Post by Maaku on 2010-12-07
> **pizza-is-good said:**
> Yes, Ubuntu has its own partition. 

Go to Windows. Defrag.

Then boot live CD. Open GParted (System>>Administration>>GParted).
Click on your windows partition. Resize it to whatever you want. Then click on Ubuntu's partition, drag it to the left.
Click the green check mark atop the program to apply. You are done! Boot into Ubuntu and enjoy the extra space.

Oh, and by the way, BACKUP! Always, before you mess with partitions, you need to do a backup of everything you would regret loosing, both in windows and in ubuntu.

If you need help along the way, just ask.

~pizza

Thanks for your very informative response. I am not sure how you do a backup in Ubuntu. I did download this application called Simple backup, but it does not seem to be working.

---

### Post by pizza-is-good on 2010-12-07
No problem.

Simple backup never worked for me either. I use luckyBackup in Ubuntu. It is very easy to use.

~pizza

---

### Post by Maaku on 2010-12-07
> **pizza-is-good said:**
> No problem.

Simple backup never worked for me either. I use luckyBackup in Ubuntu. It is very easy to use.

~pizza

Okay, I'll download that now and do what you said in the second post. Thanks for your help, pizza-is-good.

---

### Post by pizza-is-good on 2010-12-07
Hope everything works fine. Let us know how it went.

~pizza

---

### Post by Maaku on 2010-12-08
I am not entirely sure which partition Ubuntu and Windows are on.

Here is a screenshot. I think Windows could be on sda2, and Ubuntu is on sha3. How can I check to make sure this is the situation?
[IMG]http://i56.tinypic.com/2q04z1l.png[/IMG]

---

### Post by Maaku on 2010-12-09
Okay, so I think Ubuntu is on /dev/sda5/. The thing is, I cannot move it or increase it. It just gives me the option of "New". What do I do? Any help is appreciated.

---

### Post by Maaku on 2010-12-15
Really need help with this. Bump.

---

### Post by pizza-is-good on 2010-12-15
OK, I'm back. Sorry, I had forgotten about this thread...

The screen shot didn't post correctly, so I cannot see it. Please try again.

Also, if you could, open up a terminal and type:
```
sudo fdisk -l
```and post the output of that command here.

Also, just checking, you are in the LiveCD when you are trying to do this correct?

---

### Post by Maaku on 2010-12-22
> **pizza-is-good said:**
> OK, I'm back. Sorry, I had forgotten about this thread...

The screen shot didn't post correctly, so I cannot see it. Please try again.

Also, if you could, open up a terminal and type:
```
sudo fdisk -l
```and post the output of that command here.

Also, just checking, you are in the LiveCD when you are trying to do this correct?

I think so, I am using the CD you use to install Ubuntu and go into the demo; and then from there I open GParted. Here is the output produced by that command:
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfda59a3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1529    12281661   12  Compaq diagnostics
/dev/sda2   *        1530        4904    27109524    6  FAT16
/dev/sda3            4905        8664    30202200    7  HPFS/NTFS
/dev/sda4            8665        9730     8551425    5  Extended
/dev/sda5            8665        9678     8135680   83  Linux
/dev/sda6            9678        9730      414720   82  Linux swap / Solaris

```

---

