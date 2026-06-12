---
title: "wont boot after atempting to set a static ip"
date: 2010-11-11
forum: General Help
---

### Post by ibod on 2010-11-11
Hi first i am fairly new to ubuntu, but am an experienced x windows user and glad to be 
i was trying to work out how to set a static ip in ubuntu 
what i did was ;-
right click the auto eth0 icon in the top panel
left click edit connection
wired tab
select auto eth0
edit
ipv4 tab
and changed the method from automatic (dhcp) to manual
then in addresses click add and entered  
address 192.168.1.20
netmask 255.255.255.0
gateway 192.168.1.1
ie my required static internal ip netmask and gateway to my router
i was prompted for the su password which i entered 
and upon reboot   i get [B] 
One or more of the mounts listed in /etc/fstab/ cannot yet be mounted: [/B]
**/home: waiting for uuid=97f9d57c-**....etc 

have booted from the live cd and looked in gparted and the /home partition is there 
/dev/sda2   ext4

i am not sure this is anything to do with the static ip setting or not 

thanks in advance for any help

the system is 
ubuntu 9.10 clean install from cd
dell dimension 4600
1gb ram
80 gb hd
intel pentium 4 2.8ghz

---

### Post by The Cog on 2010-11-11
Maybe an fsck will fix it. From a live CD, try:
**sudo fsck /dev/sda2**

Also, check that the UUID is correct. Again, from a live CD:
**sudo blkid**
will show all the UUIDs of the partitions.

Thirdly, verify that you can mount sda2 from the live CD (double-click it in Places and make sure it mounts and you can see the contents).

---

### Post by lisati on 2010-11-11
I think it's unlikely that changing your network settings caused this problem, and would go with The Cog's suggestions for starting the troubleshooting. 

As for the network settings, my own personal preference is for my routers to handle assignment of local IP addresses, making the necessary changes to static IP settings in my routers instead of my OS. This way, if I connect my laptop to someone else's network, I'm less likely to run into IP address allocation problems.

---

### Post by ibod on 2010-11-11
Hi The Cog 

thanks for your help
1.
**sudo fsck /dev/sda2**  results in :-

[B]fsck from util=linux-ng 2.16
e2fsck 1.41.9 (22 aug 2009)
/dev/sda2: clean, 15256/3891200 files, 14239191/15536863 blocks
[/B]
then 
2.
**sudo blkid**    results in :-

[B]/dev/loop0:type="squashfs"
/dev/sda1: uuid="2690fcf5-...." type="ext4"
/dev/sda3: uuid="b33599f7-...." type="swap"
[/B]

3.
only the /     partition shows up in places as "15GB File system"

tried manual mount 
**sudo mount -t ext4 /dev/sda2 /home**
and again 

**sudo blkid**
[B]/dev/loop0:type="squashfs"
/dev/sda1: uuid="2690fcf5-...." type="ext4"
/dev/sda3: uuid="b33599f7-...." type="swap"

[/B]still no /dev/sda2

tried clicking Computer in places  results in :-

[B]Nautilus could not creat the following required folders: /home/ubuntu/Desktop,/home/ubuntu/.nautilus.
before running nautilus, please creat these folders, 
or set permissions such that nautilus can creat them.
[/B]
of cause i did not do that :-)

