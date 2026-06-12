---
title: "Partition Resizing"
date: 2010-04-08
forum: General Help
---

### Post by KLStringer on 2010-04-08
I have a Ubuntu 9.10 server with a 698 GB Raid 5 array, during install I chose the LVM option so I could resize partitions later if I needed to & gave Ubuntu 243 GB of space and now need to expand it to the full array size. There is nothing else on the array. 

When I try booting in to Parted Magic I can resize the 243 GB partitions but I can't add any on the unused array space. PM shows me 3 partitions like so:

```

Partition              File System                Size                  Flags
--------------------------------------------------------------------------------
/dev/sda1                 lvm2                  698.15 GB              boot,lvm
/dev/sda2                 extended              243.17 GB
      /dev/sda5           ext2                  243.14 GB

```sda5 is child of sda2, has a mount point of /media/sda5 and I can play around with their space but never go above the 243.17 limit. I need to expand it to use the full 698 GB of the array and thought choosing to use the LVM option during install would allow me to do this but I can't figure out how to use the remaining ~455 GB of free space.

---

### Post by srs5694 on 2010-04-08
It sounds to me as if you created an LVM and then proceeded not to use it, so you'll get no benefit from it without further reconfiguration. To be sure, please post the output of "df -h". If you see entries that reference logical volumes in /dev/mapper, then I'm wrong and at least some of your storage is in the LVM; however, if you see no /dev/mapper entries in the "df -h" output, then you'll need to decide whether to begin using LVM or eliminate it and use more conventional partitions. An understanding of how you're using your disk space will be helpful -- are you storing big files in your /home directory tree, are you running a server with lots of space consumed in /var, etc.?

---

### Post by KLStringer on 2010-04-08
The server is used as a Samba file server, I need the user recordings  /home/recordings/recordings folder to be as big as possible. 

running df -h from root gives me:

```

Filesystem                      Size       Used     Avail      Use%      Mounted on
/dev/mapper/terrasan--temp-root
                                 201G       68G      123G       36%      /
udev                            1007M      172k      1007M       1%      /dev
none                            1007M        0       1007M       0%      /dev/shm
none                            1007M      292k      1007M       1%      /var/run
none                            1007M        0       1007M       0%      /var/lock
none                            1007M        0       1007M       0%      /lib/init/rw
/dev/sda5                        228M       15M       202M       7%      /boot

```

---

### Post by srs5694 on 2010-04-08
First, please verify the size of /dev/sda5 by typing "sudo parted -l /dev/sda". Your original post specified it as 243GB, but your "df -h" output indicates that its filesystem is only 228MB (not GB) in size. If the partition is 243GB but the filesystem is 228MB, then it may be worth correcting that discrepancy to recover over 200GB of disk space. If your original post's size report was a typo, then you can ignore this issue. (Your original post also specifies your extended partition is 243GB. Again, the fdisk output will reveal the truth of the matter.)

Second, my original hypothesis was incorrect; it looks like the bulk of your installation is in a logical volume, terrasan--temp-root, which is 200GB in size, of which 68GB is in use. Issues (if any) with /dev/sda5 aside, here is what I would do, in outline:


