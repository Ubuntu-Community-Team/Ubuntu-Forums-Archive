---
title: "Data being duplicated"
date: 2010-06-15
forum: General Help
---

### Post by COKEDUDE on 2010-06-15
Could someone please take a look at my screenshots and tell me why my data is being duplicated. I store all my data in BOB so the 26.2 GB of data is expected. I don't store anything in .ecryptfs so the 26.2 GB of data is completely unexpected. Could you please explain why this is happening and how to fix it. Also when I used the file manager to look at the data there was no data in .ecryptfs.
[http://i46.tinypic.com/5x8m02.jpg](http://i46.tinypic.com/5x8m02.jpg)
[http://i50.tinypic.com/sz8i1x.jpg](http://i50.tinypic.com/sz8i1x.jpg)

---

### Post by jerome1232 on 2010-06-15
Your using an encrypted home folder, .ecryptfs is where all that data is kept. Your not seeing data duplication your just misunderstanding disk usage analyzers output.


It's saying the home folder has 26 G's, all of it is in the subfolder /home/bob/.ecryptfs  which is expected when your using an encrypted home directory.

---

### Post by COKEDUDE on 2010-06-16
> **jerome1232 said:**
> Your using an encrypted home folder, .ecryptfs is where all that data is kept. Your not seeing data duplication your just misunderstanding disk usage analyzers output.


It's saying the home folder has 26 G's, all of it is in the subfolder /home/bob/.ecryptfs  which is expected when your using an encrypted home directory.

There's 2 problems with what you said. The first being I get a low disk space warning every time I restart my computer. The second is I can't copy a 700 mb file to my desktop which proves there is no available space. Since the partition I am using is 52 GB the only explanation I can think of is that my data is being duplicated.
[http://i50.tinypic.com/sqplqh.jpg](http://i50.tinypic.com/sqplqh.jpg)

---

### Post by jerome1232 on 2010-06-16
What's the output of these commands, you can use du to further investigate folders by changing the path at the end of the command. The du line will print a list of directories and their size sorted (biggest at the bottom)

```
df -h
sudo du -x -B M --max-depth=2 /home | sort -n
```

Also have you emptied your trash?

---

### Post by COKEDUDE on 2010-06-16
Here it is. 
```
 ~ $ sudo du -x -B M --max-depth=2 /home | sort -n
1M	/home/bob
1M	/home/lost+found
1M	/home/Recycled
26822M	/home
26822M	/home/.ecryptfs
26822M	/home/.ecryptfs/bob
 ~ $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.4G  3.4G  5.6G  38% /
none                  1.6G  312K  1.6G   1% /dev
none                  1.6G  3.0M  1.6G   1% /dev/shm
none                  1.6G   88K  1.6G   1% /var/run
none                  1.6G     0  1.6G   0% /var/lock
none                  1.6G     0  1.6G   0% /lib/init/rw
/dev/sda6              29G   27G  378M  99% /home
/home/bob/.Private     29G   27G  378M  99% /home/bob
/dev/sr0              3.7G  3.7G     0 100% /media/KNOPPIX

```

---

### Post by jerome1232 on 2010-06-16
According to that I was correct


```
 ~ $ sudo du -x -B M --max-depth=2 /home | sort -n
1M	/home/bob
1M	/home/lost+found
1M	/home/Recycled
26822M	/home
26822M	/home/.ecryptfs
26822M	/home/.ecryptfs/bob
 ~ $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.4G  3.4G  5.6G  38% /
none                  1.6G  312K  1.6G   1% /dev
none                  1.6G  3.0M  1.6G   1% /dev/shm
none                  1.6G   88K  1.6G   1% /var/run
none                  1.6G     0  1.6G   0% /var/lock
none                  1.6G     0  1.6G   0% /lib/init/rw
[COLOR="Blue"]/dev/sda6              29G   27G  378M  99% /home[/COLOR]
/home/bob/.Private     29G   27G  378M  99% /home/bob
/dev/sr0              3.7G  3.7G     0 100% /media/KNOPPIX
```

See how /home is only 29G, I'm supposing it's full at 27G because by default ext filesystems reserv 5% of the space for use by the root user so that a system will be still be functional for the root user in case it gets 100% filled up.

The mount point /home/bob/.Private is just Ubuntu's system for encryption, it's not duplicating the files there that just where the files actually reside. 

If the data was being duplicated under /home you would see a different total from du's output would have looked more like.

```
53644M	/home
26822M	/home/.ecryptfs
26822M	/home/.ecryptfs/bob
26822M /home/.ecryptfs/somefolder
```

---

### Post by COKEDUDE on 2010-06-16
Ok what you said makes sense :). 

How do I use /dev/sda1 Filesystem? I would like to store some stuff there. 

Lastly why isn't my linux-swap showing up? I know its there but I can't see it. 
```
~ $ sudo df -ahT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3    9.4G  3.4G  5.6G  38% /
proc          proc       0     0     0   -  /proc
none         sysfs       0     0     0   -  /sys
none       fusectl       0     0     0   -  /sys/fs/fuse/connections
none       debugfs       0     0     0   -  /sys/kernel/debug
none    securityfs       0     0     0   -  /sys/kernel/security
none      devtmpfs    1.6G  312K  1.6G   1% /dev
none        devpts       0     0     0   -  /dev/pts
none         tmpfs    1.6G  772K  1.6G   1% /dev/shm
none         tmpfs    1.6G   88K  1.6G   1% /var/run
none         tmpfs    1.6G     0  1.6G   0% /var/lock
none         tmpfs    1.6G     0  1.6G   0% /lib/init/rw
/dev/sda6     ext3     29G   27G  345M  99% /home
binfmt_misc
       binfmt_misc       0     0     0   -  /proc/sys/fs/binfmt_misc
/home/bob/.Private
          ecryptfs     29G   27G  345M  99% /home/bob
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon    0.0K  0.0K  0.0K   -  /home/bob/.gvfs

```

Thx for explaining this to me.

---

### Post by jerome1232 on 2010-06-16
I guess df doesn't show swap by default since mine doesn't show it either.

If you wanted files to goto /dev/sda1 which is mounted at / you would have to write to anywhere outside of /home. You're user by default isn't allowed to do that without escalating it's privileges to root via sudo. Well you can write to /tmp but it get's wiped out periodically.


You could get the space reserved for root on /home back (it's really only needed on the / partition imo) by running this command, it will get you a few gigs to work with at least.

```
sudo tune2fs -m 0 /dev/sda6
```

Really though I think you just need to extend your /home partition! If you have free space on your disk I would do that.

---

### Post by COKEDUDE on 2010-06-16
> **jerome1232 said:**
> I guess df doesn't show swap by default since mine doesn't show it either.

If you wanted files to goto /dev/sda1 which is mounted at / you would have to write to anywhere outside of /home. You're user by default isn't allowed to do that without escalating it's privileges to root via sudo. Well you can write to /tmp but it get's wiped out periodically.


You could get the space reserved for root on /home back (it's really only needed on the / partition imo) by running this command, it will get you a few gigs to work with at least.

```
sudo tune2fs -m 0 /dev/sda6
```

**Really though I think you just need to extend your /home partition!** If you have free space on your disk I would do that.

What would this command do? I thought this would expand my home partition. 
```
sudo tune2fs -m 0 /dev/sda6
```

How would I delete /dev/sda1 and expand /dev/sda6 with that extra space?

---

### Post by jerome1232 on 2010-06-17
That command simply changes the reserved space for the root user on your home partition to zero, it would free up about 2 gigs of space for you to work with.


Your system files are on /dev/sda1, so deleting it would be a very bad idea.

Can you post the output of fdisk to help determining whether you can expand your home partition. 

```
sudo fdisk -l
```

While resizing partitions is fairly safe, it does put the data on that partition at risk, so whenever you play with partitions you should always have backups of your data somewhere.

---

### Post by COKEDUDE on 2010-06-17
I have a external HD to back up all my data on. Here is the output. 
```
~ $ sudo fdisk -l
[sudo] password for bob: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c8b89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1245     9999360   83  Linux
/dev/sda2            1246        5478    33998849    5  Extended
/dev/sda3   *        5479       12161    53681197+   7  HPFS/NTFS
/dev/sda5            1246        1743     3998720   82  Linux swap / Solaris
/dev/sda6            1744        5478    29999104   83  Linux

```

---

### Post by COKEDUDE on 2010-06-18
Could anyone tell me how would I delete /dev/sda1 and expand /dev/sda6 with that extra space?

---

### Post by jerome1232 on 2010-06-18
Well you can't delete /dev/sda1, it's your root partition, it contains your system files, You may be able to boot a live cd and use gparted to drag your partitions around but it looks to me like you have an extended partition in the middle of your drive surrounded by primary partitions, which can make fiddling with it difficult.

I would back up your data, then pop into a live cd and see if you can resize /dev/sda1 down smaller then move the extended partition, /dev/sda5 and /dev/sda6 closer to /dev/sda1 (more to the left) then extend the extended partition and /dev/sda6 out further up against your ntfs partition /dev/sda3. If i'm right that swap partition is nearly 4 GB's! You could stand to shrink that down to like 1 GB's as well unless you need to hibernate then swap needs to be at least as much as ram.

Gparted can be found under System -> Administration -> Gparted from the live cd.

It would take a very long time, if you look at gparted from the live cd you should see what I mean, you can always post back with screenshots of gparted if you have further questions on how to proceed. The gparted operation will take a very long time moving all those partitions around. 

Make sure you back up your data, partitioning is fairly safe but user error can really screw you up. I think we've all accidentally deleted a wrong partition by mistake. At least those of use that mess with the partitions way to much :)

---

### Post by COKEDUDE on 2010-06-19
> **jerome1232 said:**
> Well you can't delete /dev/sda1, it's your root partition, it contains your system files, You may be able to boot a live cd and use gparted to drag your partitions around but **it looks to me like you have an extended partition in the middle of your drive surrounded by primary partitions, which can make fiddling with it difficult.**

I would back up your data, then pop into a live cd and see if you can resize /dev/sda1 down smaller then move the extended partition, /dev/sda5 and /dev/sda6 closer to /dev/sda1 (more to the left) then extend the extended partition and /dev/sda6 out further up against your ntfs partition /dev/sda3. **If i'm right that swap partition is nearly 4 GB's!** You could stand to shrink that down to like 1 GB's as well unless you need to hibernate then swap needs to be at least as much as ram.

Gparted can be found under System -> Administration -> Gparted from the live cd.

It would take a very long time, if you look at gparted from the live cd you should see what I mean, you can always post back with screenshots of gparted if you have further questions on how to proceed. The gparted operation will take a very long time moving all those partitions around. 

Make sure you back up your data, partitioning is fairly safe but user error can really screw you up. I think we've all accidentally deleted a wrong partition by mistake. At least those of use that mess with the partitions way to much :)

I wasn't aware that I setup an extended partition. Any idea how I did that? I remember when I was installing mint I set up 3 partitions. The swap partition, a ext3 partition with the mount point of /, another ext3 partition with the mount point of /home. I thought that was common practice after reading several guides. 

Yes your right my swap partition is 4 GB. How did you know that? I have 4 GB of ram. For some reason I'm only able to use 3.2 GB of it. When I was reading guides about how to set up the swap partition it said to make it double how much ram you have. I thought having 8 GB would be very excessive so I chose to set it up with 4 GB. I do hibernate my computer since I use a laptop. 

If I were to wipe my HD how would you recommend me to setup my partitions? My HD is only 100 GB. I would like to keep about 40 GB for windows XP. I unfortunately need XP. I have a 1 TB external HD so I have no problem with backing up my data.

---

### Post by jerome1232 on 2010-06-19
When you make logical partitions (the default I believe when creating partitions during the install process) You make an extended partition. Extended partitions are simply partitions which hold one or more logical partitions. You can have up to 4 primary partitions on a disk. If you need more than that you can create an extended partition (which itself is a primary partition so 3 primary and 1 extended now) and create up to 15 I believe logical partitions inside that.

The Windows C: drive must reside on a primary partition. Linux doesn't care if it's in logical or primary partitions.

Linux can read ntfs drives fine and dandy, Windows however can't read or write to ext4 which is the default filesystem for Ubuntu, so with that in mind....

I would simply install Windows to a good sized partition, store all of your data there.

Install Ubuntu to the rest of the drive, how you do your partitions is up to you but it shouldn't need more than 20 GB's or so in the foreseeable future if your storing data on the Windows partition. (possibly a 15 GB / and a 4-5 GB swap ) You can go bigger with the root partition if you want to just to be safe, it depends on how many programs you install.

The way I knew your swap size was from the fdisk output.
> Units = cylinders of 16065 * 512 = 8225280 bytes

> /dev/sda5            1246        1743     3998720   82  Linux swap / Solaris


So swap is on cylnders 1246 through 1743 making it 497 cylinders total, each cylinder is 8225280 bytes, so 497 * 8225280 = 4087964160 bytes, divide that by 1024 3 times to get 3898.586 MB's.

As to the Ubuntu doesn't see all of your ram part it is one of 2 things.

A) Your integrated video or video card is stealing system ram for it's use

B) You installed the 32 bit version of Ubuntu, 32 bit Operating Systems (including windows) are limited to 4 GB's of ram which after system addressing is about 3.2 GB's of ram. You may want to try the 64 bit version of Ubuntu to see if it uses all your ram.

I hope that helps feel free to ask more questions. If you need more info.

---

### Post by COKEDUDE on 2010-06-22
> **jerome1232 said:**
> When you make logical partitions (the default I believe when creating partitions during the install process) You make an extended partition. Extended partitions are simply partitions which hold one or more logical partitions. You can have up to 4 primary partitions on a disk. If you need more than that you can create an extended partition (which itself is a primary partition so 3 primary and 1 extended now) and create up to 15 I believe logical partitions inside that.

The Windows C: drive must reside on a primary partition. Linux doesn't care if it's in logical or primary partitions.

**Linux can read ntfs drives fine and dandy, Windows however can't read or write to ext4 which is the default filesystem for Ubuntu, so with that in mind....**

I would simply install Windows to a good sized partition, store all of your data there.

Install Ubuntu to the rest of the drive, how you do your partitions is up to you but it shouldn't need more than 20 GB's or so in the foreseeable future if your storing data on the Windows partition. (possibly a 15 GB / and a 4-5 GB swap ) You can go bigger with the root partition if you want to just to be safe, it depends on how many programs you install.

The way I knew your swap size was from the fdisk output.



So swap is on cylnders 1246 through 1743 making it 497 cylinders total, each cylinder is 8225280 bytes, so 497 * 8225280 = 4087964160 bytes, divide that by 1024 3 times to get 3898.586 MB's.

As to the Ubuntu doesn't see all of your ram part it is one of 2 things.

A) Your integrated video or video card is stealing system ram for it's use

B) You installed the 32 bit version of Ubuntu, 32 bit Operating Systems (including windows) are limited to 4 GB's of ram which after system addressing is about 3.2 GB's of ram. You may want to try the 64 bit version of Ubuntu to see if it uses all your ram.

