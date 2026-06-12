---
title: "Hard drive partitions"
date: 2009-08-22
forum: General Help
---

### Post by Rainbow Road on 2009-08-22
I have been dual booting XP Pro and Ubuntu (Jaunty) and have now just added Mint 7 as a third boot. It all works well but I am wanting to tidy up the spare space on the drive and the long grub list. The computer is a laptop with a 160GB ide drive. All linux distros have been installed from outside windows and linux (not wubi). I did have 37GB free on the drive but Mint would not install there and I had to resize XP from approx 50GB to 40GB and put it between XP and Ubuntu. I hardly ever use XP anymore so am happy leaving it that size but would like to increase size of Mint and share some of the space at end of disk between Mint and Ubuntu (if possible).

Below are the results of GParted, fdisk -l and the menu.lst file if they will help anyone with understanding my setup:

I know Mint is on SDA7; XP SDA1 & Ubuntu SDA5
I think SDA 4 is a linux partition which has a folder called Lost+Found but neither Ubuntu or Mint have permission to view contents.
Also not sure on what size my swap files should be (installed RAM on laptop is 768MB)

[IMG]http://i966.photobucket.com/albums/ae149/john741/Gparted.jpg[/IMG]

> title		Linux Mint 7 Gloria, kernel 2.6.28-11-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Linux Mint 7 Gloria, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Linux Mint 7 Gloria, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=12c0051e-eba4-4e09-a424-51b221d5cdc4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=12c0051e-eba4-4e09-a424-51b221d5cdc4 ro single 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=12c0051e-eba4-4e09-a424-51b221d5cdc4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=12c0051e-eba4-4e09-a424-51b221d5cdc4 ro single 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=12c0051e-eba4-4e09-a424-51b221d5cdc4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=12c0051e-eba4-4e09-a424-51b221d5cdc4 ro single 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=12c0051e-eba4-4e09-a424-51b221d5cdc4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=12c0051e-eba4-4e09-a424-51b221d5cdc4 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


> john@john-laptop ~ $ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7108f6c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5227    41985846    7  HPFS/NTFS
/dev/sda2           11871       16709    38865960    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            5228       11870    53359897+   5  Extended
/dev/sda4           16710       19337    21109410   83  Linux
/dev/sda5            6650       11650    40170501   83  Linux
/dev/sda6           11651       11870     1767118+  82  Linux swap / Solaris
/dev/sda7            5228        6583    10892007   83  Linux
/dev/sda8            6584        6649      530113+  82  Linux swap / Solaris

Partition table entries are not in disk order


---

### Post by HiImTye on 2009-08-22
you can get rid of SDA8 or SDA6 as you only need one swap drive (and only one is in use there) - or just merge them

---

### Post by jbeukema on 2009-08-22
that's some really ugly partioning....

---

### Post by Rainbow Road on 2009-08-22
> **jbeukema said:**
> that's some really ugly partioning....

Exactly, that's why I want to tidy it up.

---

### Post by ks07 on 2009-08-22
> **jbeukema said:**
> that's some really ugly partioning....
That wasn't a very helpful reply, was it? lol

Anyway, as to answer one of your questions, your swap space should be about 2x your RAM, so in your case about 1.5-2gb. And as HiImTye said, you only need one swap partition. /dev/sda6 is pretty much perfect for your system, so disabling sda8 (right click in gparted, swapoff) and growing the partition before it would be a good idea (if that is the partition you want to grow that is).

---

### Post by howefield on 2009-08-22
> **Rainbow Road said:**
> Exactly, that's why I want to tidy it up.

You could combine sda2 with the unallocated space and sda4 to form a shared Data partition, which all your installs could access. Change the permissions to allow your installs to use it.

Delete the swap nearest mint and incorporate the space into mint.

Startupmanager is an easy way of controlling your boot up list. INstall via synaptic.

---

### Post by jbeukema on 2009-08-22
> I have been dual booting XP Pro and Ubuntu (Jaunty) and have now just added Mint 7 as a third boot. 

Here's what I would do, personally

Partition 1 = Whichever Linux you use most

