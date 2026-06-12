---
title: "Windows files occupy Linux partition"
date: 2010-08-03
forum: General Help
---

### Post by HHelsinger on 2010-08-03
On my dual boot UbuntuLucid/WinXP machine, the windows partition, sda2, is mounted at /media/windows.   The entire windows system occupies 22GB.  Because it is mounted under /, it seems to also occupy 22GB of my Ubuntu partition, sda7.  Thus, out of the 38GB used on sda7, 22GB is really from Windows.  

I thought if I saved files in the Windows partition they wouldn't take up room on the Linux partition.  Seems not to be true.  

Is there any way of keeping the windows files accessible, and continuing to be able to save to the windows ntfs system, and yet not have files stored in windows take up space also on the Linux partition?

---

### Post by marshmallow1304 on 2010-08-03
No, files on the Windows partition will not use any space on any other partitions.

See
```
df -h
```
before and after mounting the partition.

---

### Post by HHelsinger on 2010-08-03
You are right.  This morning I looked at my other dual-boot machine, and the numbers on disk usage make sense.   I'll try to figure out why Linux on the laptop is so bloated.  Thanks.

---

### Post by dv3500ea on 2010-08-03
On the file systems tab of the system monitor (System -> Administration -> System Monitor), you can view the disk usage on each of your partitions.

It is most likely that the files in your home folder are taking up most of the space. I personally keep my /home on another partition.

Normally, you should find that the Linux partition has <8GB used not counting the contents of /home.

---

### Post by HHelsinger on 2010-08-03
My /home directory occupies only 1.1GB (I keep no Music,Video, or Photos on this machine).   

But Gparted tells me how much of the partition is used, and the Disk Analyzer under Accessories shows a windows directory under /media, and reports that directory as taking 22GB.   Drill down, and it is clear that this is the entire  Windows partition file system.  

Windows is in fact mounted at /media/Windows.   But its content isn't supposed to be counted.   

I know things aren't supposed to work this way --

---

### Post by rawlins02 on 2010-08-03
Post the output of: 

```

> sudo fdisk -l

```

also 

```

> df -h

```

Disk Analyzer is a nice tool to show sizes of your linux partitions and directories.  Disk Utility under System -> Administration will show you sizes and characteristics of all partitions on the entire hard disk.  

fdisk and df will help to determine where exactly the Windows OS exists on your drive.

---

### Post by HHelsinger on 2010-08-04
Here is the relevant information

from fdisk -l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2   *          13       12768   102462570    7  HPFS/NTFS
/dev/sda3           12769       19457    53729392+   5  Extended
/dev/sda5           12769       13029     2096451   83  Linux
/dev/sda6           13030       13290     2096451   82  Linux swap / Solaris
/dev/sda7   *       13291       19198    47455978+  83  Linux

```

and from df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              45G   39G  3.5G  92% /
none                 1002M  328K 1002M   1% /dev
none                 1006M  456K 1006M   1% /dev/shm
none                 1006M  288K 1006M   1% /var/run
none                 1006M     0 1006M   0% /var/lock
none                 1006M     0 1006M   0% /lib/init/rw
/dev/sda2              98G   22G   77G  22% /media/windows
/dev/sda5             2.0G   36M  1.9G   2% /media/extra

```

Here is the content of fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda7
UUID=1fbd52ac-70bb-4a82-af89-4f80bed9ed25     /    ext3    defaults,errors=remount-ro    0   1

# /dev/sda2
UUID=16680F9A680F782F    /media/windows    ntfs   defaults    0   0

# /dev/sda5
UUID=e2110b67-94df-4ef3-9bd2-3a6d06191320    /media/extra     ext3    defaults    0   0

# /dev/sda6
UUID=7d0f1fcd-cd9c-4857-9f78-9ea0652677c1    none    swap      sw      0   0

/dev/cdrom /media/cdrom auto rw,noauto,user,exec 0 0

```

Finally, I've attached an image of the output from Disk Analyzer.  It shows under /media the size(22GB) of sda2 mounted at /media/windows.

---

### Post by rawlins02 on 2010-08-04
You are automounting the Windows partition on startup.  First, do you want to do this?  And once that partition is mounted it becomes part of the file system total under /.  Unmount that partition using umount command and then run Disk Usage Analyzer.  The size amount under / should decrease by the 22GB listed under /media/Windows.  Then go around the Rings Chart and inventory the partitions and directories that constitute / and what should be 17GB.

---

### Post by HHelsinger on 2010-08-04
A good thought, but when I do that sda7, my ubuntu partition, reports that 38.8 GB out of 44.5 is used.   When I run Disk Usage Analyzer, it gives me roughly the same numbers for the file system, but now my linux root, / , has shrunk to a proper size because there is no /windows under /media.   Attached is a screenshot of the new report from Disk Usage Analyzer.

On my desktop system, with the windows partition similarly automounted at startup, I have no such problem.

---

### Post by oldfred on 2010-08-04
Under Karmic I mounted my shared NTFS partition into /home and it appeared to be part of the space. I now mount in a hidden location, so it does not show anywhere and link it into /home.
```

fred@fred-LucidDT:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc7              25G  5.7G   18G  25% /
none                  2.0G  380K  2.0G   1% /dev
none                  2.0G  284K  2.0G   1% /dev/shm
none                  2.0G  304K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda1              55G   36G   20G  66% /media/cdrive
/dev/sdc2             100G   23G   77G  24% /usr/local/fred/shared
/dev/sdc6              97G   53G   39G  58% /usr/local/fred/data
/dev/sdd2             1.6G  2.3M  1.5G   1% /media/New Volume
/dev/sdd1             359M  144M  215M  41% /media/C0CC-4E19
fred@fred-LucidDT:~$ 


```

---

### Post by HHelsinger on 2010-08-04
Sounds like that might work -- I'll try it in a moment.  But in the directory structure you printed, where is the hidden mount point?   Shouldn't the mountpoint be something like /media/.windows  ?  and then I take it you are suggesting a link from /media/.windows > [someplace unhidden like] /* or* /media/windows  .   

And even if this works, I'll remain puzzled why with identical fstab I should have this problem on one machine and not the other.

---

### Post by oldfred on 2010-08-04
I put my data & shared partitions into 

sudo mkdir /usr/local/fred
sudo mkdir /usr/local/fred/data
sudo mkdir /usr/local/fred/shared
sudo chown -R fred:fred /usr/local/fred
#sudo chmod -R 766 /usr/local/fred/data

I link all the folders in my data partition back into /home by running this from home (so it is the default location)

for i in `echo /usr/local/fred/data/*`;do ln -s $i; done
ln -s /usr/local/fred/shared

I have all this in a bash script with auto editing of fstab, so every install has all my data in the same locations.

---