its not looking good for my /home :-(

---

### Post by dcstar on 2010-11-12
> **ibod said:**
> 
..........
have booted from the live cd and looked in gparted and the /home partition is there 
/dev/sda2   ext4
..........

Use gparted to check the UUID of the partition and check if the /etc/fstab entry matches.

Make sure the partition type also matches.

---

### Post by endotherm on 2010-11-12
on the fsck, try running it with -f to force a check even if the volume is marked clean. it may turn up issues with parts of the disk that have not been read recently. 

as for your disks, lets start by looking at your partitions, and uuids. please post back
```

sudo fdisk -l
ls -l /dev/disks/by-uuid
cat /etc/fstab

```

---

### Post by ibod on 2010-11-12
> **dcstar said:**
> Use gparted to check the UUID of the partition and check if the /etc/fstab entry matches.

Make sure the partition type also matches.

checken in gparted right click the partition then information :-

[B]file system ext4
size 59.27gib
used 54.32gib
unused 4.95gib
flags

path /dev/sda2
status not mounted
label
uuid

first sector 29993355
last sector 154288259
total sectors 124294905[/B]

uuid in /etc/fstab

# / was on  /dev/sda1 during installation
uuid=2690fcf5-55bf-4095-acb3-080809386101 /                ext4
errors=remount-ro    0     1
[B]# /home was on /dev/sda2 during installation
uuid=97f9d57c-0ee4-4b26-a270-86e77de8ae9b /home     ext4
defaults                    0      2[/B]
# swap was on /dev/sda3 during installation
uuid= b33599f7-81a1-4d52-bd5b-7a9d5bc50de6  none      swap
sw                            0     0


just to be clear uuid in gparted is blank

---

### Post by oldfred on 2010-11-12
Some extra options on fsck - see man e2fsck for explanation of options.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sda2
if errors:
sudo e2fsck -f -y -v /dev/sda2

---

### Post by ibod on 2010-11-12
> **endotherm said:**
> on the fsck, try running it with -f to force a check even if the volume is marked clean. it may turn up issues with parts of the disk that have not been read recently. 

as for your disks, lets start by looking at your partitions, and uuids. please post back
```

sudo fdisk -l
ls -l /dev/disks/by-uuid
cat /etc/fstab

```


ok 
[B]$ sudo fsck -f /dev/sda2 
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda2: 15256/3891200 files (7.4% non-contiguous), 14239191/15536863 blocks[/B]


[B]$ sudo fdisk -l
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc5f30dc2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1867    14996646   83  Linux
/dev/sda2            1868        9604    62147452+  83  Linux
/dev/sda3            9605        9729     1004062+  82  Linux swap / Solaris
[/B]
I hope this is what you intended me to do if not then I need a little more guidance
had to look this up. :-)

first /[B]
$  ls -l /dev/disk/by-uuid|grep 2690fcf5-55bf-4095-acb3-080809386101
lrwxrwxrwx 1 root root 10 2010-11-12 15:26 2690fcf5-55bf-4095-acb3-080809386101 -> ../../sda1

[/B]second /home [B]
$ ls -l /dev/disk/by-uuid|grep 97f9d57c-0ee4-4b26-a270-86e77de8ae9b

[/B]third swap[B] 
$ ls -l /dev/disk/by-uuid|grep b33599f7-81a1-4d52-bd5b-7a9d5bc50de6
lrwxrwxrwx 1 root root 10 2010-11-12 15:22 b33599f7-81a1-4d52-bd5b-7a9d5bc50de6 -> ../../sda3[/B]


[B]$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0
[/B]
Thanks for your help but remember i only understand some of this where i can relate it to windows.

---

### Post by endotherm on 2010-11-12
ok, kewl.

fdisk -l prints out a list of your partitions. I asked for it, so I could see that your disk still has an sda2 partition, and that it is an Linux partition. so now we know that there is a partition there. good.

ls -l means "list the contents of this directory in long output format". long output is needed when listing /dev/disk/by-uuid.
by-uuid is a special folder that shows you the "universally unique identifier" associated with each partition in your system. that way we can see what the uuid for sda2 is. unfortunately, with the grep in the command, we can't quite tell from your output, so try running it like this
```
ls -l /dev/disk/by-uuid
```

this is the output on my machine.
```

orenji:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2010-11-11 03:38 06087798-ca47-4d39-bcad-407790fe1089 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2010-11-11 03:38 0bc8f47d-6aba-4960-bdf3-7f29ca1c68e6 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2010-11-11 03:38 331f7495-62df-4f33-bd4d-7cc01d6abf68 -> ../../sda1

```
note that from this, I can confirm that the uuid for sdb1 is 06087798-ca47-4d39-bcad-407790fe1089


on an linux system, /etc/fstab is a file that contains instructions on how each disk in your system is supposed to be mounted. here is some documentation on fstab: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