Partition 2 = Linux SWAP (placing it between the two linux partitions means each travels roughly the same disk space to reach the SWAP partition, instead of one traveling farther and hindering performance. Ideally, you need two drives for this system, if your laptop has a second bay) Else having you operating system, swap partition, and the files being accessed on the same drive is going to slow you down)

Partition 3= Whichever Linux you use next

Partition 4= NTFS (shared. Your music files, documents, etc that are shared go here. Again, ideally this should be on a second physical drive.)

Partition 5 = NTFS Windows(if you barely use it, make it 30Gb. It need only store the operating systems and programs)

The rule of thumb I've heard is to make your SWAP *2 your RAM. 2GB should be plenty for you.

160GB ide drive. All linux distros have been installed from outside windows and linux (not wubi). I did have 37GB free on the drive but Mint would not install there and I had to resize XP from approx 50GB to 40GB and put it between XP and Ubuntu. I hardly ever use XP anymore so am happy leaving it that size but would like to increase size of Mint and share some of the space at end of disk between Mint and Ubuntu (if possible).

[IMG]http://www.brandonsorg.com/images/159.jpg[/IMG]

---

### Post by Rainbow Road on 2009-08-22
Thanks for all replies so far which gives me a lot of options to try. 

Does anyone have any ideas on SDA4 with the Lost+Found folder? 

If I could safely delete this partition and merge SDA2 and the 2 unallocated partitions this would give me losts of space to move the partitions around.

