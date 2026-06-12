---
title: "Emergency, formatted my hard drive"
date: 2009-10-09
forum: General Help
---

### Post by N4zgu1 on 2009-10-09
Hi everybody.

I have different partitions in my hard drive, today when I was installing fedora I accidentaly erased a ntfs partition where I had my archives.

Is there a way to recover my archives????

I would greatly appreaciate any help

Note: I have both ubuntu and windows so I can use both linux and windows programs

---

### Post by wojox on 2009-10-09
You could try killdisk: [http://www.killdisk.com/](http://www.killdisk.com/)

---

### Post by N4zgu1 on 2009-10-09
It looks like killdisk is for erasing partitions but I dont want to erase anything, I want to recover my files

---

### Post by wojox on 2009-10-09
Theres an option to recover deleted partitions. I use it all the time for erasing. You can't botch it up.

---

### Post by hal10000 on 2009-10-09
the best tool i know is [COLOR="Red"]testdisk[/COLOR], it's acommand line tool, but it works very well. if you did'nt overwrite the partition you will get your windows back.

---

### Post by QIII on 2009-10-10
TestDisk works very well, so I second that.

DON'T use the disk at all until you have had a chance to recover your files, though.  You might end up writing over something you would have liked to have recovered.

---

### Post by N4zgu1 on 2009-10-10
I want to know which is the safest option, If you think test disk is the safest then Im going to give it a try

---

### Post by QIII on 2009-10-10
I can't tell you what's best.

I can tell you that I have been able to salvage the data on other peoples' disks on a number of occasions by plugging their disk into my motherboard and running TestDisk from one of my drives.

I don't know about getting Windows back as a whole, working OS.  What I have done is recovered data (files) to removable media as necessary and allowed people to reinstall Windows fresh.  They have been able to use the removable media to put back all of their bits and pieces.

I've never used wojox' suggestion.  If that can recover partitions *in toto, *then it might be a good option.

---

### Post by hal10000 on 2009-10-10
To be honest, i never tried another than testdisk. I have recovered whole partitions (ext3 and ntfs) as well as particular files.

But it's only possible to recover a whole partition if it was not overwritten with other data. independently from the tool you use, unless you carry the disk to a specialist and pay him several thousands of $ to get your data back.

---

### Post by N4zgu1 on 2009-10-10
I didn't have windows installed on that partition, the partition only had my files.

I'm going to try test disk, but do I have to run Testdisk from another computer?. Or can I do it from my own computer, I have linux installed in another partition.

---

### Post by hal10000 on 2009-10-10
You can run it from your ubuntu system if you just want to recover your windows partition or boot your live-cd, i guess it's installed per default, if not run
[COLOR="Red"]sudo apt-get install testdisk[/COLOR], if you want to recover your ubuntu system, then of course you would have to boot the live-cd.

---

### Post by N4zgu1 on 2009-10-11
It looks like when I delated the partition using fedora it made an lvm2 partition, what can I do??

---

### Post by hal10000 on 2009-10-12
> It looks like when I delated the partition using fedora it made an lvm2 partition, what can I do??

If the partitiom was overwritten and formatted, then i guess you will have no luck to get the wole partition back. You can try to get several files restored (you can also use testdisk for that), but it may be a lot of work for you.

---

### Post by N4zgu1 on 2009-10-14
Ok now I restored the ntfs partition with testdisk but I cannot mount it, here is the whole story, maybe somebody can help me.


At the beginning I had four partitions in my hard drive:


1 primary hfs partition for hackintosh(mac)
2 primary ntfs partitions:
[LIST]
[*]1 for windows
[*]1 for my files  <<<<(this is the partition that I want to save)
[/LIST]
1 extended parition for linux that had
[LIST]
[*]1 ext3 partition for /
[*]1 parition for swap
[/LIST]

I wanted to install fedora 11 in the hfs partition but I made a mistake and I selected the ntfs parition that had my files, luckily I cancel the installation before it had the chance to overwrite the files, but the partition was erased.

after that I lose all my files but linux and windows continued functioning, I posted my problem in this forum and after they recommended me Testdisk I used it to restore the "files partition"

The problem is that I didn't understand how the program worked so in the new partition table I only restore the "files partition" but I didn't put my other partitions so everything was delated.

I used testdisk again, this time from the livecd because linux and windows were delated, this time I restore: 
[LIST]
[*]the two ntfs paritions (the windows parition and the "files parition")
[*]the linux / partition
[/LIST]

I didn't restore the swap partition because there were two options an I didn't know which one to choose.

After that I tried to boot but I had a Grub error 22, so I booted with the livecd and all the partitions worked fine except the "files partiton" (the only one that I care about)

when I try to mount the partition I get this error

```
mint@mint ~ $ sudo mount /dev/sda3 /media/
mount: unknown filesystem type 'LVM2_member'
```


here is the output of fdisk -l

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d1ece

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            3922        6532    20972857+   7  HPFS/NTFS
/dev/sda2            6533        7837    10482380   83  Linux
/dev/sda3            8622       30396   174907687+   7  HPFS/NTFS

```

Basically my problem is that I cannot mount /dev/sda3.

It would be great if somebody could help me, I'm desperate, so please help me

Thanks in advice


Note: Sorry if the story is confusing, I tried to be as clear as posible

---

### Post by hal10000 on 2009-10-15
Try to mount the windiws file partition manually with this command:
```

sudo mount -tntfs /dev/sda3 /mnt

```

I this works, then look into your /etc/fstab file. There should be a line similar to this one:
```

UUID=9A6C7BD26C7BA821 /media/Win_SYSTEM ntfs    defaults,umask=007,gid=46 0       1

```
You cansee six columns separated by spaces or TABs.
This is my own windows partition, so you probably have another UUID (first column) and another place to be mounted (the second column). Crucial is the third column, there has to be the entry "ntfs" (without the quotes).
I suppose your entry here is something like LVM2_member, but anyway what the entry is, it must be ntfs.

After you changed this to ntfs, unmount the partition (if you did'nt this already):
```
 sudo umount /dev/sda3
```

and test your new /etc/fstab file with
```
 sudo mount /dev/sda3
```
If that works, then your main problem is solved, and also your grub error may disappear. If it still exists, then post it here so we can g o further.

Good luck

[EDIT]
One problem still exists: you already have three primary partitions, and you will need two more partitions ( a swap and an ext3 for your fedora), so these would have to be logical partitions inside an extended partition. You should use the unallocated sectors 1 - 3921 of your harddrive for the extended partition.
At the end of your drive (sectors 30397 - 30401) there will remain some unusable space (where your former swap space resided). You may enlarge your /dev/sda3 partition to use this unallocated space for your /dev/sda3.

---

### Post by P4man on 2009-10-15
Im in the same boat!
I just accidentally (quick) formatted a ntfs external drive when i wanted to format a USB key for making it bootable. I figured it wouldnt be that catastrophically, but oh boy.

Anyway, long story short, Im now recovering (as Im typing lol ) most of my files using easeus data recovery wizard. Its not freeware, but it does work (on windows!), where as testdisk was making quite a mess for me.

---

### Post by N4zgu1 on 2009-10-17
Thanks everybody I could restore my partition and now everything is working fine.

---

