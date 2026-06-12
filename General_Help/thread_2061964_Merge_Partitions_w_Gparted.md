---
title: "Merge Partitions w Gparted"
date: 2012-09-23
forum: General Help
---

### Post by euphoric_anomaly on 2012-09-23
I was wondering if there was a way to merge the 19GB filesystem with the current Ubuntu partition?

---

### Post by Bashing-om on 2012-09-23
euphoric_anomaly;
 Hello; Sure, as the 19 Gigs is free (unallocated) I expect it to be a simple process.
Be aware ...Murphie's law always applies.....Back up important data before altering any partitions.
  Further advice pends on results from in a live cd (no mounted partitions):
```
sudo fdisk -lu
sudo parted -l
```[those are lower case "L"'s] ..and a screen shot of GParted (from live cd) as a graphical aid would be helpful also.
 We then know the current partitioning layout of the disk involved.

[INDENT][INDENT]Kind regards <==BDQ

[/INDENT][/INDENT]

---

### Post by jerrrys on 2012-09-23
Think you need to resize that partition

[http://gparted.sourceforge.net/docs/sw-req-spec/C/Software_Requirements_Specification_-_GParted.pdf](http://gparted.sourceforge.net/docs/sw-req-spec/C/Software_Requirements_Specification_-_GParted.pdf)

chapter 3.12

---

### Post by agillator on 2012-09-23
As bashing-om said, it 'should' be a simple process. The specific steps I would follow were I you:

1.  Backup anything you can't or wouldn't want to replace.

2. When you mess with partitions it is entirely  possible that the master boot record and GRUB will end up invalid. That  should not happen in this case but one never knows. Replacing/updating  /repairing GRUB is not difficult (I have had to do it several times) but  I cannot remember the steps right now so look them up (a search for  'Ubuntu repair GRUB2 ' should get you there) and be sure you are  comfortable with them. Printing them out would be a good idea.

3. Boot into the Ubuntu live CD and run gparted.

4. Make sure the 19GB free space you want to expand into immediately follows the partition you want to expand. If not, the procedure will be different. Tell us the situation and we will give you further instructions.

5. Now, the easy part. Select the partition in use, tell gparted to expand its size to include the 19GB free space, acknowledge the warning it will probably give you about booting and GRUB, apply and be patient. 

You should actually have no problems. The instructions are more complicated than the process, but such are instructions. If this is the first time you have used gparted, take a look at it and get comfortable with it. It is a very powerful (and therefore dangerous) tool that allows to do all sorts of things, including screw up your entire hard drive with no effort at all! Be cautious when using it, but don't be afraid to use it when appropriate.

---