I am currently in mint and the swap file has a key beside it so I presume I cannot delete that unless I do it from Ubuntu (just thinking I couldn't get Ubuntu to run gparted).

Also on my menu.lst for Ubuntu in the grub list I have 4 choices plus their recovery options can I safely delete the last 2?

---

### Post by jbeukema on 2009-08-22
The most important thing to remember is to never do this during a rainstorm. Power loss while GParted is fiddling with your partitions can have devastating results...

It it takes three days... let it finish... trust me..:(

---

### Post by ks07 on 2009-08-22
> **Rainbow Road said:**
> Thanks for all replies so far which gives me a lot of options to try. 

Does anyone have any ideas on SDA4 with the Lost+Found folder? 

If I could safely delete this partition and merge SDA2 and the 2 unallocated partitions this would give me losts of space to move the partitions around.

I am currently in mint and the swap file has a key beside it so I presume I cannot delete that unless I do it from Ubuntu (just thinking I couldn't get Ubuntu to run gparted).

Also on my menu.lst for Ubuntu in the grub list I have 4 choices plus their recovery options can I safely delete the last 2?
Well the 'lost + found' folder is where the disk checker puts any files or fragments of files it manages to recover after a power failure causes some data loss. You should be able to check the contents of it by using

```
gksudo nautilus
```then navigating to that lost and found folder. If there's anything inside, try opening it to try and figure out what it is (or was). If the folder is empty, I think it is safe to delete that partition because afaik, each partition is supposed to have it's own lost + found. However, on my PC, my shared partition does not have one, although this is likely caused by the fact it is a FAT32 drive. (EDIT: My /home partition _does_ have a lost+found though, so this leads me to think that the only reason you have that folder on that empty drive is just because it is standard for an ext3 partition.)

My best guess is it is safe to remove that partition if there is nothing on it apart from an empty lost + found partition.

---

### Post by Rainbow Road on 2009-08-22
> **ks07 said:**
> ```
gksudo nautilus
```then navigating to that lost and found folder. If there's anything inside, try opening it to try and figure out what it is (or was). If the folder is empty, I think it is safe to delete that partition because afaik, each partition is supposed to have it's own lost + found. 

My best guess is it is safe to remove that partition if there is nothing on it apart from an empty lost + found partition.

I tried that but it would not allow me to access other partitions, but I went to the folder, right clicked and opened as root which confirmed that it was empty. I have now deleted this partition and both Ubuntu and Mint seem to be happy without it.

My next question is I am trying to make the SDA3 partition bigger but which ever version of linux I go into it is locked :-k (I guess I could do this from a live CD).

---

### Post by Rainbow Road on 2009-08-22
> **Rainbow Road said:**
> My next question is I am trying to make the SDA3 partition bigger but which ever version of linux I go into it is locked :-k (I guess I could do this from a live CD).

:? That didn't work, it was still locked with the Mint Live CD.

Here is latest image of gparted (from live cd):

[IMG]http://i966.photobucket.com/albums/ae149/john741/GParted2.jpg[/IMG]

I am now thinking of removing the SDA6 swap file as previously advised, but how will Ubuntu which previously used this swap file know to use the Mint swap file SDA8 (or do I need to tell it).

---

### Post by ks07 on 2009-08-22
> **Rainbow Road said:**
> :? That didn't work, it was still locked with the Mint Live CD.

Here is latest image of gparted (from live cd):

[IMG]http://i966.photobucket.com/albums/ae149/john741/GParted2.jpg[/IMG]

I am now thinking of removing the SDA6 swap file as previously advised, but how will Ubuntu which previously used this swap file know to use the Mint swap file SDA8 (or do I need to tell it).

The reason you can't resize from the live cd is because it automatically uses any swap space on the hdd. Inside gparted on the live cd, right click the swap partitions with keys next to them and choose swap-off.

After this, all the key symbols should be gone and you will be able to grow your partition. :)

EDIT: As for removing sda6, hopefully ubuntu will use the other swap space. If it doesn't, it's very easy to tell it to from inside gparted.

---

### Post by Rainbow Road on 2009-08-22
> **ks07 said:**
> The reason you can't resize from the live cd is because it automatically uses any swap space on the hdd. Inside gparted on the live cd, right click the swap partitions with keys next to them and choose swap-off.

After this, all the key symbols should be gone and you will be able to grow your partition. :)

Found that in another users reply to a similar thread, which worked and drive partitioned almost perfect, and both linux distros started with no problems.

> **ks07 said:**
> As for removing sda6, hopefully ubuntu will use the other swap space. If it doesn't, it's very easy to tell it to from inside gparted.

Then I removed SDA6 and got a grub error 17 #-o

GRUB Loading Stage 1.5
GRUB Loading, Please Wait.
Error 17

Please can anyone help me return to the Mint grub.

---

### Post by Rainbow Road on 2009-08-22
Think I have solved it, although haven't got time at the moment. It appears that my Mint partition has changed from SDA7 to SDA6. So I will try and change the menu.lst file from the Live CD later. [-o<

---

### Post by oldfred on 2009-08-22
You also have to update fstab with any changes to UUIDs. Especially one like this for swap from my fstab:

# Entry for /dev/sdb5 :
UUID=144d59f5-9eeb-49ce-9d78-83bd317c443d none swap sw 0 0

---

### Post by ks07 on 2009-08-22
> **Rainbow Road said:**
> Think I have solved it, although haven't got time at the moment. It appears that my Mint partition has changed from SDA7 to SDA6. So I will try and change the menu.lst file from the Live CD later. [-o<
I have to admit I'm not too savvy when it comes to GRUB lol. But I can say I've come across that problem before.  It looks like you and oldfred are on the right track but if you get stuck here's two things I've tried in the past when I had a similar problem:
[Reinstall Grub]("http://ubuntuforums.org/showthread.php?t=224351")
[Super Grub Disk]("http://www.supergrubdisk.org/")

EDIT: Just had a thought. You will need to edit your menu.lst file and (probably just for the swap space) fstab. But this won't fix your GRUB, because your GRUB error means that it cannot find where it is installed from the number change and thus cannot see any of its config files (including the menu.lst). In this case I think your best option is to use the 'reinstall grub' guide i linked to above.

---

### Post by Rainbow Road on 2009-08-24
> **ks07 said:**
> if you get stuck here's two things .....
[Reinstall Grub]("http://ubuntuforums.org/showthread.php?t=224351")
[Super Grub Disk]("http://www.supergrubdisk.org/")


Thanks for your help, I used the Reinstall Grub link which restored my old Ubuntu grub enabling me to access both XP and Ubuntu again. Removed Mint partitions and reinstalled. All working fine now and partitions are a lot tidier than they were, although I still have 2 swap files but don't think I will try deleting one again.

---

