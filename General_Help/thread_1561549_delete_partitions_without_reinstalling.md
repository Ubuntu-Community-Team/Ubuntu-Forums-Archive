---
title: "delete partitions without reinstalling"
date: 2010-08-26
forum: General Help
---

### Post by ieBrazil on 2010-08-26
Hi.

I've installed Ubuntu on my Pavilion dv4. I did not, when doing it, delet the other partitions. But now I want to. How can I do it without reinstalling it all?

Thanks! Ah, I'm lay person on this commands things... so teach me the easy way, if any.

C u!



ieBrazil

---

### Post by sikander3786 on 2010-08-26
Hi.

How many partitions are there and on which one is Ubuntu installed?

Use Disk Utility in Lucid to delete the partitions GUI way. System > Administration > Disk Utility or if you prefer you can install gparted.

---

### Post by Rubi1200 on 2010-08-26
In order for us to offer advice, we need to know more than you have told us.

What is the current state of your system?

Meaning, what operating systems are installed and how is the drive partitioned?

Please post the output of ```
sudo fdisk -l
```
Lowercase L not 1

Thanks.

---

### Post by User-007 on 2010-08-26
System -> Disk Utility, then select partitions -> delete partition

User JB

---

### Post by dabl on 2010-08-26
Unless Ubuntu is on the _first_ partition (/dev/sda1), if you remove non-used partitions, you will change the partition numbers.

Depending on how the partitions are identified in /etc/fstab, after the partition numbers are changed you might not be able to boot.  If it uses "boot by-uuid", then it could be OK.

If you post the /etc/fstab file, we can answer that question.

---

### Post by ieBrazil on 2010-08-26
The systems in my machine is W...7, Home Basic.
it's in Portuguese, my mother tongue:

file:///home/isaque/%C3%81rea%20de%20Trabalho/screenshot1.png

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificador do disco: 0x0002db44

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sda1   *           1       18783   150867243+  83  Linux
/dev/sda2           18783       38914   161701889    5  Estendida
/dev/sda5           37882       38914     8284160   82  Linux swap / Solaris
/dev/sda6           18783       37102   147147776   83  Linux
/dev/sda7           37102       37882     6261760   82  Linux swap / Solaris

Partições lógicas fora da ordem do disco
isaque@isaque-laptop:~$ ^C
isaque@isaque-laptop:~$ 

 


> **Rubi1200 said:**
> In order for us to offer advice, we need to know more than you have told us.

What is the current state of your system?

Meaning, what operating systems are installed and how is the drive partitioned?

Please post the output of ```
sudo fdisk -l
```
Lowercase L not 1

Thanks.

---

### Post by ieBrazil on 2010-08-26
up here I've attached an image of my disk utility. See it and tell me if I really have a partition!

it appears when I boot my computer as option to start. Plus, my disk is 320gb, but I just can use + or - 130bg... therefore, there must be a partition somewhere.

---

### Post by Rubi1200 on 2010-08-26
> **ieBrazil said:**
> up here I've attached an image of my disk utility. See it and tell me if I really have a partition!

it appears when I boot my computer as option to start. Plus, my disk is 320gb, but I just can use + or - 130bg... therefore, there must be a partition somewhere.
Can you take another screenshot but this time after you have clicked on the 320GB icon?
Thanks.

You said you have Win7, but fdisk only shows Linux?!?

---

### Post by ieBrazil on 2010-08-26
yeap, I've already dit it... right after I attached that one.

tnx.. take a look at it ... please,

> **Rubi1200 said:**
> Can you take another screenshot but this time after you have clicked on the 320GB icon?
Thanks.

You said you have Win7, but fdisk only shows Linux?!?

---

### Post by Rubi1200 on 2010-08-26
Did you install Windows first and then Ubuntu or the other way?

In Ubuntu, go to the terminal (Applications > Accessories) and run ```
sudo update-grub
``` and see if it finds Windows (it will say so if it did).

As dabl already asked, please post the output of
```
 cat /etc/fstab
```

---

### Post by ieBrazil on 2010-08-26
W7 was the OS that came pre-installed on the computer. 

Did you check the second image I've attached... there is an extended ('extendida', in my language) of 166GB... you see that?

I'll do the command you told right now...


isaque@isaque-laptop:~$ sudo update-grub
[sudo] password for isaque: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
isaque@isaque-laptop:~$ sudo update-grub





> **Rubi1200 said:**
> Did you install Windows first and then Ubuntu or the other way?

In Ubuntu, go to the terminal (Applications > Accessories) and run ```
sudo update-grub
``` and see if it finds Windows (it will say so if it did).

---

### Post by Rubi1200 on 2010-08-26
Ok, this is odd.
fdisk says Linux is on sda1, and GRUB says Windows is there (as I expected it should be).

Please run ```
sudo fdisk -l
``` again and ```
cat /etc/fstab
```

---