[list=1]
[*]Create a new logical volume (using lvcreate) of some convenient size, probably between 200GB and 400GB.
[*]Create a filesystem on this new logical volume. If the recordings you're storing are MP3s or other sub-GB files, I'd make it ext3fs or ReiserFS. If your recordings are video files (approaching or exceeding 1GB in size), then I'd make it JFS or XFS.
[*]Mount the new logical volume someplace convenient, such as /mnt.
[*]Copy everything from /home to /mnt. "cd /home; sudo tar cpf - ./ | (cd /mnt; sudo tar xvpf -)" should do it, assuming no typos on my part. This will take a while to finish.
[*]Edit /etc/fstab to mount the new logical volume at /home.
[*]Shut down all user programs except a single command prompt.
[*]Type "sudo mv /home /home-old". (If this fails, you may need to rename /home to /home-old using an emergency disc.)
[*]Reboot.
[*]Use df to verify that the new logical volume is mounted at /home.
[*]Verify that everything is working correctly. Take your time -- run the system for a few days, if necessary, to be comfortable.
[*]When you're satisfied that everything is working, remove /home-old. You can delay or even skip the following steps unless and until you feel a need to recover the ridiculous amount of disk space that your root (/) logical volume will now be consuming (200GB), compared to the files stored on it (probably about 5-10GB).
[*]Boot into an emergency disc.
[*]Resize the filesystem in /dev/mapper/terrasan--temp-root to a small size -- not much bigger than the used space. (You'll grow it slightly shortly.) You'll resize using filesystem-specific tools, such as resize2fs.
[*]Use lvresize to resize the terrasan--temp-root logical volume to a good size -- perhaps 1.5 to 2 times the used space. This *must* be bigger than the filesystem's size at this point.
[*]Use your filesystem resizer to resize the filesystem to fill the logical volume. This can usually be done by omitting a size parameter when you resize the filesystem.
[*]Reboot.
[*]If desired, increase the size of the new /home volume and its filesystem -- but I recommend leaving at least some free space in the volume group.
[/list]


I realize this is fairly complex. It could be simplified to just increase the size of the existing terrasan--temp-root logical volume; however, for a system like yours, having the system separate from the files your server is handling will greatly increase your options down the road. For instance, you'll be able to install a new OS (a new version of Ubuntu or another Linux distribution) alongside your current one so that you can test the new installation before deleting the current one.

---

### Post by KLStringer on 2010-04-09
The files are [COLOR=Red][.vox format]("http://en.wikipedia.org/wiki/VOX_%28file_format%29")[/COLOR], that rarely exceed more than a few MB's. This server is a temporary solution to store them off the main server so that QA can access them while we wait for a new RAID controller that can handle 2TB drives. Once that comes in I'll be building the permanent replacement and this server will be taken offline once everything has been copied over, until that happens I have to get the files off the main server so that it has free space to capture the recordings as they come in. Since this is temporary the quickest fix to gain the most size out of the array would be the best option.

Here's the output of  parted -l /dev/sda

```

Model: CERC terrasan-primar (scsi) 
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos 

Number      Start     End       Size      Type         File system   Flags 
   1        32.3kB    750GB     750GB    primary                      boot, lvm 
   2         750GB    750GB     255MB    extended
   5         750GB    750GB     255MB    logical            ext2 


Model: Linux device-mapper (linear) (dm) 
Disk /dev/mapper/terrsan--temp-swap_1: 6182MB 
Sector size (logical/physical): 512B/512B 
Partition Table: loop 


Number     Start      End       Size       File system        Flags
  1        0.00B      6182MB    6182MB     linux-swap(v1) 


Model: Linux device-mapper (linear) (dm) 
Disk /dev/mapper/terrsan--temp-root: 219GB 
Sector size (logical/physical): 512B/512B 
Partition Table: loop 


Number    Start     End      Size     File system      Flags
    1     0.00B     219GB    219GB    ext4

```

---

### Post by srs5694 on 2010-04-09
It appears you mistyped "MB" as "GB." This means that your /boot partition, and the extended partition that contains it, are reasonably sized for this installation.

The simpler solution is therefore to use lvresize to increase the size of your terrasan--temp-root logical volume, then use a filesystem resizer for whatever filesystem you're using to resize the filesystem to fit the new logical volume size. Check /etc/fstab or use blkid on the /dev/mapper/terrasan--temp-root file to identify the filesystem.

---

### Post by KLStringer on 2010-04-09
/dev/mapper/terrasan--temp-root is ext4 format. I've read the man files on lvresize but I don't know what to put in the command to make it resize /dev/mapper/terrasan--temp-root to the full array or lvcreate to make a new partition on /dev/mapper/terrasan--temp-root that uses the remaining free space in the array, or if I'm even understanding the commands correctly.

---

### Post by KLStringer on 2010-04-09
I've tried

lvresize  -L +400G /dev/mappr/terrasan--temp /recordings

which gives me the error:

Path required for Logical Volume "terrasan-temp"

and 

lvcreate /recordings +400G /dev/mapper/terrasan-temp-root

which gives me the error:

Volume group name expected (no slash)

---

### Post by KLStringer on 2010-04-09
From reading [http://manpages.ubuntu.com/manpages/karmic/man8/lvm.8.html](http://manpages.ubuntu.com/manpages/karmic/man8/lvm.8.html) I did lvm without any arguments, then did a pvdisplay and got this:

```

PV Name           /dev/sda1
VG Name           terrasan-temp
PV Size           698.15 GB / not usable  4.16 MB
Allocatable       Yes
PE Size (Kbyte)   4096
Total PE          178726
Free PE           125109
Allocated PE      53617
PV UUID           Lv5bpq-A15D-9c5J-4Dqy-WwL7-0RYI-UVPxMH

```I'm not sure what all that means but I think 

PV Name = Physical Volume Name
VG Name = the Volume Group Name
PV Size = Physical Volume Size

Now what I really don't know is how to use that to make new partition or resize an existing partition to gain the unused space.

A pvs command gave me

```

PV            VG              Fmt     Attr    PSize      Pfree
/dev/sda1    terrasan-temp    lvm2    a-     698.15G      488.71G

```

---

### Post by KLStringer on 2010-04-09
OK if I'm understanding this correctly I need to do:

lvcreate -L +400G -n/recordings

and it'll make a new logical volume thats 400GB in size in the /dev/sda1 primary volume

---

### Post by srs5694 on 2010-04-09
```

sudo lvresize -L +400G /dev/mapper/terrasan--temp-root

```

Note that your logical volume's device name includes "-root" at the end, and you should *not* include "/recordings", which is just an ordinary directory on the filesystem, with no special meaning for this command.

After you resize the logical volume, you must resize the filesystem it contains:

```

sudo resize2fs /dev/mapper/terrasan--temp-root

```

---

### Post by srs5694 on 2010-04-09
> **KLStringer said:**
> OK if I'm understanding this correctly I need to do:

lvcreate -L +400G -n/recordings

and it'll make a new logical volume thats 400GB in size in the /dev/sda1 primary volume

You could do that (but replace "/" with " "); however, this then brings you back to my much longer procedure in which you move data and edit /etc/fstab.

---

### Post by KLStringer on 2010-04-09
sudo lvresize -L +400G /dev/mapper/terrasan--temp-root

Gave me error: Volume Group "terrasan-temp" not found

lvcreate -L +400G -n recordings

Gave me error: Path required for Logical Volume "recordings" Please provide a volume group name

---

### Post by KLStringer on 2010-04-09
```
lvcreate -L +400G -n recordings terrsan-temp
```gave me Logical volume "recordings" created

Am I right in assuming that I can now boot back into Parted Magic and move the space around as I need to?

Nope can't do that, so I did 

```

mkfs -t ext3 -m 1 -v /dev/terrsan-temp/recordings

```

I got to step 4 of your outline and am leaving it copying everything over, will pick back up on Monday.

Thanks so much for all your help, have a good weekend!

---

### Post by KLStringer on 2010-04-12
Just stopped in to check on this omw to class and everything has copied over. In step 5 I don't know what I should put into the fstab file to mount  the new LV /mnt to /home.

Thanks again for all your help, hope you had a good weekend.

---

### Post by KLStringer on 2010-04-12
Since this is a temporary solution instead of mounting the new LV as /home and going through all of that is there a way to share out the new LV that's currently mounted at /mnt  with Samba? The LV that I created is 400GB in size and that's plenty to hold us over till the new hardware gets setup and installed.

What if I remounted the LV to /home/recordings/mnt could I share it that way since /home/recordings is already shared?

---

### Post by srs5694 on 2010-04-12
> **KLStringer said:**
> Since this is a temporary solution instead of mounting the new LV as /home and going through all of that is there a way to share out the new LV that's currently mounted at /mnt  with Samba? The LV that I created is 400GB in size and that's plenty to hold us over till the new hardware gets setup and installed.

What if I remounted the LV to /home/recordings/mnt could I share it that way since /home/recordings is already shared?

Yes, that should work fine.

---

### Post by KLStringer on 2010-04-12
Just to see if it would work I edited the smb.conf file and added:

```

[recordings]
;  comment = recordings folder
   path = /mnt/recordings/recordings
   browseable = yes
   writable = yes


```Under the [homes] section and now the LV that I mounted to /mnt shows on the network share. QA can access it and only copy files off the server which is exactly what we needed as the originals have to be kept safe from editing.

---

