---
title: "YAPT (Yet Another Partitioning Threaad)"
date: 2006-06-16
forum: General Help
---

### Post by Gustav on 2006-06-16
I've decided to remove my windows partition (after about two years of not using it). And while I'm on it I would like to resize my / partition (I were a little cheap when I first made it maybe three years ago (for mandrake 9.0)).

My current setup is a little strange, but here it is

|  win_c |  win_d  | linux_media |  linux_/  |  swap  |  linux_home  |

What I want to do is remove the windows partitions and resize my root partition (from 5 to 8-10 GB). All linux partitions are almost full (70-85%).

What do you think is the best way to accomplish this?

(and will the removal of win_c do stuff to my mbr?)

(win_c has one physical partition and the others are logical partitions that share the other)

---

### Post by Rui Pais on 2006-06-16
[QUOTE=Gustav]I've decided to remove my windows partition (after about two years of not using it). And while I'm on it I would like to resize my / partition (I were a little cheap when I first made it maybe three years ago (for mandrake 9.0)).

My current setup is a little strange, but here it is

|  win_c |  win_d  | linux_media |  linux_/  |  swap  |  linux_home  |

What I want to do is remove the windows partitions and resize my root partition (from 5 to 8-10 GB). All linux partitions are almost full (70-85%).

What do you think is the best way to accomplish this?

(and will the removal of win_c do stuff to my mbr?)

(win_c has one physical partition and the others are logical partitions that share the other)[/QUOTE]

Hi, 
do that from a livecd (quite obvious ;)). Delete or reformat partitions didn't touch your MBR (or at least will not remove the Grub starter).

Resize is easy, and i never had any problems with it. But i never had great luck when it cames to move partitions. In your case, i would remove the win_ and win_d, make a partition on that space with the desired new size and copy all from the actual root linux to there with cp -a command. Then it was just a question of edit the new /etc/fstab line of / to the new /dev/hdXX path and grub menu.lst entrys (you will have most probabily have to edit those files anyway, since your partition numberation may change).

Just 2 more points. 
When resizing partitions the underground process should do 2 things. Resize the partition and resize the filesystem on it. Some tools don't do both automaticaly and people ends with a large partiton size but with the same useful space as before. If that happen to you just use resize2fs for ext2/3 and resize_reiserfs for reiserfs.

The other thing. Consider make an boot partition (outside / i mean) it makes things easier and you can enev choose not to keep it mounted after a boot of the system, avoiding any bad things that could happen to your kernels and grub if mounted. Again you just need to use cp -a to copy your actual  /boot/* to there.

hope that give some lights.

---

### Post by jak on 2006-06-16
I recently 'reshuffled' my partitions on my harddisks around about a week ago.
I used the GParted Live CD which is a small (30mb!) download from here[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
I resized, deleted and moved partitions so I had a problem with GRUB afterwards, I used the Ubuntu 6.06 CD to boot into a live distro and I re-installed GRUB by doing the following:
$grub
root (hd1,3)      <- this is where my / partition is ( i got a message about the filesystem after this command)
grub setup (hd0,0) <- this installed it to the MBR. ( this showed checks and installed GRUB.)

I hope I am recalling it correctly, and incase you move your linux partition around this should come in helpful.

**Ooh quick edit:** Don't forget to edit your grub.conf if you do!

---

### Post by Gustav on 2006-06-16
Thank you everybody!

I'll give it a try as soon as I have some spare time (probably sometime next week)

Is it best to leave it with root partition as one physical partition and the others on a logical partition or does that matter at all?

---

### Post by Gustav on 2006-06-16
Here is a more exact picture of the partitions by the way. :)

---

### Post by Gustav on 2006-06-19
I've encountered problems :(

The plan is to make a 10 gb rootpartition and a 1 gb swap at the beginning of the drive. That's easy, it's just to remove the first two partitions.

But then I want the rest to be a big /home, but gparted wont move the hda6 partition (in any direction) (I want to move it left so that it would come directly after the new swap).

Do I have to use a extra drive to store all my data (except root), or is there a better way?

(I'd rather not use any command line tools for partitioning since that's scary :))

---

