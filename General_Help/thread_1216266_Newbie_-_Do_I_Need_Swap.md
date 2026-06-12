---
title: "Newbie - Do I Need Swap"
date: 2009-07-18
forum: General Help
---

### Post by Quarkrad on 2009-07-18
At the moment I do not have a swap partition - I have googled and think I do not need one but I'm not sure.  I have 2GB RAM and typically use about 18% of it so perhaps I'm alright.  I have actually created a 4GB partition on my HD (sda12) for swap but Ubuntu does not see/use it.  I am a light user and doubt whether I will every use an app that needs more memory.  I can see the logic of how to set up (I think I do!) a swap page but it is going to be painful - do I really need to get ubuntu (9.04) to see/use a swap page/partition?

---

### Post by ibutho on 2009-07-18
4GB of swap is a lot IMHO. In your case, you can get away with 512MB to 1GB of swap space. If your RAM usage is not very high, then there probably is no need for swap space although enabling it won't hurt.

---

### Post by earthpigg on 2009-07-18
> I have 2GB RAM and typically use about 18% of it so perhaps I'm alright. 

that conclusion sounds correct to me!

---

### Post by Quarkrad on 2009-07-18
Thanks - I'll stick with no page file.

---

### Post by Operan on 2009-07-18
At least you need a swap partition to enable hibernate your computer. 512MB of swap space is suitable for you!

---

### Post by Quarkrad on 2009-07-19
Slightly concerned now  -  my PC never hibernates/goes to sleep.  It sometimes goes to screensaver mode if I am not at keyboard but this is not the same as hibernation (to my understanding).  So is it safe to assume (for Linux/Ubuntu) that if you have enough RAM/resources (2GB/18%) you do not need a separate swap partition?

---

### Post by binbash on 2009-07-19
Yes if you are not planning to use hibernate.

---

### Post by Elfy on 2009-07-19
You won't need a swap until the time that you do so it's as well to have some, that said 512Mb would be more suitable than 4GB. Just my tuppence worth.

---

### Post by Quarkrad on 2009-07-20
OK thanks.  I'm new to this and have done some googling; it looks like I have to set up and config the swap partition.  One thing I cannot seem to fnd is:

mkswap /dev/hda12     for instance

What is the difference between hda12 and sda12?  Using gparted I can see the partition the partition I want to use - it is /dev/sda12.  But all the references I can find refer to the partition in the context hda. I have a number of partitions on my HD, what will my sda12 partition be called in terms of hdaX?

---

### Post by Elfy on 2009-07-20
hdxy is th eold way of referring to partitions, use sda12

---

### Post by ibutho on 2009-07-20
hdaX is what IDE hard drives used to be referred to until recent kernel versions when the IDE and SATA drivers were unified. Some distros still use this naming method. If your hard drive is identified as sda12, then thats what you need to use.

---

### Post by Quarkrad on 2009-07-24
It's been a few days since I was on top of this and I've got a little lost again.  I have sorted all my partitions (I have Ubuntu 9.04 on the first HD partition followed by a number of winxp/NTFS partitions) and I now have a new empty partition (at the end of my HD) /sda10, formated as ext4 ready to be my Swap file/volume/partition.  All I need to do now is to make Ubuntu aware of this partition and use it if necessary.  From what I can make out, I think I do not need to use mkswap as the partition is already there - I think I need to kick off with the swapon command.  But what do I type in the terminal?

---

### Post by Cheesemill on 2009-07-24
ext4 wont work as a swap partition, it has to be formatted as type swap.
This is what the mkswap command does.

---

### Post by Quarkrad on 2009-07-25
Thanks - that explains it.  Is it possible for some help with the terminal commands?  If I type in mkswap how do I point to sda10 and ensure that Ubuntu recognises this all the time?

---

### Post by Quarkrad on 2009-07-26
OK - I have used gparted to reformat sda10 as the Linux Swap and it looks OK.  I had a look at fstab to see if this change had changed anything and I got:

[B]# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sda1 during installation
UUID=c53012b0-9713-4ba5-94c8-1c75cba2d88c  /               ext4         relatime,errors=remount-ro  0  1  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sdb5                                  /media/sdb5     ntfs         defaults                    0  0  
/dev/sdb6                                  /media/sdb6     ntfs         defaults                    0  0  
/dev/sdb7                                  /media/sdb7     ntfs         defaults                    0  0  
/dev/sdb8                                  /media/sdb8     ntfs         defaults                    0  0  
/dev/sdb9                                  /media/sdb9     ntfs         defaults                    0  0  [/B]


To be honest I'm not sure what it says re SWAP.  Interesting it is showing all my partitions as sdb (which is my 2nd HD) although gparted shows my swap partition as the last partition on my 1st HD (which was sda10).  I am new to Linux - it looks a bit strange to me, where are all the sda partitions on my 1st HD?

---

### Post by Elfy on 2009-07-27
It doesn't have your swap partition. You need to add it yourself - open the file for editing

```
gksudo gedit /etc/fstab
```

Add this to the bottom of the file

```
/dev/sda10 none  swap  sw  0  0
```

Save and then run ```
sudo swapon -a
```

Check that swap is active ```
free -m
```

---

### Post by Quarkrad on 2009-07-27
Wow - thank you very much for your post.  I followed your instructions - the output of free -m   is:


             total       used       free     shared    buffers     cached
Mem:          2012        928       1083          0        129        364
-/+ buffers/cache:        434       1577
Swap:          517          0        517


my sda10 is 517.69 MB so the last line seems to confirm all is now set up.

Appreciated!

---

