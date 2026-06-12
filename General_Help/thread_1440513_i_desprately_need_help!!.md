---
title: "i desprately need help!!"
date: 2010-03-27
forum: General Help
---

### Post by tfrizzl on 2010-03-27
Ok, i have ubuntu 9.10 and in the GNU GRUB 1.97 beta4, windows 7 isn´t listed. I can´t access my files on my windows partition or anything! If i use my windows install disk to try to repair start up, or go into system recovery, it won´t let me because it can´t recongise ubuntu and it doesn´t show windows! 

i´m a huge noob to ubuntu and i don really know what i´m doing at all. I really need help to fix this, i need to be able to access my windows files! 

I have a single 500gb hard drive with 3 partitions. thats all the info i can provide. if you need more, please tell me how to access it.

THANKS!

---

### Post by nitstorm on 2010-03-27
try this to try accessing files on your windows partition
type in 
sudo fdisk -l
see where the windows partition is located
then type
mkdir /media/"whatever-you-want-to-name-the-partition"
then
sudo mount location-of-device whatever-younamed-the-partition

Ex:
If i put in sudo fdisk -l in my comp
i find windows partition is /dev/sda1

then i make a new directory in /media:
mkdir /media/windows

then i mount the partition to the directory i just created:
sudo mount /dev/sda1 /media/windows

Now that the partition is mounted, you should be able to access the files.
Hoping this is useful. If not, sorry. Cheers :)

---

### Post by tfrizzl on 2010-03-27
@nitstorm, when i try to make the directory of WINDOWS, it says PERMISSION DENIED. what do i do now?

---

### Post by nitstorm on 2010-03-27
try ```
sudo mkdir /media/windows
```

---

### Post by tfrizzl on 2010-03-27
Nothing happened.

---

### Post by nitstorm on 2010-03-27
so you were able to mount the windows partition in /media/windows ?
try opening up the partition using nautilus( the file manager)
```

nautilus /media/windows

```


Also could you please post the output of
```

sudo fdisk -l

```

---

### Post by tfrizzl on 2010-03-27
Ok, the only thing that i was able to do was get _sudo fdisk -1_ to work. 

> frizzy@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x248cc25b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217       60801   478616512+   5  Extended
/dev/sda5           60098       60801     5654848+  82  Linux swap / Solaris
/dev/sda6            1217       59393   467306689+  83  Linux
/dev/sda7           59394       60097     5654848+  82  Linux swap / Solaris

Partition table entries are not in disk order
frizzy@ubuntu:~$ 


I just noticed that if i go to computer, ubuntu doesn´t even recongize my hard drive. could that be a problem?

---

### Post by nitstorm on 2010-03-27
Please post the output of sudo fdisk -l  (l as in list) not sudo fdisk -1 
copy the output and paste it here please..

---

### Post by ken22 on 2010-03-27
Is your bios set to boot from the CD? Does it?

Can you see the windows disk under "Places" on the desktop?

---

### Post by tfrizzl on 2010-03-27
Yes, yes, no

---

### Post by nitstorm on 2010-03-27
sorry , i didnt read ur earlier edited post.
seems like u installed linux on top of ur windows partition meaning you replaced windows with linux...

---

### Post by tfrizzl on 2010-03-27
I did, its on the first page

---

### Post by tfrizzl on 2010-03-27
So reinstall windows? thats the fix?

---

### Post by ken22 on 2010-03-27
Well yes. It seems you've lost all your files though.

---

### Post by nitstorm on 2010-03-27
yes you have to reinstall windows on the free space that u have left, which is seen as the extended space in the output of fdisk -l
then, you will have to reinstall the grub, this link should be able to guide you through it
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Sorry that you lost your files, I crashed my system and lost a few hundred GB wen i toyed around with Ubuntu for the first few times too... 

Cheers :)

---

### Post by tfrizzl on 2010-03-27
OK, it was working fine yesterday. I could do everything without any trouble. I tried to get on this morning and i got a GRUB RECOVERY thing, the GRUB didn´t load. 

After trying a lot of different things and possible solutions, i reinstalled Ubuntu on a new partiton since none of the solutions worked. 

Does that change anything? or is it just that there are two installs of ubuntu and they are conflicting and hiding things in the process?

---

### Post by nitstorm on 2010-03-27
> 
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217       60801   478616512+   5  Extended
/dev/sda5           60098       60801     5654848+  82  Linux swap / Solaris
/dev/sda6            1217       59393   467306689+  83  Linux
/dev/sda7           59394       60097     5654848+  82  Linux swap / Solaris



You see the part where it says Linux twice, Linux swap/Solaris twice - That means you have 2 Linux OS's installed in those drives
Then you see /dev/sda2 which says extended which means that's the free space on your system. 
So wen u installed linux again you probably overwrote on the windows partition
Have a look at my fdisk -l 
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6528    52428800    7  HPFS/NTFS
/dev/sda2            6528       12794    50331648    7  HPFS/NTFS
/dev/sda3           12794       16841    32513024    7  HPFS/NTFS
/dev/sda4           16842       19457    21013020    5  Extended
/dev/sda5           16968       19457    20000925   83  Linux
/dev/sda6           16842       16967     1012032   82  Linux swap / Solaris

You see the HPFS/NTFS , that is the NTFS partitions I have on my system and /dev/sda1 is where my Windows is installed.
Something similar to that is missing in your fdisk -l output so you probably overwrote on your windows partition but have 2 linux OS's installed....

---