I hope that helps feel free to ask more questions. If you need more info.

I figured that out. It really stinks. Windows is a royal pain in the behind. 

I prefer to stick with mint which uses ext3. I really like all of the media codecs, the themes, and the mint menu. 

Should I make a boot partition? I have read throughout the forum that a lot of people make a boot partition. How do I check how many programs I have installed? How do I check how big the programs are? I don't think I have installed very many programs. 

What type of partitions do you usually create for yourself? 

Very nice with figuring out my swap partition size. I would have never of thought of that. 

I installed the 32 bit. 

Yes all of this helps A TON. Thx a lot for all the help so far.

---

### Post by jerome1232 on 2010-06-22
My setup is a little different because I use LVM but the concept is the same.


Here is my partition layout, back when I built this system /boot couldn't be on an lvm volume, that's the only reason I have a separate /boot, if I were to redo this today (grub can handle lvm now) I would leave /boot on the root partition.

I don't dual boot this computer, it's ubuntu only. Some of these volumes are quite small because one of the advantageous of lvm is I can expand any lvm volume while the system is running easily. So I don't have to worry about accidentally out growing specific partitions.

```
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/direbane-UbuntuRoot 15G  8.0G  6.1G  57% /
/dev/sda1                       265M  36M  216M  14% /boot
/dev/mapper/direbane-UbuntuHome 40G   26G   13G  68% /home
/dev/mapper/direbane-data       99G   59G   41G  60% /mnt/data
/dev/mapper/direbane-wow        25G   20G  4.1G  83% /mnt/wow

```

In your case I would do something like this (if your really intent on the separate /boot). There really isn't many good reasons for a separate /boot imo.


This is assuming you will store all your data on the windows drive.
```

/dev/sda1 ntfs /mnt/windows as large as possible
/dev/sda5 swap 4 GB's
/dev/sda6 ext4 / 15 GB's or so 20 should be a safe max. As you can see use about 8 GB's on mine.
/dev/sda7 ext4 /home assuming you store all your data on the windows drive, a couple GB's should be sufficient.
/dev/sda8 ext4 /boot 1 GB max
```


How I handle storing data on a seperate data partition is I create what are called symlinks, they are like shortcuts in Windows.

My /home/jeremy/Pictures folder is really a symlink that points to /mnt/data/Pictures, so When I open the "Pictures" folder in my home folder, it redirects me to the other partition. I do the same thing with Documents, Videos, and Downloads, anything that will get alot of files stored in it is actually on /mnt/data, /mnt/windows in your case.

I hope that helps.

---