here is my fstab:
```
orenji:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=331f7495-62df-4f33-bd4d-7cc01d6abf68 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=0bc8f47d-6aba-4960-bdf3-7f29ca1c68e6 /home           ext4    defaults        0       2
# swap was on /dev/sdb1 during installation
UUID=06087798-ca47-4d39-bcad-407790fe1089 none            swap    sw              0       0
```

from this, I can see that I have 3 disks that mount to /, /home, and swap, and that they use the ext4 file system (or swap). 

now, I see that your / partiton is aufs, which I have never seen on ubuntu before. are you running off a thumbdrive, or a wubi installation? do you know what type of partition sda2 is (ext3, ext4, aufs, reiserfs, etc)? you can probably find out via gparted if you don;t know already. 


so, run the by-uuid command again so we can get the uuid for sda2 and the filesystem type, we'll just add a line to your fstab for sda2, and hopefully all will mount correctly.

---

### Post by dcstar on 2010-11-12
> **ibod said:**
> checken in gparted right click the partition then information :-

[B]file system ext4
size 59.27gib
used 54.32gib
unused 4.95gib
flags

path /dev/sda2
status not mounted
label
uuid
............
just to be clear uuid in gparted is blank
This will create a new random UUID for the partition:
```
sudo tune2fs -U random /dev/sda2
```
You will have to update /etc/fstab to match it.

---

### Post by ibod on 2010-11-14
> **lisati said:**
> I think it's unlikely that changing your network settings caused this problem, and would go with The Cog's suggestions for starting the troubleshooting. 

As for the network settings, my own personal preference is for my routers to handle assignment of local IP addresses, making the necessary changes to static IP settings in my routers instead of my OS. This way, if I connect my laptop to someone else's network, I'm less likely to run into IP address allocation problems.


Hi Thanks for that. 

I had tried to do it that way first but could not get it to work 
but having ether messed things up a bit or more likely had some bad luck
I looked back at the router and found a type in the MAC address 
so that should work fine 
when I get the screwed up partition fixed

---

### Post by ibod on 2010-11-14
> **oldfred said:**
> Some extra options on fsck - see man e2fsck for explanation of options.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sda2
if errors:
sudo e2fsck -f -y -v /dev/sda2

I would just like to say that when I promote Ubuntu to people  I hear them say so often 
" But there is no support, what if it goes wrong?"

Well the answer to this is so simple " They are Wrong!"

Thanks for all you continued help and support :)

output from sudo e2fsck -C0 -p -f -v /dev/sda2

[B]$ sudo e2fsck -C0 -p -f -v /dev/sda2
                                                                               
   15256 inodes used (0.39%)
    1111 non-contiguous files (7.3%)
      12 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 14955/266/15
14239191 blocks used (91.65%)
       0 bad blocks
      14 large files

   11451 regular files
    3786 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
      10 symbolic links (10 fast symbolic links)
       0 sockets
--------
   15247 files
$[/B]

could not see any errors so did not do sudo e2fsck -f -y -v /dev/sda2

---

### Post by ibod on 2010-11-14
> **endotherm said:**
> ok, kewl.


```
ls -l /dev/disk/by-uuid
```now, I see that your / partiton is aufs, which I have never seen on ubuntu before. are you running off a thumbdrive, or a wubi installation? do you know what type of partition sda2 is (ext3, ext4, aufs, reiserfs, etc)? you can probably find out via gparted if you don;t know already. 


so, run the by-uuid command again so we can get the uuid for sda2 and the filesystem type, we'll just add a line to your fstab for sda2, and hopefully all will mount correctly.


Ok I see now what went wrong here, and why i could not get it to work the way you intended. Here is the output you wanted.

```
 
$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2010-11-14 09:41 2690fcf5-55bf-4095-acb3-080809386101 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-11-14 09:41 b33599f7-81a1-4d52-bd5b-7a9d5bc50de6 -> ../../sda3
$ 

```no sda2 See message #7 gparted shows no uuid for sda2 this may be the problem ?

