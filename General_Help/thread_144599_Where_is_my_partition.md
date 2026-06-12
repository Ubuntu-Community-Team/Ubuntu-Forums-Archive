---
title: "Where is my partition?"
date: 2006-03-14
forum: General Help
---

### Post by achtungbaby on 2006-03-14
I have recently partitioned my main hard disk using Partition Magic in Windows XP. The situation was like this:
I had four partitions and I will name them according to what Partition Magic calls them:
C: (NTFS)
E: (FAT32)
/ (EXT2)
Linux swap.

Windows is installed on C and Ubuntu 5.10 with kernel 2.6.12-10-386 on /.

What I did in Partition Magic was to decrease the size of C and increase the size of E. No changes concerning the Linux partitions.

This works well in Windows. I see two partitions in My Computer: C and E. The Linux partition is not recognized, as expected...

The new sizes of the partitions are:
C: 40 GB
E: 85 GB
/ 30.3 GB
Linux swap 1 GB.

File systems remain unchanged.

E contains some docs etc that I really need in both Windows and Ubuntu so that is why I've made this "data"-partition in the middle. Stupid? Maybe, but that seemed like a solution for me. :) 

No to the problem. In Ubuntu I can't get access to my "data" (E)-partition. Inside System/Administration/Disks. When I select my hard disk I have four partitions in the Partition List:

Partition 1: NTFS Device: /dev/hda1 Access path: /media/hda1 39 GB
Partition 5: EXT3 Device: /dev/hda5 Access path: / 83 GB
Swap partition: Device: /dev/hda6 29.6 GB
Swap partition: Device: /dev/hda7 1 GB

So, what happened to my new partition? Before I resized it, I had no problem accessing it in Ubuntu.

What makes me even more confused is when I take a look at my partitions inside GParted. There I see two "main" partitions, first /dev/hda1 (NTFS, 40 GB) and second /dev/hda2 (extended 116 GB) with three "branches":
/dev/hda5 FAT32 85 GB
/dev/hda6 EXT2 30 GB
/dev/hda7 linux-swap 1 GB

Seems like these three partition has become sub-partitions (does that exist?) to a new partition.

Any idea how to solve this?

I've got both Ubuntu installation CD and Live CD at hand if needed. I can give closer specifications of my system if that would be necessary. Please consider me as a newbie. I've got some Linux experience but don't take anything for granted concerning my knowledge.

---

### Post by halfvolle melk on 2006-03-14
What does it say when you do Applications -> Accessories -> Terminal
```
cat /etc/fstab
```?

---

### Post by achtungbaby on 2006-03-14
[QUOTE=halfvolle melk]What does it say when you do Applications -> Accessories -> Terminal
```
cat /etc/fstab
```?[/QUOTE]


