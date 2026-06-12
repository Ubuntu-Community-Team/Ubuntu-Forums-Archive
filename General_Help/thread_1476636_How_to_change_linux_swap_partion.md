---
title: "How to change linux swap partion?"
date: 2010-05-08
forum: General Help
---

### Post by hoanggeneral on 2010-05-08
I've ubuntu 9.10 installed on an external HD. This HD has 2 partitions;  one (H:) 272GB-NTFS contents my documents; one 25GB-Ext2 contents the  ubuntu. I've one internal HD with 4 partitions; (C:) 164GB-NTFS contents  Windows 7; one 55GB-Linux swap; (D:) 10GB-NTFS contents Dell's recovery  OS, and one 70MB-FAT16 contents some stuffs from Dell.
When I boot up my computer without connecting the external HD, a screen  shows 
"[B]GRUB loading.
error: no such partition.
grub rescue>[/B]   "
up. I  want to know why this problem happens. And how could I fix it?
I also want to move/change the linux swap partition and the partition  that contents ubuntu together into one physical HD. <- in order to  boot up the Windows 7/UBUNTU without have to connect the external HD.
  I know it is a lot of questions, but I'm very new to Linux.
  I will very very appreciate if you could help me out.
Thanks a lot.

---

### Post by spuny on 2010-05-08
For "GRUB loading. error: no such partition. grub rescue> " check this link: [http://ubuntuforums.org/showthread.php?t=1359802](http://ubuntuforums.org/showthread.php?t=1359802), and Linux swap should be double your physical memory (RAM) as I see you created 55GB SWAP. There's no need for that huge space for SWAP. Regarding moving partition I've no idea about that, sorry!

---

### Post by nikhilbhardwaj on 2010-05-08
55 GB swap is hilarious.


the steps are
sudo /sbin/swapoff /dev/hdXY
then create your new swap partition 
enable swap with /sbin/swapon
and add correct entry to the fstab.

if you cant understand thin then post the output of sudo fdisk -l
and we'll tell you what to do

---

### Post by hoanggeneral on 2010-05-08
Here is what displayed after I run "sudo fdisk -l" command.

[http://picasaweb.google.com/lh/photo/gzniC1CJDApOVY81_d4A6A?feat=directlink](http://picasaweb.google.com/lh/photo/gzniC1CJDApOVY81_d4A6A?feat=directlink)

To [nikhilbhardwaj]("http://ubuntuforums.org/member.php?u=842654"). For the command "sudo /sbin/swapoff /dev/hdXY", should I put "," and space at hdXY? Because they are hd0,1    hd0,2 hd1,1.... Also I have no idea how to create a new swap partition.

---

### Post by nikhilbhardwaj on 2010-05-09
your swap partition is /dev/sda4
first disable the swap by
```

sudo swapoff /dev/sda4

```

now you can create a new partition with gparted(available in the repos search in synaptic)
btw how much memory(ram) do you have the size of the swap partition should be in accordance with that and in no case should exceed 2 GB.
you can install gparted with
```

sudo aptitude install gparted

```
then after starting gparted its a point and click interface
if you have problems let me know i'll post screenshots.

also post the output of 
```

cat /etc/fstab

```
there will be a line of this form
# swap was on /dev/sda6 during installation
**UUID=785c4a95-4ee1-4a01-8c56-a77d611a9fd7 none            swap    sw **

make sure to comment it out for the time being
commenting means addind a # to the start of the line it should look like
**#UUID=785c4a95-4ee1-4a01-8c56-a77d611a9fd7 none            swap    sw **

we'll add the new uuid after you've done all the steps

---

### Post by dcstar on 2010-05-09
> **spuny said:**
> 
........
... and Linux swap should be double your physical memory (RAM)
........

Please do not parrot myths.

There is no need whatsoever for swap to be double physical memory, that was just a "rule of thumb" from the 1980's when RAM was expensive and rare and has no application today at all.

Swap size should be whatever your system requires, and the only "rule" these days is to have swap at least equal to physical RAM if you want to use Hibernation.

---

### Post by Zireth ZH on 2010-05-09
i cant believe theres ppl with 8000 beans LOL ur an ubuntu freak! xD

---

### Post by spuny on 2010-05-09
> **dcstar said:**
> Please do not parrot myths.

There is no need whatsoever for swap to be double physical memory, that was just a "rule of thumb" from the 1980's when RAM was expensive and rare and has no application today at all.

Swap size should be whatever your system requires, and the only "rule" these days is to have swap at least equal to physical RAM if you want to use Hibernation.

Well I'm not a "Linux GURU!" I was just telling him what I know .. anyway thanks for letting me know that.

---

### Post by hoanggeneral on 2010-05-09
This is the screen-short of the commands **sudo aptitude install gparted** and** cat /etc/fstab**

[http://picasaweb.google.com/lh/photo/qENheYksWNbIpah0EU0p2A?feat=directlink](http://picasaweb.google.com/lh/photo/qENheYksWNbIpah0EU0p2A?feat=directlink)

I installed the gparted from Synaptic Package Manager; however, I cannot run it because I cannot find its location :(.

This screenshort for **#UUID=07360eac-d046-4951-87b4-8a78f4a94345 none swap sw**

[http://picasaweb.google.com/lh/photo/PbRgR9BTRvSsTspFj6ORRQ?feat=directlink](http://picasaweb.google.com/lh/photo/PbRgR9BTRvSsTspFj6ORRQ?feat=directlink)

---

### Post by nikhilbhardwaj on 2010-05-10
no no no
thats not what i meant
you arent supposed to **type #UUID=07360eac-d046-4951-87b4-8a78f4a94345 none swap sw in a terminal**
you were supposed to add the # in front of it the /etc/fstab file
to do this open fstab as root with
```

sudo gedit /etc/fstab

```
and then make that ammendment.

it doesnt look like you have gparted installed
could you pleas post the output of
```

which gparted

```
if installed you will find it under
System>Administration>Gparted
alternatively you could start it from the terminal wit
```

gksu gparted

```

after you do this we'll proceed forward.

btw how much ram does your system have??

---

### Post by hoanggeneral on 2010-05-11
I got the gparted run.
I created a partition name "check", it is a primary partition (see this screen short: [http://picasaweb.google.com/lh/photo/ZsqqW5wX-uXyWKk6l0jXDQ?feat=directlink](http://picasaweb.google.com/lh/photo/ZsqqW5wX-uXyWKk6l0jXDQ?feat=directlink) ). However, I didn't use gparted to create it. I used the Acronis.Disk.Director.Suite to create the partition. I think it is fine, isn't it?
Here is what after I issue the command **which gparted** .
[http://picasaweb.google.com/lh/photo/yxndP3qRD4e6hHlUR3KlWQ?feat=directlink](http://picasaweb.google.com/lh/photo/yxndP3qRD4e6hHlUR3KlWQ?feat=directlink)
[http://picasaweb.google.com/lh/photo/eUi2B9HPJOIKJJtJkST1Zg?feat=directlink](http://picasaweb.google.com/lh/photo/eUi2B9HPJOIKJJtJkST1Zg?feat=directlink)

I have 3GB RAM.
I created the check partition with 6GB because I heard somewhere that the grub has do be as least double the size of system memory. Is that right?

---