/ partition should be ext4
/home should be ext4
/swap should be swap
i installed from an official ubuntu 9.10 cd ordered from the ubuntu shop
all these tests are run by booting from that live cd

I am not sure where you saw the aufs but will read back and post any thing i can find to help

---

### Post by ibod on 2010-11-14
> **endotherm said:**
> ok, kewl.

now, I see that your / partiton is aufs, which I have never seen on ubuntu before. are you running off a thumbdrive, or a wubi installation? do you know what type of partition sda2 is (ext3, ext4, aufs, reiserfs, etc)? you can probably find out via gparted if you don;t know already.



Ok  have read back at the posts here

I installed this system and manually set up the partitions a 15GB / at the beginning of the drive (more than plenty of room) as ext4, then a swap at the end (more than double my RAM) swap, then the rest in the middle as /home sda2 ext4.

The system has been working for about 2 years


Opps ! having thought about whats going on here and the ext4 v aufs inconsistency in my posts....
I Have been looking at the live cd boot fstab

```

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0
ubuntu@ubuntu:~$

```ok brain in  gear now !

here is the contents of my /ect/fstab.  as you can see / is indeed ext4

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2690fcf5-55bf-4095-acb3-080809386101 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=97f9d57c-0ee4-4b26-a270-86e77de8ae9b /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=b33599f7-81a1-4d52-bd5b-7a9d5bc50de6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```I am concerned about the errors=ro is this normal or a problem ?

```

 # / was on /dev/sda1 during installation
UUID=2690fcf5-55bf-4095-acb3-080809386101 /               ext4    errors=remount-ro 0       1

```Sorry for misleading you all with a stupid mistake :oops:

---

### Post by ibod on 2010-11-14
> **dcstar said:**
> This will create a new random UUID for the partition:
```
sudo tune2fs -U random /dev/sda2
```You will have to update /etc/fstab to match it.


would making a backup of this partition be possible and sensible,  with it in its current state, before i create the new uuid.

---

### Post by ibod on 2010-11-15
> **dcstar said:**
> This will create a new random UUID for the partition:
```
sudo tune2fs -U random /dev/sda2
```You will have to update /etc/fstab to match it.

Hi 
did that 

```

$ sudo tune2fs -U random /dev/sda2
tune2fs 1.41.9 (22-AUG-2009)
$

```looked in gparted again for the uuid to add to /etc/fstab

[B]
File system:        ext4
Size:                  59.27gib
Used:                 54.32gib   (92%)
Unused:              4.95gib    (8%)
Flags:

Path:                 /dev/sda2
Status:              not mounted
Label:
UUID:

First Sector:      29993555
Last Sector:       154288259
Total Sectors:    124294905
[/B]

uuid still missing

rebooted and looked again still no uuid

also tried

```

$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2010-11-15 22:54 2690fcf5-55bf-4095-acb3-080809386101 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-11-15 22:38 b33599f7-81a1-4d52-bd5b-7a9d5bc50de6 -> ../../sda3
$

``` 

did this work and i am looking in the wrong place for the uuid or did i get something wrong here

---

### Post by ibod on 2010-11-16
ok making a little progress here 

tune2fs -l /dev/sda2 to see the correct new uuid 

```

**$ sudo tune2fs -l /dev/sda2**
tune2fs 1.41.9 (22-Aug-2009)
Filesystem volume name:   <none>
Last mounted on:          /home
**Filesystem UUID:          50a282d6-5a05-46e8-8100-6ec614f3cba2**
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              3891200
Block count:              15536863
Reserved block count:     776843
Free blocks:              1297672
Free inodes:              3875944
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1020
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sun Feb 28 16:34:28 2010
Last mount time:          Thu Nov 11 22:32:02 2010
Last write time:          Mon Nov 15 22:31:36 2010
Mount count:              0
Maximum mount count:      37
Last checked:             Sun Nov 14 11:46:46 2010
Check interval:           15552000 (6 months)
Next check after:         Fri May 13 11:46:46 2011
Lifetime writes:          162 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      93dcd47f-6de0-478c-9fd3-7f7156a77635
Journal backup:           inode blocks
ubuntu@ubuntu:~$ 