```
otto@stat:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by halfvolle melk on 2006-03-14
Weird. And what does "df -h" say?

---

### Post by achtungbaby on 2006-03-14
[QUOTE=halfvolle melk]Weird. And what does "df -h" say?[/QUOTE]

```
otto@stat:~$ df -h
Filsystem            Storlek Anvnt Tillg Anv% Monterat på
/dev/hda5              30G  8,9G   19G  32% /
tmpfs                 252M     0  252M   0% /dev/shm
tmpfs                 252M   13M  240M   5% /lib/modules/2.6.12-10-386/volatile
/dev/hda1              40G  2,5G   37G   7% /media/hda1
/dev/sda1             153G  151G  1,7G  99% /media/MAXTOR
```

For clarification. I've also got an external USB-disc (/media/MAXTOR). But it works perfectly.

---

### Post by halfvolle melk on 2006-03-14
Ok, if you're positive the info in your first post is correct you could try the following
```
ls /dev/hd*
```
to see if hda7 is realy there.
```
mkdir /mnt/hda7
sudo mount /dev/hda7 /mnt/hda7
```
Then to see what file system it actually is do
```
df -T
```
swap will show up as tmpfs (AFAIK)
You can edit /etc/fstab accordingly. My best guess is that If you'd use the live cd and get into a terminal, typing:
```
cfdisk
```
you will see free space of some 50 GB. Could also be I'm talking out of my ***.

---

### Post by achtungbaby on 2006-03-14
[QUOTE=halfvolle melk]Ok, if you're positive the info in your first post is correct you could try the following
```
ls /dev/hd*
```
to see if hda7 is realy there.[/QUOTE]

Yes, it's there:

```
otto@stat:~$ ls /dev/hd*
/dev/hda   /dev/hda2  /dev/hda6  /dev/hdc
/dev/hda1  /dev/hda5  /dev/hda7  /dev/hdd
```

[QUOTE=halfvolle melk]```
mkdir /mnt/hda7
sudo mount /dev/hda7 /mnt/hda7
```[/QUOTE]

It's not possible to mount it, since it's a swap disk.

[QUOTE=halfvolle melk]Then to see what file system it actually is do
```
df -T
```
swap will show up as tmpfs (AFAIK)[/QUOTE]

```
otto@stat:~$ df -T
Filsystem      Typ   1K-block    Använt Tillgängl Anv% Monterat på
/dev/hda5     ext3    30558176   9284536  19721364  33% /
tmpfs        tmpfs      257864         0    257864   0% /dev/shm
tmpfs        tmpfs      257864     12588    245276   5% /lib/modules/2.6.12-10-386/volatile
/dev/hda1     ntfs    40965716   2605224  38360492   7% /media/hda1
/dev/sda1     vfat   160032512 158288256   1744256  99% /media/MAXTOR
```

[QUOTE=halfvolle melk]You can edit /etc/fstab accordingly.[/QUOTE]

How do you mean I should edit it?

[QUOTE=halfvolle melk]My best guess is that If you'd use the live cd and get into a terminal, typing:
```
cfdisk
```
you will see free space of some 50 GB. Could also be I'm talking out of my ***.[/QUOTE]

I haven't tried it using the live cd. I will do it tomorrow.

---

### Post by halfvolle melk on 2006-03-14
That might be it than.
```
/dev/hda **/dev/hda2** /dev/hda6 /dev/hdc /dev/hda1 /dev/hda5 **/dev/hda7** /dev/hdd
```
> How do you mean I should edit it?
Your fstab only mounts 1, 5 and 6(swap). Then there's hda2 and hda7 to be mounted. As you say, hda7 won't mount because it's swap, but try hda2.
```
mkdir /mnt/foo
sudo mount /dev/hda2 /mnt/foo
df -T
```
If that doesn't help I'm sorry, maybe a seasoned user will jump in.

---

### Post by Sef on 2006-03-15
> I have recently partitioned my main hard disk using Partition Magic....

Just a note to those new to linux reading this post about using partitioners.  Almost all are ok to use, except Partion Magic.  There have been numerous posts about the problems with it.

---

### Post by achtungbaby on 2006-03-18
Sorry for not updating you on my progress. 

At first, Partition Magic made my data (d), ext3 and swap-partitions secondary of some reason. They worn't before I resized data but of some strange reason it was after resizing. I solved this by just changing them to primary, then no "branches" of an extended partition was seen in gParted.

Today, I learnt how /etc/fstab works and after looking at the setup there I realized that the problem could maybe be solved if I reconfigured according to what I desired. This is how it looked:

```
otto@stat:~$ df -T
Filsystem      Typ   1K-block    Använt Tillgängl Anv% Monterat på
/dev/hda4     ext3    30558176  10441872  18564028  36% /
tmpfs        tmpfs      257864         0    257864   0% /dev/shm
tmpfs        tmpfs      257864     12588    245276   5% /lib/modules/2.6.12-10-386/volatile
/dev/hda3     vfat    86997632  26452816  60544816  31% /media/data
/dev/hda1     ntfs    40965716   2605836  38359880   7% /media/hda1
/dev/sda1     vfat   160032512 158288352   1744160  99% /media/MAXTOR
```

And after manual changes:

```
otto@stat:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hda4       /               ext3    defaults        0       1
proc            /proc           proc    defaults        0       0
/dev/hda3       /media/data     vfat    defaults        0       0
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Now, everything works just as I want. Though, I'm realizing now that I'm mounting /dev/hda4 twice, both as / and as a swap partition. This is probably why I see two swap partitions in System/Administration/Disks and not the root partition. I will fix it. :)

What does the proc-line mean in fstab?

Ok, my initial problem is solved. Now to my next question concerning /dev/hda1 (my Windows NTFS partition). How can I change the permissions so I don't need to be logged in as su to access it? I know I can't write to it, but it should at least be possible to read from it.

EDIT: I can't write to the FAT32-partition. How do I solve this?

[QUOTE=Sef]Just a note to those new to linux reading this post about using partitioners.  Almost all are ok to use, except Partion Magic.  There have been numerous posts about the problems with it.[/QUOTE]

Well, Partition Magic has done a great job for me during the years. But I'm realizing now that it is not that reliable. For the future: how should I do when I want to resize my partitions or create new ones?

---

### Post by achtungbaby on 2006-03-19
Anyone got an answer for my last post? :-?

---

### Post by halfvolle melk on 2006-03-19
[QUOTE=achtungbaby]Now, everything works just as I want.[/QUOTE]
Cool, good job!

> What does the proc-line mean in fstab?
*"In Linux there is an additional mechanism for the kernel and kernel modules to send information to processes --- the /proc file system. Originally designed to allow easy access to information about processes (hence the name), it is now used by every bit of the kernel which has something interesting to report, such as /proc/modules which has the list of modules and /proc/meminfo which has memory usage statistics."* from [http://www.linux.com/guides/lkmpg/x716.shtml](http://www.linux.com/guides/lkmpg/x716.shtml)

When you browse your /proc dir you will see it's full of numbers. Those refere to running processes (I think) and I'll bet there's a lot of usefull info in there (haven't got a clue actually :mrgreen: )


> Ok, my initial problem is solved. Now to my next question concerning /dev/hda1 (my Windows NTFS partition). How can I change the permissions so I don't need to be logged in as su to access it? I know I can't write to it, but it should at least be possible to read from it.
I think a "sudo chown -R otto /media/hda1" will solve that. Dunno about the FAT32 thing.

---

