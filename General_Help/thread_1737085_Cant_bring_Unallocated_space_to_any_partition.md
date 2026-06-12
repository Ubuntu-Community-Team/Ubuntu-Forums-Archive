---
title: "Cant bring Unallocated space to any partition"
date: 2011-04-23
forum: General Help
---

### Post by Ronalddig on 2011-04-23
hi

i had 320 GB disk.

it had already 4 primary partitions. So i had to delete 1 HP_Tools partition to install UBUNTU

now, the 104 Mb space of HP_Tools comes as unallocated and I am not able to RESIZE any partition to include that space.

why ?? normally if i had unallocated space i just resize c: and include it in that .

attached Gparted screen :



thx in adavnce :)

---

### Post by Elfy on 2011-04-23
It would look that you should be able to add it to sda3. To add it to any of the other primary partitions it needs to be next to them - a lot of work for 100Mb. To add it to any of the logical partitions sda5/6 you need to add it to the extended first. 

However in order to move it or add it to any of sda1/2/5/6 then the mounted partitions need to be unmounted. Try it from a livecd.

---

### Post by Ronalddig on 2011-04-23
thx for info , but i just did not get it completely.

how am i supposed to mount and unmount and then move it next and then resize ??

---

### Post by fdrake on 2011-04-23
> **Ronalddig said:**
> thx for info , but i just did not get it completely.

how am i supposed to mount and unmount and then move it next and then resize ??

you cannot resize file systems that are mounted on the system . first you unmount them , u resize them then you mount them again. where do you want to put that memory in which file system?

like forestpiskie said it is better and safer to reboot with a live pc, use gparted and you will be able to resize everything mush easier.

---

### Post by Ronalddig on 2011-04-23
i would like to bring that space to either Windows of Linux . I just dont want to waste it . Moreover it would help me learn new things :)

---

### Post by Ronalddig on 2011-04-23
can any mod remove above SPAM comment from my thread

---

### Post by fdrake on 2011-04-23
since you are running ubuntu you cannot unmount the root folder therefore you can give this partition to windows. on the screen you posted you right click (or select) the "/dev/sd2" partition and it should either popup an menu option with "unmount" or you go to the menubar on top and search for the option "unmount". once you have unmounted the partition you have the access to move back and forward the border of the windows partition by using the extra space left.

---

### Post by Ronalddig on 2011-04-23
the unmount option is greyed out , so i cannot select it ...

also if i try to resize  /dev/sda2 , it doesnt let me add  anything ( i.e. right arrow doesnt move )

---

### Post by Quackers on 2011-04-23
It appears that the free space can only be added to sda3, which is a recovery partition. That would just be wasting the space but in a different place :-)

As you have already been informed you cannot change partitions that are mounted. You cannot unmount your root partition if you are using the system. You need to do these actions from the live cd desktop.

---

### Post by coffeecat on 2011-04-23
@Ronalddig, you can only easily add that 104MiB space to your recovery partition which, as Quackers points out, is a bit pointless. If you really want to add it to your sda6 Linux partition, you would have to...

- boot up the live CD and open Gparted.
- "swapoff" the swap partition.
- Move the sda3 partition 104MiB to the right.
- Enlarge the sda4 extended partition by 104MiB.
- Move the sda5 swap partition 104MiB to the right.
- Enlarge the sda6 partition by 104MiB.

If you want to add it to your sda2 Windows partition, you would have to do the first 5 steps above, and then:

- Move the sda6 partition 104MiB to the right.
- Shrink the extended partition sda4 by 104MiB.
- Enlarge the sda2 partition by 104MiB.

Each of those steps would take a long time and each of those steps risks something going wrong and you losing one partition or the lot. For approx 100MiB, it's not worth the risk - in my opinion.

---

### Post by Ronalddig on 2011-04-23
> **coffeecat said:**
> @Ronalddig, you can only easily add that 104MiB space to your recovery partition which, as Quackers points out, is a bit pointless. If you really want to add it to your sda6 Linux partition, you would have to...

- boot up the live CD and open Gparted.
- "swapoff" the swap partition.
- Move the sda3 partition 104MiB to the right.
- Enlarge the sda4 extended partition by 104MiB.
- Move the sda5 swap partition 104MiB to the right.
- Enlarge the sda6 partition by 104MiB.

If you want to add it to your sda2 Windows partition, you would have to do the first 5 steps above, and then:

- Move the sda6 partition 104MiB to the right.
- Shrink the extended partition sda4 by 104MiB.
- Enlarge the sda2 partition by 104MiB.

Each of those steps would take a long time and each of those steps risks something going wrong and you losing one partition or the lot. For approx 100MiB, it's not worth the risk - in my opinion.


Thanks a lot for complete details and instructions . I would skip it then . I dont love that 100 MB that much :D

---

