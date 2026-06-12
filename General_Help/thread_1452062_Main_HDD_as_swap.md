---
title: "Main HDD as swap"
date: 2010-04-11
forum: General Help
---

### Post by sam45 on 2010-04-11
I did something wrong while setting up my swapspace
so now my main HDD is linux-swap
I am dual booting windows and ubuntu, but now I can't boot into windows nor acces the partition because it is swap now..

I really hope I didn't lose my files on that partition, any help is appriciated

the screenshot explains my problem [IMG]http://img213.imageshack.us/i/screenshotmk.png/[/IMG]

---

### Post by uRock on 2010-04-11
Can you run this in a terminal and post the results for us to see what is going on? ```
sudo fdisk -l
``` This command will show all of the partitions and what type they are. and that is a lower case L, not a 1(one).

---

### Post by sam45 on 2010-04-11
> **uRock said:**
> Can you run this in a terminal and post the results for us to see what is going on? ```
sudo fdisk -l
``` This command will show all of the partitions and what type they are. and that is a lower case L, not a 1(one).

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc537805c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       47745   383511681    7  HPFS/NTFS
/dev/sda2           47746       60801   104872320    5  Extended
/dev/sda5           47746       60265   100566868+  83  Linux
/dev/sda6           60266       60801     4305388+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd4bdd4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdc: 1017 MB, 1017117696 bytes
33 heads, 63 sectors/track, 955 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         956      993263    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logical endings:


     phys=(217, 32, 63) logical=(955, 17, 42)

/dev/sda1 is the problem..

---

### Post by uRock on 2010-04-11
> **sam45 said:**
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc537805c

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]/dev/sda1   *           1       47745   383511681    7  HPFS/NTFS[/COLOR]
/dev/sda2           47746       60801   104872320    5  Extended
/dev/sda5           47746       60265   100566868+  83  Linux
/dev/sda6           60266       60801     4305388+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd4bdd4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdc: 1017 MB, 1017117696 bytes
33 heads, 63 sectors/track, 955 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         956      993263    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logical endings:


     phys=(217, 32, 63) logical=(955, 17, 42)

/dev/sda1 is the problem..

You are in luck, your Windows partition is still there. :)

When you restart does the boot menu show Windows as a selection?

---

### Post by sam45 on 2010-04-11
> **uRock said:**
> You are in luck, your Windows partition is still there. :)

When you restart does the boot menu show Windows as a selection?

that's a relief :)

yes, it's still in the GRUB
but when I select it, I get a reboot

---

### Post by uRock on 2010-04-11
Which version of Windows do you have? Chances are you will need to get a repair disk to fix Windows' boot loader.

---

### Post by sam45 on 2010-04-11
> **uRock said:**
> Which version of Windows do you have? Chances are you will need to get a repair disk to fix Windows' boot loader.

Windows 7 ultimate
I have the installation disk..

but why is Gparted showing /dev/sda1 (my main partition) as linux swap?

---

### Post by uRock on 2010-04-11
One of the good things is that you can access the NTFS partition via ubuntu to back up any data in case you have to reinstall Windows.

---

### Post by uRock on 2010-04-11
> **sam45 said:**
> Windows 7 ultimate
I have the installation disk..

but why is Gparted showing /dev/sda1 (my main partition) as linux swap?

That is very odd. When you go to Places then select the file system that is/was Windows are the files still there?

---

### Post by sam45 on 2010-04-11
> **uRock said:**
> One of the good things is that you can access the NTFS partition via ubuntu to back up any data in case you have to reinstall Windows.

and ehm, how can I acces it? :/
it's not in the list of partions in "computer"

edit

no, that partition isn't there..

---

### Post by uRock on 2010-04-11
It should show under the Places menu like the one I have highlighted in this screenshot.

---

### Post by sam45 on 2010-04-11
> **uRock said:**
> It should show under the Places menu like the one I have highlighted in this screenshot.