```

This shows the new uuid 
dont know why it still shows as blank in gparted 

then set the new uuid in /etc/fstab
my new fstab

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2690fcf5-55bf-4095-acb3-080809386101 /               ext4    errors=remount-ro 0       1
[B]# /home was on /dev/sda2 during installation
UUID=50a282d6-5a05-46e8-8100-6ec614f3cba2 /home           ext4    defaults        0       2[/B]
# swap was on /dev/sda3 during installation
UUID=b33599f7-81a1-4d52-bd5b-7a9d5bc50de6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

but still i get the same message on boot 

[B]One or more of the mounts listed in /etc/fstab cannot yet ne mounted:
/home : waiting for UUID=50a282d6-5a05-46e8-8100-6ec614f3cba2[/B]

...

---

### Post by ibod on 2010-11-16
The current situation is that when booted with the live cd  i can now, mount the sda2 partition with 

```

$ sudo mount -t ext4 /dev/sda2 /media

```

and can then see the contents
but as in the above post the system still will not boot  

Any help with this would be appreciated as i have run out of options 

Thanks

---

### Post by matt_symes on 2010-11-16
Hi

Thats odd. It looks fine to me but it is late so i might have missed something. I will have another gander tomorrow.

Have you considered looking in the logs? Syslog or kernel log would be where i would look to hopefully find more meaningful error messages than *waiting on.....*

mount the main partition and have a look in /var/log

BTW to answer your earlier question, what is:

> errors=remount-roThis instruction will mount the file system as read only on the next boot up if the file system encounters a problem. This forces a user to run fsck to check the volume for errors.

Kind regards

---

### Post by ibod on 2010-11-17
> **matt_symes said:**
> Hi

Thats odd. It looks fine to me but it is late so i might have missed something. I will have another gander tomorrow.

Have you considered looking in the logs? Syslog or kernel log would be where i would look to hopefully find more meaningful error messages than *waiting on.....*

mount the main partition and have a look in /var/log

BTW to answer your earlier question, what is:

                                                 errors=remount-ro                       

This instruction will mount the file system as read only on the next boot up if the file system encounters a problem. This forces a user to run fsck to check the volume for errors.

Kind regards

Hi Matt 
Thanks for your reply and suggestions.  I will look at the logs to see it i can make sense of anything in there.
 
Late for me as well, had already given up for the day, been working on this for a few days now, and was determined to work this through. Rather than just reload and slap the backup (even though a little older than i would have liked ) back on. Ubuntu is so easy and fast to do it that way, but you don't learn if all you ever do is reload! I am slow to learn and make enough stupid mistakes as you can see above, but that does not stop me, it just slows me down.

This morning I printed the hole thread out and decided to work through it again to see if any steps had made a difference. I had already noted that i could now mount  /dev/sda2 while booted to the live cd, this had been roughly since i created the new uuid with tune2fs, but still could not boot from the hard drive. I was still not seeing the new uuid with some commands that I thought should show it.

I started with The Cog's suggestion fsck to fix errors and rebooted the cd to look for any improvements. 

I looked in places to make sure my /home (/dev/sda2) was not there, and there it was!
I did a restart and took the cd out and the system booted 

All is now working :-)

I still don't understand exactly what caused this or what half of what i did means, but everyone's  help got me there.

If anyone understands what happened here and can tidy this thread up or explain it, it may help someone else in the future. 

I will leave it open for a week or so, but after that will mark it as solved

Thanks for all the help I have been given here.

---

### Post by endotherm on 2010-11-19
my guess is that a sector that contained information about your partition was corrupted, including the UUID, but also bothering other crucial bits of the partition metadata. once you genned a new UUID, that piece was taken care of, and the drive became mountable. after that, you were able to perform a disk scan, which recovered or corrected the rest of the corrupted metadata. 

just a guess. glad everything worked out!

---

### Post by ibod on 2010-11-19
OK Thanks endotherm. 

That sounds as close as we are going to get to this. 

Thank once again to all for their help :-)

---