### Post by ieBrazil on 2010-08-26
I think the question is: may I or should I, in order to have more space in disk, delete the 'extended' partition? (it's a container for logical partitions, according to what I've read.

---

### Post by ieBrazil on 2010-08-26
> **Rubi1200 said:**
> Ok, this is odd.
fdisk says Linux is on sda1, and GRUB says Windows is there (as I expected it should be).

Please run ```
sudo fdisk -l
```

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificador do disco: 0x0002db44

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sda1   *           1       18783   150867243+  83  Linux
/dev/sda2           18783       38914   161701889    5  Estendida
/dev/sda5           37882       38914     8284160   82  Linux swap / Solaris
/dev/sda6           18783       37102   147147776   83  Linux
/dev/sda7           37102       37882     6261760   82  Linux swap / Solaris

Partições lógicas fora da ordem do disco
isaque@isaque-laptop:~$ 


 again and ```
cat /etc/fstab
```

isaque@isaque-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=8ac44aef-7e60-4620-842d-d6dca94c43e7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=36e46e2e-f3d3-4fcf-bd57-8af6ae2b708b none            swap    sw              0       0
isaque@isaque-laptop:~$

---

### Post by oldfred on 2010-08-27
Both Disk Utility and fdisk see it as type 83 but NTFS which it cannot be.

From your disk utility can you click on edit partition in the lower right corner and see if it will let you change it to HPFS/NTFS 0x07 in the combo box? If so then try fdisk again. if not we will have to see if we can force the change another way.

You may have to make sure the partition is unmounted for the change to work. So if in places it is mounted right click and unmount first.

---

### Post by ieBrazil on 2010-08-30
"You may have to make sure the partition is unmounted for the change to work..."

Well, to unmout the partition is all that I want to do! The case is that I don't know if I can, if deleting it this won't f*** my system as a whole!

The 166GB partition and its sub-partitions is what I want to know if I can delete it. Then I'd have my 320GB hd for use...

Anyway... how about if I delete the 166gb partition ('extended' stuff for logical...) and if something wrong happens, then I try to install it all again?

Olfred, please, take a look at the attachments in the first part of the thread. Thank you all so much!


iebrazil



> **oldfred said:**
> Both Disk Utility and fdisk see it as type 83 but NTFS which it cannot be.

From your disk utility can you click on edit partition in the lower right corner and see if it will let you change it to HPFS/NTFS 0x07 in the combo box? If so then try fdisk again. if not we will have to see if we can force the change another way.

You may have to make sure the partition is unmounted for the change to work. So if in places it is mounted right click and unmount first.

---

### Post by oldfred on 2010-08-30
If you want to delete the extended partition you should use the liveCD. Because swap is in the extended it will usually get mounted by the liveCD and you have to right click on it and swap off. Not sure if you have to do it for both since you have two swaps.

You then can delete each partition inside the extended and only then can you delete the extended partition that is empty.

But you still have a mis match issue on sda1. If you installed linux into sda1 it still says NTFS in another place, or if it still is windows it says ext3 in anther place. It cannot be both and will not work until you fix that error. It looks like you installed linux in sda1 overwriting the windows, but something was recovered that brought back the NTFS setting from windows.

---

### Post by ieBrazil on 2010-08-30
hi.
I really don't knwo what swap off is about.
Anywhow, I then can delete the partitions in place one (see attached picture) and get, naturally, more space that is deserved for my use, right?

I dont understand in fact what you're supposing about Windows and stuff, about what is weird in this case. I just do not comprehend, you know. Ignorance sux. I dont get the 'miss issue' on my sda1...
 


> **oldfred said:**
> If you want to delete the extended partition you should use the liveCD. Because swap is in the extended it will usually get mounted by the liveCD and you have to right click on it and swap off. Not sure if you have to do it for both since you have two swaps.

You then can delete each partition inside the extended and only then can you delete the extended partition that is empty.

Let me translate what it is said down the 'extended' partition for you here:

USE: container for logical partitions        DEVICE: /dev/sda2
TYPE OF PARTITION: extended (0x05)       CAPACITY: 166GB
etc.
[there'a an option which says:] exclude partition.

Also there is a saying which states that "SMART's Status: The unity is good/well/alright"

And that's it. In fact I'm just afraid of deleting it, now. 


But you still have a mis match issue on sda1. If you installed linux into sda1 it still says NTFS in another place, or if it still is windows it says ext3 in anther place. It cannot be both and will not work until you fix that error. It looks like you installed linux in sda1 overwriting the windows, but something was recovered that brought back the NTFS setting from windows.

---

### Post by oldfred on 2010-08-30
Using gparted info:

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Do you have windows in sda1 or do you have Ubuntu in sda1?

---

### Post by ieBrazil on 2010-09-06
Do you have windows in sda1 or do you have Ubuntu in sda1?[/QUOTE]

cant you check this info on the pics I have attached on the posts? 'cause I dont know, sorry...

In the disk utility only appears, on the partitions part, SYSTEM 154 GB NTFS and another onether one named Extended 166GB with three sub-partitions 151GB ext4, unknown 6,4 GB and SWAP Area 8,5 GB.

It all counts my 230 GB HD, which in fact I'm only using the 154 GB. that's why I want to know how to proceed in order to delete the other partitions... But I dont know if I can do, or even if I can do, if it won't hurt my linux system... there's the button to exclude, another to format and another to edit the partitions and sub-partitions. But I dont know which format etc. to chose nor if I really can do it, from the point of view of 'root, system, demage, etc.' which I really lay on.

Tnx for the time taken on my case, oldfred. You're the one!



[QUOTE=oldfred;9786236]Using gparted info:

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by oldfred on 2010-09-06
For issues of partitions not being correctly identified, testdisk is often a solution.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

I have not used testdisk but many who have, have said it works.

---