I know.. :(
but it isn't there...
only my second hard drive and my linux partiton..

---

### Post by sam45 on 2010-04-11
I tried this:

sam@PC:~$ swapoff /dev/sda1
swapoff: Not superuser.
sam@PC:~$ 

but.. =/

---

### Post by uRock on 2010-04-11
Can you run this command in a terminal and post the output?
```
free
```
This will show how much swap is being used and will let us know if the system is using that partition for that purpose.

---

### Post by sam45 on 2010-04-11
> **uRock said:**
> Can you run this command in a terminal and post the output?
```
free
```
This will show how much swap is being used and will let us know if the system is using that partition for that purpose.

sam@PC:~$ free
             total       used       free     shared    buffers     cached
Mem:       2061744    1109148     952596          0      94200     541712
-/+ buffers/cache:     473236    1588508
Swap:      4305380          0    4305380
sam@PC:~$ 

The system isn't using the partition atm I think..
only my 4.1 gig swap partition (according to system monitor)

---

### Post by uRock on 2010-04-11
That is a good thing. Sadly I do not know how to recover the partition. Hopefully someone will come along shortly that knows how.
I wish you luck with this.

Regards,
Ronnie

---

### Post by sam45 on 2010-04-11
> **uRock said:**
> That is a good thing. Sadly I do not know how to recover the partition. Hopefully someone will come along shortly that knows how.
I wish you luck with this.

Regards,
Ronnie


thanx a lot for your help ^^
I hope I can recover the partition, most of my files are on it..

---

### Post by srs5694 on 2010-04-11
My hunch is that you accidentally used the mkswap command on /dev/sda1 (on the command line or via a GUI tool). If so, it could be that recovery will be difficult. One option you should try first is ntfsclone:

```

sudo ntfsclone --save-image --output backup.img /dev/sda1

```This will save a copy of the NTFS data on /dev/sda1 to the file backup.img. Note that you must have sufficient free space on the partition on which you store backup.img to hold all the data on /dev/sda1. This could be tiny, if /dev/sda1 is mostly empty; or it could be as large as /dev/sda1, if it's completely full. This command may fail if the NTFS data structures have been damaged badly enough.

With this done, try your Windows installation/recovery disc. With any luck the Linux swap data structures will have done little enough damage that the Windows CHKDSK utility will be able to fix things. I don't know how like this is, though.

---

### Post by sam45 on 2010-04-11
> **srs5694 said:**
> My hunch is that you accidentally used the mkswap command on /dev/sda1 (on the command line or via a GUI tool). If so, it could be that recovery will be difficult. One option you should try first is ntfsclone:

```

sudo ntfsclone --save-image --output backup.img /dev/sda1

```This will save a copy of the NTFS data on /dev/sda1 to the file backup.img. Note that you must have sufficient free space on the partition on which you store backup.img to hold all the data on /dev/sda1. This could be tiny, if /dev/sda1 is mostly empty; or it could be as large as /dev/sda1, if it's completely full. This command may fail if the NTFS data structures have been damaged badly enough.

With this done, try your Windows installation/recovery disc. With any luck the Linux swap data structures will have done little enough damage that the Windows CHKDSK utility will be able to fix things. I don't know how like this is, though.

You are right, I used mkswap on the wrong partition..
I will try to recover the files your way..
I haven't used my pc much since this happend, so I hope the damage will be rather small..
too bad the files on that disc are about 200 gig if I remember well.. so I don't have enough space to back it up..

can't I browse the partition one way or another?

edit: 
sam@PC:~$ sudo ntfsclone --save-image --output backup.img /dev/sda1
sudo: ntfsclone: command not found

---

### Post by SPr on 2010-04-11
```

sudo  ntfs-3g.probe --readwrite /dev/sda1

```
Read the man page and [this link](http://ntfs-3g.org/support.html) first. [ntfs-3g maunal](http://www.tuxera.com/community/ntfs-3g-manual/). I've never used it so can not guarantee it wont cause more problems.

---

### Post by sam45 on 2010-04-11
> **SPr said:**
> ```

sudo  ntfs-3g.probe --readwrite /dev/sda1

```
Read the man page and [this link](http://ntfs-3g.org/support.html) first. [ntfs-3g maunal](http://www.tuxera.com/community/ntfs-3g-manual/). I've never used it so can not guarantee it wont cause more problems.

Anyone used something like this before?..
I really don't wanna cause any more dmg to my most important partition :s
and since I'm kinda new with linux, it's hard to understand all the information on those links..

---

### Post by SPr on 2010-04-11
You're quite right to be cautious and so am I which is why I gave the warning.

FWIW I have a 1GB partition on an external HDD that I have formatted to NTFS and written data to it. I ran ntfs-3g.probe on it and the data is still there so I can say that in my limited experience it does no harm.

---

### Post by sam45 on 2010-04-12
> **SPr said:**
> You're quite right to be cautious and so am I which is why I gave the warning.

FWIW I have a 1GB partition on an external HDD that I have formatted to NTFS and written data to it. I ran ntfs-3g.probe on it and the data is still there so I can say that in my limited experience it does no harm.

thanx for trying yourself 

but, 
sam@PC:~$ sudo  ntfs-3g.probe --readwrite /dev/sda1
[sudo] password for sam: 
sam@PC:~$ 

=/ seems like nothing changed.. can't mount /dev/sda1

sam@PC:~$ mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

---

### Post by sam45 on 2010-04-12
I tried to make a backup, but since there is not enough free space on my linux partition that's impossible.

sam@PC:~$ sudo ntfsclone --save-image --output backup.img /dev/sda1
ntfsclone v2.0.0 (libntfs 10:0:0)
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 392715956224 bytes (392716 MB)
Current device size: 392715961344 bytes (392716 MB)
Scanning volume ...
100.00 percent completed
Accounting clusters ...
Space in use       : 134076 MB (34.1%)   
ERROR: Destination doesn't have enough free space: 56773 MB < 134076 MB


but, if I move some files, I would have enough free space to make the backup on my 2nd HDD.
so, anyone knows how I can adapt the command to make it write to my 2nd HDD?

---

