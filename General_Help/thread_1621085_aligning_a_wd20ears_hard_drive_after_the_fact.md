---
title: "aligning a wd20ears hard drive after the fact"
date: 2010-11-13
forum: General Help
---

### Post by bric on 2010-11-13
After getting my components, building my computer, installing ubuntu and beginning to configure things I found out about the issues with aligning Western Digital's wd20ears 2TB hard drive.

So I'm wondering what my options are.  It's Maverick I've installed and when I go to the 'administration > disk utility' it reports a 1MB partition at the front, then 2TB partition for Ubuntu, then 25GB swap.

Can/should I be worrying about this now? Am I too late to do anything except start over (remove old partitions and create new ones beginning in the right sector?)

I read in this thread ([this thread here]("http://ubuntuforums.org/showpost.php?p=9908238&postcount=26")) a post that made me hope perhaps I'm worrying about a non-issue but I don't know enough to diagnose things (or fix) myself ... so here I am. 

Start over completely?
Fix existing install?
It's fine, just leave it alone?
Other?

---

### Post by blueridgedog on 2010-11-13
Based on a quick google, it should be good to go for Ubuntu out of the bag...the sticker on the bag also stated as much:

[http://homeservershow.com/wp-content/uploads/2010/04/DSC01249.jpg](http://homeservershow.com/wp-content/uploads/2010/04/DSC01249.jpg)

---

### Post by bric on 2010-11-14
Yeah, I read the sticker ... and I read all the postings.  However, my understanding of exactly what alignment entails is so scanty that I was still left wondering if something was not quite right.

If it's all right then that's good.

I had tried an 'fdisk -lu' as suggested elsewhere in the other thread I mentioned but it gave an error related to ... hmmmm 'guid based ' something or other.:confused:

Anyway, it left me wondering if my drive was ok or not.

Sucks being stuck on the cusp between understanding something and nothing.

Thanks for your reassurance.

---

### Post by fatbotgw on 2010-11-14
> **bric said:**
> Yeah, I read the sticker ... and I read all the postings.  However, my understanding of exactly what alignment entails is so scanty that I was still left wondering if something was not quite right.

If it's all right then that's good.

I had tried an 'fdisk -lu' as suggested elsewhere in the other thread I mentioned but it gave an error related to ... hmmmm 'guid based ' something or other.:confused:

Anyway, it left me wondering if my drive was ok or not.

Sucks being stuck on the cusp between understanding something and nothing.

Thanks for your reassurance.

maybe this will help get you on the other side of that cusp:  [http://consumer.media.seagate.com/2010/03/the-digital-den/4k-sector-hard-drive-primer/]("http://consumer.media.seagate.com/2010/03/the-digital-den/4k-sector-hard-drive-primer/")

---

### Post by srs5694 on 2010-11-15
Post the output of the following command (changing /dev/sda to whatever the relevant drive filename is):

```

sudo parted /dev/sda unit s print

```

If the Start values are all divisible by 8, then you should be fine. If not, then you may need to start again, although it's conceivable that some careful move/resize operations will fix the issue. I don't know offhand if WD's partition alignment software works with Linux filesystems. I certainly wouldn't trust it with any important data, though.

---

### Post by bric on 2010-11-15
Thanks fatbotgw for the overview of the basics. That puts my head on straight about the why.

And thanks srs5694, that's what I was looking for (something to test/confirm and offer more concrete reassurance).

This output seems to indicate that I am indeed okay. Hooray!

```
Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sda: 3907029168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start        End          Size         File system     Name  Flags
 1      2048s        4095s        2048s                              bios_grub
 2      4096s        3857881087s  3857876992s  ext4
 3      3857881088s  3907028991s  49147904s    linux-swap(v1)

```

---

### Post by srs5694 on 2010-11-17
Yup, it looks fine to me, too.

---

### Post by HandeH on 2011-04-07
What does it mean that fdisk -l outputs: 
Partition 1 does not end on cylinder boundary.

The Benchmark of Disk Utility gives about 94 MB/s as Average Read Rate. I'm using 10.04. Here is the whole output: 
```

Disk /dev/sda: 2000.4 Gt, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = 1 * 512 = 512 [byte long] sectors
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Device      Boot     Start   End         Blocks     Id  System
/dev/sda1   *        2048    70130335    35064144   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2        70130336    77143367     3506516   82  Linux-swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3        77143368  3907029167  1914942900   83  Linux
Partition 3 does not end on cylinder boundary.
```

---

### Post by srs5694 on 2011-04-07
HandeH, ordinarily it's best to start a new thread for a new problem rather than hijack an existing thread. This thread is quite old, so it's not as bad in this case, but starting a new thread is still preferable. I suggest you do so, explicitly state what problem you're experiencing, make it clear what type of hard disk you're using, and post the output of "sudo fdisk -lu /dev/sda" to your new thread. (Note that's "-lu", not "-l"; the latter is insufficiently informative.) To answer your explicit question, the "does not end on cylinder boundary" warning is completely useless today; it refers to alignment practices that have been pointless for over a decade. You can and should ignore this warning.

---

### Post by HandeH on 2011-08-15
Hi,
thanks for the answer. Actually, the output above is the same as the output of: ```
~$ sudo fdisk -lu /dev/sda
```My mistake. The hard drive is stated on the topic. 

Those confusing, depricated warnings do not show when you use the recommened -c option (ie. Switch off DOS-compatible mode): 
```
sudo fdisk -luc /dev/sda
```

---

