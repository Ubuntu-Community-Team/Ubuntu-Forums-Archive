---
title: "External HDD problem"
date: 2012-04-02
forum: General Help
---

### Post by gtdcubo on 2012-04-02
I am using Ubuntu 10.10. I have 2 * 1TB external hard drives for my data backups. These clearly show as 1TB each one, and I have them named as BACKUP01 & BACKUP02. When I try to move a backup of 38GB to one or other of my hard drives I get the message 'Error while copying to "BACKUP01". There is not enough space on the destination. Try to remove files to make space. There is 21.9 GB available, but 38.1 GB is required.' The problem with this message is that there ought to be much more that 21.9 GB left. I have used only 62.3 GB. So bearing in mind that the disk is one terrabyte and that there is 62.3 GB used, I ought to have 947.7 GB free space, not 21.9GB. I am trying hard to work out what is going on here. The only thing I can think of is that past deletes although they may have freed up the logical space, have not freed up the physical space. I have not come across this type of thing before. Normally the elimination of logical files should have cause the equivalent free up of physical space.

I would be interested in getting behind the graphical interface and seeing what might be going on. I do not know enough about unix type commands to even know how to navigate to what is my external hard drive. I am thinking of opening a terminal session and navigating to the external hard drive and seeing what occupancy there actually is, but I am finding it easy to imagine but dificult to execute. For instance in windows disks have a letter identifying them, and if my external HDD were X:\ I would just write X: and I would be there. This does not seem available in Linux

So briefly 
1. My actual problem is some kind of mis-reported disk occupancy
2. My handicap to self help is not being able to navigate to the disk in the terminal window

I would appreciate your help on both issues. I recognise that Linux is the better operating system, but it seems to me that the windows command prompt is more intuitive to use and navigate round the file system. But that may be just that I am used to it through work, though I gave up on Windows at home years ago. 

Thanks

---

### Post by CharlesA on 2012-04-02
What file system is on those two drives?

Also, run these commands when they are attached (and mounted):

```
sudo fdisk -l
```
```
df -ih
```
```
df -h
```

---

### Post by gtdcubo on 2012-04-02
What file system is on those two drives? 
I don't know, they may be raw. I just bought them, put them into this cradle and joined that to the PC by USB. This is some months ago, and I do not really keep a log, sorry.

I don't know how you get the code examples in a frame, this seems to be undocumented, but here are the outputs, inside your frame. You have to scroll to see it

Thanks
     Code:
```
     sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfbd708b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           25496       60802   283590656   83  Linux
/dev/sda2               1       16215   130244608   83  Linux
/dev/sda3           16215       25496    74549249    5  Extended
/dev/sda5           16215       25485    74455040   83  Linux
/dev/sda6           25485       25496       93184   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5ad34ea8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       60682   487424000    7  HPFS/NTFS

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5ad34ea7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       59917   481280000    7  HPFS/NTFS

Disk /dev/sdf: 16.0 GB, 16026435584 bytes
84 heads, 19 sectors/track, 19612 cylinders
Units = cylinders of 1596 * 512 = 817152 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe67dfcc6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           6       19613    15646784    7  HPFS/NTFS
```



     Code:
```
     df -ih

paul@VLC-GF7050VT-M:/$ df -ih
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda5               4.5M    342K    4.2M    8% /
none                    207K    1.1K    206K    1% /dev
none                    210K       5    210K    1% /dev/shm
none                    210K      89    209K    1% /var/run
none                    210K       4    210K    1% /var/lock
/dev/sda1                17M     90K     17M    1% /media/Data1
/dev/sda2               7.8M     323    7.8M    1% /media/Data2
/dev/sr0                   0       0       0    -  /media/OFFICE_2000
/dev/sdg1                23M    414K     22M    2% /media/BACKUP01
/dev/sdh1                20M    146K     20M    1% /media/BACKUP02
/dev/sdf1               6.3M     102    6.3M    1% /media/PENDRIVE


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              70G   62G  5.0G  93% /
none                  1.6G  380K  1.6G   1% /dev
none                  1.6G  572K  1.6G   1% /dev/shm
none                  1.6G  456K  1.6G   1% /var/run
none                  1.6G     0  1.6G   0% /var/lock
/dev/sda1             267G   54G  200G  22% /media/Data1
/dev/sda2             123G   39G   79G  33% /media/Data2
/dev/sr0              507M  507M     0 100% /media/OFFICE_2000
/dev/sdg1             465G  443G   22G  96% /media/BACKUP01
/dev/sdh1             459G  440G   20G  96% /media/BACKUP02
/dev/sdf1              15G  8.7G  6.3G  59% /media/PENDRIVE
```

---

### Post by CharlesA on 2012-04-02
Well both the drives look like they are formatted as NTFS and have one partition that is around 500GB of each.

```
/dev/sdg1             **465G**  443G   22G  96% /media/BACKUP01
/dev/sdh1             **459G**  440G   20G  96% /media/BACKUP02
```

Fdisk shows that they are 1TB but there is only one partition on each and it's nowhere near 1TB.

You could try running gparted and checking to see what the partitions look like:

```
gksu gparted
```

Do you have a copy of Windows you can boot to and see if it reports the full 1TB (+/- 10%)? I would recommend hooking them up to a Windows box if you can, and check what disk management says and also run a chkdsk on them.

Also, to add the code tags, click on the # in the toolbar after selecting your text. :)

---

### Post by gtdcubo on 2012-04-03
Thanks Charles, and thanks for tidying up my reply. I am unsure how to encapsulate code in boxes like this.

This PC used to be dual boot with windows and there may be some remnants of Windows on the hard drives, but I cannot say. It could be that the hard drives began as NTFS partitions.

It is your suggestion that jogged my memory.

---

### Post by CharlesA on 2012-04-03
Have you checked gparted to see what the partitions look like?

That would be the next step, fdisk says the drive is 1TB with one partition but that partition is only around 500GB in size.

I still think it would be a good idea to run chkdsk on it to make sure the file system is ok.

Normally any external drives you buy will be formatted as NTFS out of the box.

---

### Post by gtdcubo on 2012-04-03
Thanks for the advice Charles. My opening of this thread was perhaps dumb. The disk is working normally now and is reformatted to ext4. There has been no data loss.

---

### Post by CharlesA on 2012-04-03
> **gtdcubo said:**
> Thanks for the advice Charles. My opening of this thread was perhaps dumb. The disk is working normally now and is reformatted to ext4. There has been no data loss.
Good to hear. Is df -h reporting the correct free space?

---

