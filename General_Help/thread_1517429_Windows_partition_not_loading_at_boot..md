---
title: "Windows partition not loading at boot."
date: 2010-06-25
forum: General Help
---

### Post by rmjohnson144 on 2010-06-25
I have a big problem of my windows partition not being active at boot and I have to open it manually from places or somewhere.

My problem is Deluge and my torrents.  If I start Deluge at boot I get errors as it can't find the windows partition.  Once I open the partition for Places, then Deluge proceeds with no issues.

How can I get the Windows partition to load at boot?
-=Mark=-
p.s. I've been searching for a while with nothing that works for me.

---

### Post by lukashjanssen on 2010-06-25
Ah, this is an issue I've had to deal with quite a few times.

What you're trying to do is mount the Windows partition at start-up.
To do that, you're going to need to use the command line and edit the fstab file.
It's really not that difficult at all. However, all links you've made to your Windows partition (such as in Rhythmbox or a launcher) will have to be remade, as the partition will be mounted in a separate location. For you, this means that you will have to re-enable the settings in Deluge to point to the new mount point.

Ok, to automount the Windows partition:

1) Unmount the Windows partition (right click on desktop icon or however)
2) Open up a terminal
3) Type ```
sudo fdisk -l
```4) Find the Windows partition (should be type NTFS or FAT32) and its location (probably /dev/sda1 or something similar)
5) Create a mount point: type ```
sudo mkdir /windows
``` or anything else you'd like to name the directory in place of 'windows.'
6) Backup the fstab file by typing ```
sudo cp /etc/fstab /etc/fstab_backup
```7) Type ```
sudo gedit /etc/fstab
```8} It will look crazy as hell
9) Simply add at the very bottom of the file ```
"LOCATION" "MOUNT POINT" "PARTITION TYPE" default 0 0
```10) For me this looks like ```
/dev/sda2 /windows ntfs defaults 0 0
```11) Save and exit

Good luck! If you get confused, take a look at this: [http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by rmjohnson144 on 2010-06-25
hmm, I just did that and it didn't work.  I then tried yours as it was using a different directory.(i was using /media/windows) but that shouldn't matter. but it still won't work.  after reading that article, I think maybe my fstab is corrupt.  it has a strange output.  especially the last line.

My original fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1d0b112d-eae1-4331-ab08-6bbe19caa4c6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=88c96334-8aa1-43b7-9e33-c519c2310c1d none            swap    sw              0       0

```

Thanks for your help
-=Mark=-

---

### Post by oldfred on 2010-06-25
Your fstab is using UUIDs which is slightly better than partition entries.
Your last entry is just swap so what do you think is wrong?

After editing fstab run this and it will either give an error message or just return to the terminal if it is ok. Reloads fstab.

sudo mount -a

To see UUIDs

sudo blkid

---

### Post by rmjohnson144 on 2010-06-25
In my fsstab it was listing the last part of the lines under itself(wrapping), so the last read sw 0 0 and thought it was an error.  

but my drive still doesn't load properly.  I can find it in places, but when I start up Deluge it errors out because it can't find it.

here is what I did, in hopes someone can see my mistake.

my fdisk -l reports:
```
mark@mark-asus:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
12 heads, 4 sectors/track, 40698441 cylinders
Units = cylinders of 48 * 512 = 24576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb1df1280

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          43    32000043   768000000    7  HPFS/NTFS
/dev/sda2        32000086    40698411   208759809    5  Extended
/dev/sda5        32000086    40343979   200253440   83  Linux
/dev/sda6        40344022    40698411     8505344   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x38c45e3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2              13       60802   488282112    7  HPFS/NTFS

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x228a67bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243202  1953512448    7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x330ca779

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       30516   245011456    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

```

My updated fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1d0b112d-eae1-4331-ab08-6bbe19caa4c6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=88c96334-8aa1-43b7-9e33-c519c2310c1d none            swap    sw              0       0
/dev/sdb1 /windows ntfs defaults 0 0
```

should I be using the UUId method? or will it accept both?

Thanks
-=Mark=-
ps I'm using the 1tb drive to dual boot my Windows 7 Ult x64 and Ubuntu 10.4 x64 on the same drive.  My other drives are for backup, data, and rescue.

---

### Post by oldfred on 2010-06-25
You can use UUID, label or partition. And they do not have to be the same but must refer to valid items.

If you do this do you get any errors or does it just come back to terminal?

sudo mount -a

---

### Post by rmjohnson144 on 2010-06-25
It just drops to terminal.

---

### Post by oldfred on 2010-06-25
Then it mounts ok. With defaults like you have I have had no issues with my NTFS partition as I have both firefox and thunderbird profiles in the NTFS partition.

Is there someother configuration for deluge. I am not familiar with deluge.

---

### Post by rmjohnson144 on 2010-06-25
> **oldfred said:**
> Then it mounts ok. With defaults like you have I have had no issues with my NTFS partition as I have both firefox and thunderbird profiles in the NTFS partition.

Is there someother configuration for deluge. I am not familiar with deluge.

I just changed my download location for Firefox to point at my Win partition and I get nthis error:

```
/media/Win_Ubun/Users/Mark/Downloads/ati-driver-installer-10-6-x86.x86_64.run.part could not be saved, because an unknown error occurred.

```

Maybe I'll try changing my folder to /media/Win_Ubun and see what happens.
-=Mark=-

---

### Post by oldfred on 2010-06-25
What path is 

/media/Win_Ubun/Users/Mark/Downloads

I thought you mounted windows to:

/dev/sdb1 /windows

So should not the first part of the path be 
/windows/....

---

### Post by mexicanseaf00d on 2010-06-25
hi, i'm really not sure, but the /dev/sdb1 looks quite small .. try the /dev/sdb2

---

### Post by gadolinio on 2010-06-25
I've accomplished what you're trying to do using these programs:
disk-manager (in ubuntu 8.10 and 9.04)
pysdm (in ubuntu 10.04; disk manager isn't available for this version).

You can install them with System--> administration--> Synaptic package manager.
The application appears under System--> administration.

Pysdm is more user-friendly. You have each partition listed, and you can go to options. Set it to be automatically mounted on startup, and enable write support.

---

### Post by rmjohnson144 on 2010-06-25
> **oldfred said:**
> What path is 

/media/Win_Ubun/Users/Mark/Downloads

This is my Downloads path Ubuntu setup when I select the drive from the Places menu.  It came up with Win_Ubun as I named the drive Win/Ubun during formatting.

> I thought you mounted windows to:

/dev/sdb1 /windows

So should not the first part of the path be 
/windows/....

I can't find this path anywhere at all.  Where would it be located?  Normally it shows up on the desktop.

Win/Ubun only shows up on the desktop after I open it from the Places menu.  

My desktop shortcut to my uTorrent folder also doesn't work at boot, and the icon has a padlock with a document for an icon and a X on the lower corner of the icon.  so it's not recognizing the folder either.

Thanks a ton for you helping me with this.  It's much appreciated.
-=Mark=-

---

### Post by oldfred on 2010-06-26
I did not realize that was the name of your computer. You mounted windows to /windows. It will be a folder directly off root. Which may not be where you want it. If you do places, computer, filesystem, it will be at the bottom of the list of all your root folders. Since it is not in /media or /home it will not appear in the normal left pane of places.

I mount my shared NTFS directly into /home/fred/shared where I had created mkdir /home/fred/shared as my mount

```
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  
```

In lucid I am changing it to the same way I mount my /data  partition.
I mount it to sudo mkdir /usr/local/fred/shared so it is now hidden. Thin I link it into /home. With my data partition I link each folder into /home to replace all my default folders for data.

ln -s /usr/local/fred/shared

from a terminal you could do this and then your windows will appear in /home even though it is still in root. You do have to remember its true location in case of issues.

ln -s /windows

---

### Post by rmjohnson144 on 2010-06-26
> **mexicanseaf00d said:**
> hi, i'm really not sure, but the /dev/sdb1 looks quite small .. try the /dev/sdb2

I installed pysdm and it lists /dev/sda1 as /dev/sdb2?  and /dev/sdb2 is listed as /dev/sdb2 as well.

I rename sda1 to sda1 as it should be and reboot. 

Now I get all my hard drives listed on the desktop as it should be, except of course, Win/Ubun (sda1).

I couldn't see a way of mounting at startup in pysdm.  It had very few options.  but after I changes the name from sdb2 to the sda1 it should be, pysdm still had sdb2 at the lower right corner, and in the next tab, things were still listed as sdb2 there as well.

Thanks Gadilinio for the pysdm program.  It will come in handy.

should I be changing things elsewhere to get this change permanent?
-=Mark=-
to be clear, both sda1 and sdb2 both point at sdb2

---

### Post by rmjohnson144 on 2010-06-26
I got it figured out finally.

After seeing my HD icons appear on the desktop I thought I'd check fstab and sure enough all my drives were listed in there now.  Then I notice sda1 is mapped to /dev/sdb2, so I edited fstab and changed it and now everything works fine now that I have remapped my download folders for shortcut and Deluge as they were still pointing at /media/Win_Ubun.

Thanks again for everyone's help
-=Mark=-

---

### Post by gadolinio on 2010-06-26
> **rmjohnson144 said:**
> I installed pysdm and it lists /dev/sda1 as /dev/sdb2?  and /dev/sdb2 is listed as /dev/sdb2 as well.

I rename sda1 to sda1 as it should be and reboot. 

Now I get all my hard drives listed on the desktop as it should be, except of course, Win/Ubun (sda1).

I couldn't see a way of mounting at startup in pysdm.  It had very few options.  but after I changes the name from sdb2 to the sda1 it should be, pysdm still had sdb2 at the lower right corner, and in the next tab, things were still listed as sdb2 there as well.

Thanks Gadilinio for the pysdm program.  It will come in handy.

should I be changing things elsewhere to get this change permanent?
-=Mark=-
to be clear, both sda1 and sdb2 both point at sdb2
I don't understand that problem about the incorrect name for the partitions.
To set the partition to be mounted on startup: in the main window select the partition; then on the right you'll see a textbox saying "options", then 2 buttons; the second, "assistant", gives you another window. In that window you can tick the option "mount filesystem on startup". I have all the other options of that tab unselected.

---

### Post by rmjohnson144 on 2010-06-26
> **gadolinio said:**
> I don't understand that problem about the incorrect name for the partitions.

me either.  lol  I just select SDA1 in the list on the side bar and a pop up shows says, "/dev/sdb2 hasn't been configured.  Do you want to configure now?  If I click OK, then it maps sda1 to sdb2.  Same if I go to sdb2, it says it the exact same thing, but it is actually sdb2.

> To set the partition to be mounted on startup: in the main window select the partition; then on the right you'll see a textbox saying "options", then 2 buttons; the second, "assistant", gives you another window. In that window you can tick the option "mount filesystem on startup". I have all the other options of that tab unselected.

ah, the assistant threw me off.  It has a blue question mark which is normally reserved for help files and I didn't press it.  instead I was right clicking the mount button for extra options.  It does woork fine for me now though and already has mount on startup.

also, all my ntfs drives have mounting options selected in pysdm of,"mount the file shystem in read only" and "unmask for file permissions in octal   umask=000"

also, when I now startup pysdm I get some errors:
> Warning: Unknown especial options for ext4 filesystem
Warning: Unknown option: rw
Warning: nouser is not suitable for user
Warning: Unknown option: async
Warning: Unknown option: errors=remount-ro


This is my new fstab file:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid         0  0  
# / was on /dev/sda5 during installation
UUID=1d0b112d-eae1-4331-ab08-6bbe19caa4c6  /            ext4  errors=remount-ro           0  1  
# swap was on /dev/sda6 during installation
UUID=88c96334-8aa1-43b7-9e33-c519c2310c1d  none         swap  sw                          0  0  
/dev/sda1                                  /media/sda1  ntfs  defaults                    0  0  
/dev/sdb1                                  /media/sdb1  ntfs  defaults                    0  0  
/dev/sdc1                                  /media/sdc1  ntfs  defaults                    0  0  
/dev/sdc2                                  /media/sdc2  ntfs  defaults                    0  0  
/dev/sdd1                                  /media/sdd1  ntfs  nls=iso8859-1,ro,umask=000  0  0  
/dev/sdb2                                  /media/sdb2  ntfs  nls=iso8859-1,ro,umask=000  0  0  
```

also on my ext4 partition, it says, "errors=remount-ro"  what does this mean?

whew. my head is spinning.  lol.  I justc hopes this makes sense to you.
-=Mark=-

---

### Post by gadolinio on 2010-06-26
> **rmjohnson144 said:**
> ah, the assistant threw me off.  It has a blue question mark which is normally reserved for help files and I didn't press it.

Haha that's right, the icon isn't apropriate, nor is the button's name. I would have simply called it "options" or "configure", and no icon.

> **rmjohnson144 said:**
> 
also, all my ntfs drives have mounting options selected in pysdm of,"mount the file shystem in read only" and "unmask for file permissions in octal   umask=000"

I've used pysdm in a friend's computer and now I can't recall, but I think "mount the file system in read only" was selected, and i unselected it in order to allow the windows partition to be written on.

---

### Post by oldfred on 2010-06-27
I hope your can keep track of partitions better than I. I have a bunch but have to both label with disk utility or gparted and mount with names not partitions numbers. I use /share for the NTFS partiton I use with data I want for both windows and linux and /data for linux only data.

I created a spare and a beta partition but during install it only shows partition numbers, so of course I installed my beta to the spare. Fortunately I had not yet put any data into my spare, so I jsut relabeled them.

---

### Post by rmjohnson144 on 2010-06-27
Yeah, I always hated installs with multiple drives/partitions.  I have learned over the years to use drives of different sizes.  My current rig, if you noticed, are 250GB, 500GB, 1TB, and 2TB.  It makes it easier to know which drive is which.

at one time I had 4 drives exactly the same for a fast raid 0 array.  Well, when I stopped using raid it was a nightmare installing any OS.  even windows used only manufacturer's drive names, and since they all had the same name and size it was just easier to disconnect all drives but one drive and install the OS, then reconnect the other drives after wards.  unfortunately linux hates this and doesn't mount drives properly and even worse, doesn't keep it's drive letters. so, now sda1 becomes sdb1, sdc3 now becomes sda3, etc.

I thought this UUID thing it does in fstab would eliminate this problem, but apparently it hasn't worked for me yet.  so I wonder what's the point of the UUID?

-=Mark=-

---

