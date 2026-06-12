---
title: "Sharing a folder within a hardware RAID"
date: 2012-09-11
forum: General Help
---

### Post by trekbike on 2012-09-11
Good day!

I am relatively new to Linux and especially Ubuntu. I have read extensively within the forums looking for possible solutions but none I have found seem be sufficiently similar.

Current environment:

OS: Ubuntu 12.04 LTS 64-bit

Hardware involved - Custom build:
Asus P7P55D-E motherboard
Intel (hyperthreaded) Core 2 Duo 3.2GHz processor
8G DDR3 RAM
1 64GB solid state drive
4 1.5TB SATA drives supported by 3ware 9650SE-4LPML RAID controller
One caveaut is that the RAID is formatted as NTFS which is what it was running previously under Windows 7.

The idea is to have the OS running on the 64GB while the four larger SATA drives make up a 4TB drive to be used for storage and file sharing. The 3ware bios loads at boot-up and shows that it has 4 "member" drives.

The issue is that I would like to share the bulk of the contents of this drive with other users (running Windows 7).

The "Data" drive shows up in the home screen without any problem but the sharing seems to disappear with each re-boot. It appears similarly to plugging in an external (USB) drive which may be part of the problem. Additionally, I did install Samba but when attempting to share folders on the Data drive, Samba does not recognize the drive as being present.

I like Ubuntu, and I am sure that someone out there can shed some light as to what steps would be necessary to make this work as desired.

Can anyone point me in the right direction?

Thank you!

---

### Post by critin on 2012-09-11
> 
The "Data" drive shows up in the home screen without any problem but the **sharing seems to disappear with each re-boot**.Can you share  during that session?  Can the win7 machines read/write to it during that session?  If yes, it's setup right, and it's another issue.

If not, have you setup the network share in Win7 and rebooted 7?  Actually, reboot both machines.
> 
The "Data" drive shows up in the home screen without any problem but the  sharing seems to disappear with each re-boot. It appears similarly to  plugging in an external (USB) drive **which may be part of the problem**.No problem, it should show since it's on the same machine.

The Win7 machine has to get to it through Network Group.

---

### Post by trekbike on 2012-09-11
Good evening Critin,

Thank you for your response.

Just to be clear, the only OS on the system in question is Ubuntu. I over-wrote Windows 7 with this installation.  The laptops (in the house) are running various versions of Windows 7 and these are the machines I would like to secure access of the files in the RAID for.  Later on, I would like to allow a Boxee Box I have to be able to play the media files that would be shared as well but I'll save that for another day.

Without using Samba, I went into the "open" folder on the "data" drive and set the share up. Then, went into permissions and set the owner, group, and others to all have the ability to create and delete folders as well as read and write to file access...  At the bottom of permissions I clicked the box that says: "Apply Permissions to Enclosed Files" figuring this would drive the accessibility all the way into the folder (and sub-folders).

Without a re-boot, I attempted to access the folder. The "open" folder as well as the sub-folders within "open" are all displayed (on the laptops) but when I attempt to access any of them, Windows pops an error saying I do not have permission to access \\server\folder.

When I go into the sub-folder and perform the same actions, the laptops get the same response from Windows...

When I re-boot Ubuntu, and right-click on the "open" folder, all the sharing check-boxes are showing as un-shared yet they display as shared to the laptops... Again, they display as shared but I have no permissions to access.

Hopefully that clears up a few questions??

Thanks again!

---

### Post by redmk2 on 2012-09-12
> **trekbike said:**
> Good day!

I am relatively new to Linux and especially Ubuntu. I have read extensively within the forums looking for possible solutions but none I have found seem be sufficiently similar.

Current environment:

OS: Ubuntu 12.04 LTS 64-bit

Hardware involved - Custom build:
Asus P7P55D-E motherboard
Intel (hyperthreaded) Core 2 Duo 3.2GHz processor
8G DDR3 RAM
1 64GB solid state drive
4 1.5TB SATA drives supported by 3ware 9650SE-4LPML RAID controller
One caveaut is that the RAID is [COLOR="Red"]formatted as NTFS[/COLOR] which is what it was running previously under Windows 7.

The idea is to have the OS running on the 64GB while the four larger SATA drives make up a 4TB drive to be used for storage and file sharing. The 3ware bios loads at boot-up and shows that it has 4 "member" drives.

The issue is that I would like to share the bulk of the contents of this drive with other users (running Windows 7).

The "Data" drive shows up in the home screen without any problem but the sharing seems to disappear with each re-boot. It appears similarly to plugging in an external (USB) drive which may be part of the problem. Additionally, I did install Samba but when attempting to share folders on the Data drive, Samba does not recognize the drive as being present.

I like Ubuntu, and I am sure that someone out there can shed some light as to what steps would be necessary to make this work as desired.

Can anyone point me in the right direction?

Thank you!

There are couple of points you should be aware of...  

The RAID system works a block device level.  It will bond the physical hard drives into one virtual device.  

The file system format is what you need to be concerned with.  This is what partitions are for.  So whatever you do at the block level (RAID), it is at the partition level that you really need to be concerned with.  

As you already suspect the partition is not being mounted at boot up by any directives you control.  As it is an NTFS partition (by your description (in red) above) the device is being mounted as the OS thinks it should be mounted (e.g as a very large USB stick).  This also means that the shared settings are not retained.

You can add the partition to the /etc/fstab file to mount the partition at boot time.  When you do this the OS will not find the partition and mount it incorrectly to your needs, as it will already be mounted. 

User permissions for a NTFS partition are based on the directives used at mount time.  for more info on NTFS mounting see ```
man mount.ntfs
```

Since you control the permissions at mount only with NTFS, it would be best to consider who will need to access the data.  If more than just you are going to need access, then I would use a common group for all the users.  This would be used when mounting to set the permissions.  There is not "others" with NTFS and you can't use "*chmod 777*.

In a nutshell
```
 1. Mount the NTFS partition via /etc/fstab
  a. use the options provided in mount.ntfs 
     (uid and gid, permissions and umask)

 2. Create a common group for all users that will have access 


```

In the end, if you are going to permanently mount this device to the Ubuntu file system, you might consider copying the data to a temporary location and formatting the file system to EXT4.  You will have a slight performance gain and more flexibility with user/group permissions.

As far as Samba goes --  When you share folders (directories) with Windows hosts via the file manager (Nautilus?) you will be installing Samba.  Samba does not "see drives".  The SMB resource is ```
//COMPUTER_NAME/share_name    
```...the drive (partition) is transparent.  I'll bet you are looking at either the COMPUTER NAME or the share name.  Now if you name your share ambiguously...  ;-)

---

### Post by trekbike on 2012-09-13
Good morning,

The old adage that I have good news and bad news...

First the good news:
Reformatting the RAID from NTFS to EXT4 did the trick as far as "seeing" the shared folders from the network-attached Windows 7 laptops. 

Now the bad:
On both Windows machines, when double-clicking any of the shared folders, I am still running into a lack of permission warning that Windows pops when it detects that it cannot access the resource.

I went looking on other Windows 7 forums to see if there was anything about the Windows config that would affect this but everything always seems to point back at the source of the sharing.

I will add one interesting point. I configured the shared folders in Samba... When looking at the (non)-Samba sharing options on each folder, they appear as not-shared.  Probably nothing to worry about but wanted to pass along.

Any thoughts as to what the next step would be?

Thank you all!

---

### Post by redmk2 on 2012-09-13
> Any thoughts as to what the next step would be?

Did you mount the partition using /etc/fstab ?  If so, where in the file system did you mount it?

You should use the UUID when adding this partition to the /etc/fstab file.  You can find the UUID by using this command from the terminal```
sudo blkid -c /dev/null -o list
```

Post the output back here.

---

### Post by trekbike on 2012-09-18
Ok... I am going to have to plead stupidity.

I don't believe I mounted anything...  Remember, this is on a RAID controller and as a result of that (guessing) the drive simply showed up. Initially it appeared like a very large USB drive.  Since re-formatting, it now appears as a "normal" non-USB drive.

When accessing it from the Windows laptops, in Windows explorer, I enter:
\\computer

This makes the shared folders appear.

When attempting to enter one of the folders is when I get: 
Windows cannot access \\computer\folder and goes on to state that I do not have permission.

Does this help to clarify?  

Thank you!

---

### Post by redmk2 on 2012-09-18
> **trekbike said:**
> Ok... I am going to have to plead stupidity.

I don't believe I mounted anything...  Remember, this is on a RAID controller and as a result of that (guessing) the drive simply showed up. Initially it appeared like a very large USB drive.  Since re-formatting, it now appears as a "normal" non-USB drive.

The RAID controller manages the the block devices (i.e. the physical drives).  You mount partitions.> 

When accessing it from the Windows laptops, in Windows explorer, I enter:
\\computer

This makes the shared folders appear.
The folders are on mounted partitions.> 

When attempting to enter one of the folders is when I get: 
Windows cannot access \\computer\folder and goes on to state that I do not have permission.

Does this help to clarify?  

Thank you!
Post the output of these 2 commands
```
df -h

mount
```

[COLOR="Blue"]Edit: also post the output of this[/COLOR]```
cat /etc/fstab
```

---

### Post by trekbike on 2012-09-18
Thank you!  See below...


df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        51G  3.8G   45G   8% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           1.6G  976K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  152K  3.9G   1% /run/shm

mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/server/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=server)

cat /etc/fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6dc79bd0-5607-4edb-8d62-a371f9bef2c2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f5e56201-9bd0-4a96-ae8d-6fc6c5e04eb1 none            swap    sw              0       0

---

### Post by redmk2 on 2012-09-19
> **trekbike said:**
> Thank you!  See below...
df -h
```
Filesystem      Size  Used Avail Use% Mounted on
[COLOR="Red"]/dev/sda1        51G  3.8G   45G   8% /[/COLOR]
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           1.6G  976K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  152K  3.9G   1% /run/shm
```

mount```

[COLOR="Red"]/dev/sda1 on / type ext4 (rw,errors=remount-ro)[/COLOR]
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
[COLOR="Red"]gvfs-fuse-daemon on /home/server/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=server)[/COLOR]
```

cat /etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
[COLOR="Red"]# / was on /dev/sda1 during installation
UUID=6dc79bd0-5607-4edb-8d62-a371f9bef2c2 /               ext4    errors=remount-ro 0       1[/COLOR]
# swap was on /dev/sda5 during installation
UUID=f5e56201-9bd0-4a96-ae8d-6fc6c5e04eb1 none            swap    sw              0       0
```

The items in red are the block device /dev/sda (the partition is 1) also know as UUID=6dc79bd0-5607-4edb-8d62-a371f9bef2c2.  The mount point is /.   You also appear to have shared folders at /home/server.  The shares are also from the same partition.

Is this the RAID drives that you are referring to?

Let's see what other block devices you might have.  Post output from the following commands```
sudo blkid

sudo fdisk -l
```

---

### Post by trekbike on 2012-09-19
sudo blkid:
/dev/sda1: UUID="6dc79bd0-5607-4edb-8d62-a371f9bef2c2" TYPE="ext4" 
/dev/sda5: UUID="f5e56201-9bd0-4a96-ae8d-6fc6c5e04eb1" TYPE="swap" 
/dev/sdb2: LABEL="Data" UUID="f5ccd45e-0ce9-4a2d-8e21-5cc1be9a6949" TYPE="ext4"

sudo fdisk -l:
Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009dbed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   108287999    54142976   83  Linux
/dev/sda2       108290046   125044735     8377345    5  Extended
/dev/sda5       108290048   125044735     8377344   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 4500.0 GB, 4499967049728 bytes
256 heads, 63 sectors/track, 544952 cylinders, total 8788998144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT


Thank you!!

---

### Post by trekbike on 2012-09-19
My apologies, I forgot to answer the questions posed...

The items in red are the block device /dev/sda (the partition is 1) also  know as UUID=6dc79bd0-5607-4edb-8d62-a371f9bef2c2.  The mount point is  /.   You also appear to have shared folders at /home/server.  The shares  are also from the same partition.

Is this the RAID drives that you are referring to?

The dev/sda @ 64G is the SSD I referred to at the beginning. This device is really just to contain the OS and any other installed software along the way. It may have shared folders within it but not by choice...

The 4 1.5TB SATA drives that are sitting behind the 3ware RAID controller (that I want to share) do not appear to be listed.

Thanks!

---

### Post by redmk2 on 2012-09-19
> **trekbike said:**
> My apologies, I forgot to answer the questions posed...

> The items in red are the block device /dev/sda (the partition is 1) also  know as UUID=6dc79bd0-5607-4edb-8d62-a371f9bef2c2.  The mount point is  /.   You also appear to have shared folders at /home/server.  The shares  are also from the same partition.

Is this the RAID drives that you are referring to?

The dev/sda @ 64G is the SSD I referred to at the beginning. This device is really just to contain the OS and any other installed software along the way. It may have shared folders within it but not by choice...

The 4 1.5TB SATA drives that are sitting behind the 3ware RAID controller (that I want to share) do not appear to be listed.

Thanks!
The RAID array is shown.  Using *blkid* we show the combined physical drives (block devices) as this```
/dev/sdb2: LABEL="Data" UUID="f5ccd45e-0ce9-4a2d-8e21-5cc1be9a6949" TYPE="ext4"
```...It looks like you even gave it a label (Data).

Using *fdisk *the RAID array is show as```
/dev/sdb1 1 4294967295 2147483647+ ee GPT

```..it was created using GPT so we really should be looking at it with parted```
sudo parted -l
```

The 3ware RAID controller presents the RAID array as 1 virtual block device that you can format with a file system (the partition).

All of this means to say; you do have the RAID drives and they are shown as one partition (e.g. /dev/sdb1 aka Data aka UUID="f5ccd45e-0ce9-4a2d-8e21-5cc1be9a6949") and it is formatted as EXT4 and labled as Data.

So now we need to mount the partition to the OS file system.  This will then allow you to view and share directories (folders).  I have drive formatted ext4 that I mount just like this.  I created a mount point /data and mount the partition there.  Do you have a mount point that you want too use?

Another issue you should think about is what the share is going to be used for.  Are you creating shares for you to use from several machines or are you going to have multiple users using the shared data?

---

### Post by trekbike on 2012-09-19
This sounds hopeful!

Okay...

I am (of course) the principal user.

I use it from my Windows 7 laptop but logged into the laptop under a different username than what I log onto Ubuntu with.

Additionally, I use it to back-up my work laptop - also Windows 7 and a different log-on altogether.

I have two additional network-attached machines:

Audiotron - old device you may have heard of that plugs into the router and simply "looks" through the network for shared folders and the music files that may be present so it can play them through my stereo.

Boxee Box - A newer device that works similarly to the Audiotron but can play video as well

So, some degree of anonymity (lack of log-in) may be needed in how the RAID volume is mounted.

Hope this helps!!

Thanks!!!

---

### Post by redmk2 on 2012-09-19
> **trekbike said:**
> This sounds hopeful!

Okay...

I am (of course) the principal user.

I use it from my Windows 7 laptop but logged into the laptop under a different username than what I log onto Ubuntu with.

Additionally, I use it to back-up my work laptop - also Windows 7 and a different log-on altogether.

I have two additional network-attached machines:

Audiotron - old device you may have heard of that plugs into the router and simply "looks" through the network for shared folders and the music files that may be present so it can play them through my stereo.

Boxee Box - A newer device that works similarly to the Audiotron but can play video as well

So, some degree of anonymity (lack of log-in) may be needed in how the RAID volume is mounted.

Hope this helps!!

Thanks!!!

I'm assuming you are the only human using all of these devices.  This means we really don't have any need for permissions restraints.  The various users will have to be accommodated though.

First we need to mount the partition (/dev/sdb1).  In order to mount it we need a place to mount it to.  Linux will mount the partition to any directory you tell it too so.  The one caveat is that it will obscure any data that is in that directory while you have a partition mounted, so you don't want to mount the partition to a directory with existing data in it.

Do you want to do as much as you can using the GUI interface?  Or do you want to do this from the terminal CLI?  Let me know so we can proceed.

After we have successfully mounted the partition then we can create directory we can put the data in and share it.  We are close now.  :-)

---

### Post by trekbike on 2012-09-19
Your assumption is correct. I am the only human. I suppose the way I wrote that I just wanted to make sure that the logon information was known to be different. One thing, if I have visitors who have physical access (to a connected router or switch) or I give them my wireless keys, I'm hoping they will have access to the shares (guessing they will).

I would indeed like to use the GUI if possible. I don't mind using CLI but the beauty of Ubuntu is that almost all of it can be done through the GUI. These are one-time (setup) things so I don't mind.

When you say "you don't want to mount the partition to a directory with existing data in it..." this tells me something important.

Currently, the "data" drive which is the entire RAID has the following folders:
"Closed"
"Lost and Found" - I think
"Open"

The Lost and Found was there by default.
I added the "open" and "closed" directories such that the "closed" directory would have sub-folders and any items I did not want in the share.  Alternatively the "open" directory is to contain the shared folders... This looks like our mount point.  It is occupied with the shared folders now so when you give me the next thing to do, I'll need a day or two to move the data off so that "open" is vacant... That is if I am reading you right.

Thanks!

---

### Post by redmk2 on 2012-09-19
> **trekbike said:**
> Your assumption is correct. I am the only human. I suppose the way I wrote that I just wanted to make sure that the logon information was known to be different. One thing, if I have visitors who have physical access (to a connected router or switch) or I give them my wireless keys, I'm hoping they will have access to the shares (guessing they will).

I would indeed like to use the GUI if possible. I don't mind using CLI but the beauty of Ubuntu is that almost all of it can be done through the GUI. These are one-time (setup) things so I don't mind.

When you say "you don't want to mount the partition to a directory with existing data in it..." this tells me something important.

Currently, the "data" drive which is the entire RAID has the following folders:
"Closed"
"Lost and Found" - I think
"Open"

The Lost and Found was there by default.
I added the "open" and "closed" directories such that the "closed" directory would have sub-folders and any items I did not want in the share.  Alternatively the "open" directory is to contain the shared folders... This looks like our mount point.  It is occupied with the shared folders now so when you give me the next thing to do, I'll need a day or two to move the data off so that "open" is vacant... That is if I am reading you right.

Thanks!

Nope.  The mount point is a directory on the /dev/sda1 partition (the SSD).  Do not move any data you have on the "Data" partition.  How did you make the directories 'open" and "closed"

Is the partition 'Data" mounted somewhere?  What is the path to the directory "open" (i.e /media/data/open -- or some such)?

[COLOR="Blue"]Edit:  I'm going to answer the other questions you had below.[/COLOR]

If you are the only human then I suppose that it really doesn't matter if we restrict any of your accounts from being able to read or write data to the partition, but, if you are going to allow others to do that you are taking an unnecessary risk.  You can't be sure that they have not picked up some sort of malware the would be transferred to your machine.  You have to be responsible for you, but I don't see any reason you would want to be responsible for others.  Besides its fairly easy to restrict them to read only access.

We can use the GUI to do some of the work, but as you say the details are best left to the CLI.

---

### Post by trekbike on 2012-09-19
I understand that I don't need to start off-loading - a good thing!

I'm not terribly worried about the others that I would be giving access to... My sister, my two sons.  Shouldn't be a big deal but I'll go along with you.

I believe the sequence of events from creation of the RAID was:

"Data" was created within the BIOS of 3ware. This was the name it was given from the beginning when it was formatted in Windows 7 as NTFS....  When I installed Ubuntu onto the SSD I was pleasantly surprised to see "Data" show up (as an external drive).  Then off-loaded everything and reformatted as EXT4 and moved the contents back.  I don't recall mounting "Data" or any of the initial content folders...  To create the "open" and "closed" folders it was a simple right-click and there you go.

Okay... Ready for the step-by-step!!

Thanks!!

---

### Post by redmk2 on 2012-09-19
> **trekbike said:**
> I understand that I don't need to start off-loading - a good thing!

I'm not terribly worried about the others that I would be giving access to... My sister, my two sons.  Shouldn't be a big deal but I'll go along with you.

I believe the sequence of events from creation of the RAID was:

"Data" was created within the BIOS of 3ware. This was the name it was given from the beginning when it was formatted in Windows 7 as NTFS....  When I installed Ubuntu onto the SSD I was pleasantly surprised to see "Data" show up (as an external drive).  Then off-loaded everything and reformatted as EXT4 and moved the contents back.  I don't recall mounting "Data" or any of the initial content folders...  To create the "open" and "closed" folders it was a simple right-click and there you go.

Okay... Ready for the step-by-step!!

Thanks!!

:-)  By path I mean; how is the partition mounted in the Ubuntu file system?  You can't *right-click and there you go" * unless the Data partition is mounted.

I ask because we need to make this consistently mounted at boot up or you will have some of the problems you mentioned in your first post.  Before we really start altering things I need to know what we really have.

I assume you are using Gnome of some sort for the desktop.  When you open Nautilus you have a left panel that should show to objects (Home Folder and File System).  If you click on the "File System" you should see all the directories.  Some where in there the "Data" partition is mounted.  Usually if it is auto-mounted it will be at /media.  Click on media and see what is in that folder.  The CLI way of asking this question is much more simple.  It is:  What is the output of this```
ls -l /media
```

---

### Post by trekbike on 2012-09-20
Certainly one the smaller outputs....

total 0

---

### Post by redmk2 on 2012-09-20
> **trekbike said:**
> Certainly one the smaller outputs....

total 0hmmmmmm....

So when you are looking at the directories *"Closed", "lost+found" and "Open"*, what directory are you in?

---

### Post by trekbike on 2012-09-20
When I see those as directories, I am looking at the "Data" drive.  Is that what you were looking for?

---

### Post by redmk2 on 2012-09-20
> **trekbike said:**
> When I see those as directories, I am looking at the "Data" drive.  Is that what you were looking for?

No.  When you see those directories your user is moved to a "current working directory.  And example of this would be if I asked you what directory would you be in to see the directory named dir1 that is located at: /home/data/dir1.  You would need to be at /home/data to "see dir1.

So what directory would you be in to see "Closed", "lost+found" and "Open"

---

### Post by trekbike on 2012-09-20
The best I can do is give you the sequence of events and tell you what the system is telling me...

Logging onto to Ubuntu, I click the "Home" icon on the left-hand border. It brings up the home directory...  At the very top of the left side of the folder, under Devices, is the "Data" drive. When I point at "Data" the system says "Mount and open Data."   When I click "Data," it opens and displays the three folders: "Closed" "lost+found" and "Open." 

Any better?

---

### Post by redmk2 on 2012-09-20
> **trekbike said:**
> The best I can do is give you the sequence of events and tell you what the system is telling me...

Logging onto to Ubuntu, I click the "Home" icon on the left-hand border. It brings up the home directory...  At the very top of the left side of the folder, under Devices, is the "Data" drive. When I point at "Data" the system says "Mount and open Data."   When I click "Data," it opens and displays the three folders: "Closed" "lost+found" and "Open." 

Any better?

Ahhh.  So you are mounting it and then viewing the contents.  To me that says it is not mounted until you want to use the data.  I would like to know where it mounts, if only to make sure we don't screw something else up.

I still need to know how the drives are attached physically.  Are they mounted physically inside the computer or in a separate cage?  What cable connects the drives to the Ubuntu box?

When you "...click "Data" and can see those 3 directories, hit <ALT+L > .  You will see the location displayed in the format I suggested (i.e. /dir/dir1/dir2 or some such).  This is what I need to know.  

You should permanently mount the sdb1 partition at a specific mount point.  Then we can share whatever you want, however you want.  But first we need to set up the supporting file structure.

---

### Post by trekbike on 2012-09-20
I tried <Alt-L> with no results:

1. After being into the "Data" directory, going back to its root
2. Pointing at the "Data" directory
3. Re-starting so it was before it was mounted
    After step 3, I tried it within a terminal window (didn't think that was what you meant) but it did not generate anything either...

Did I miss something?

---

### Post by trekbike on 2012-09-20
One thing.... Without doing <Alt-L> and just hovering the mouse over "Data" after it is mounted, it displays:
/media/Data

This is probably what you were looking for... ???

---

### Post by redmk2 on 2012-09-20
> **trekbike said:**
> One thing.... Without doing <Alt-L> and just hovering the mouse over "Data" after it is mounted, it displays:
/media/Data

This is probably what you were looking for... ???

Yes!  I thought so, but didn't want to guess.  The media directory is where Ubuntu mounts removable media (floppies, CD's, USB sticks, etc).  We should create our own mount point.

I still need to know how the drives are physically attached to the computer...

---

### Post by trekbike on 2012-09-20
My apologies...  

The 64GB SSD drive is the only one that is "attached" as a SATA drive.

The four 1.5TB drives are physically connected to the 3ware 9650SE 4LPML RAID controller.  This "card" is plugged into a PCI Express slot somewhat like the video card except that it uses 4 "paths" as opposed to the video card's 16 "paths."

This has to be why it is being treated as an "external" drive.  I am open to creating whatever we need so let me know what you feel would be best such that the mounting occurs automatically at boot-up and the shares  will be available..

Thanks!

---

### Post by redmk2 on 2012-09-20
> **trekbike said:**
> My apologies...  

The 64GB SSD drive is the only one that is "attached" as a SATA drive.

The four 1.5TB drives are physically connected to the 3ware 9650SE 4LPML RAID controller.  This "card" is plugged into a PCI Express slot somewhat like the video card except that it uses 4 "paths" as opposed to the video card's 16 "paths."

This has to be why it is being treated as an "external" drive.  I am open to creating whatever we need so let me know what you feel would be best such that the mounting occurs automatically at boot-up and the shares  will be available..

Thanks!

SATA and PCI are bus types.  We can talk about what that means later if you wish.  ;-)

I'm going to assume that you have the drives mounted in a separate housing but that you want the partition mounted permanently.  When we do this the partition will be mounted upon boot up.

The first step is:

Create the mount point.  This directory can be any name.  I would create a directory in / named *data*.  Let's do this using the CLI as we have more control.  To make the directory do this```
mkdir /data
```...you can check your work with the GUI by finding that folder (directory) by clicking on "file system" in the left pane of the file manager.  Do you see it?  What are the permissions?

---

### Post by trekbike on 2012-09-20
So... mkdir = make directory, right?  Wouldn't I want to name the new directory something other than "Data" if that is what will be mounted to it or does it matter??

---

### Post by redmk2 on 2012-09-20
> **trekbike said:**
> So... mkdir = make directory, right?  Wouldn't I want to name the new directory something other than "Data" if that is what will be mounted to it or does it matter??
Yes, mkdir = make directory.

The name "Data" is the Label for the partition.  The name /data is the name of the mount point.  To be precise, the name  /data is can be thought of as: The directory *[COLOR="blue"]data [/COLOR]* in the root directory /.  Also Linux is case sensitive.  The name [COLOR="Purple"]Data[/COLOR] is not [COLOR="Blue"]data[/COLOR].  Best practice is to name all objects in lower case.  Also the lable (Data) won't be seen under normal conditions.  You will see the label when looking with diagnostic tools.  

This is how I see it.  Create a directory that is descriptive using as few keystrokes as possible.  Use a name that is descriptive.  Here are some of the mount points I have used in the past```

/smb

/srv

/data

/bkp
```...use a name that is descriptive but not limiting, no upper case and no spaces.  

These don't work```
/MyFavoriteTunes

/All Of My Work Data  
```

Do you have any suggestions?  Remember this is only the mount point.

---

### Post by trekbike on 2012-09-20
Let me ask you... Would it make sense to rename "Data" to "data" and then use something a little different for the mount point or does it matter?  If it doesn't, no need in complicating things...

I'll go with "dx" for the mount point.  Something I remember from a previous employer in the early days of data switching.

So, if I should rename, and I can do it in the GUI, I can probably figure that out, if it doesn't matter, let me know what's next.

Thanks!

---

### Post by redmk2 on 2012-09-20
> **trekbike said:**
> Let me ask you... Would it make sense to rename "Data" to "data" and then use something a little different for the mount point or does it matter?  If it doesn't, no need in complicating things...No it does not make any sense at this point.  Let's leave it as it is.> 
I'll go with "dx" for the mount point.  Something I remember from a previous employer in the early days of data switching.
Okay.  This will work just fine> 
So, if I should rename, and I can do it in the GUI, I can probably figure that out, if it doesn't matter, let me know what's next.
Thanks!
The name "dx" will work perfectly for this project. The first step is to make the directory that will be the mount point```
mkdir /dx
```

Once you have done that you need to see if the permissions are correct.  As I said before..."you can check your work with the GUI by finding that folder (directory) by clicking on "file system" in the left pane of the file manager. Do you see it?  What are the permissions?"

---

### Post by trekbike on 2012-09-21
Apparently I lack the permission to make the new directory...  
So, should I enter sudo passwd root....  and add it that way?

---

### Post by redmk2 on 2012-09-21
> **trekbike said:**
> Apparently I lack the permission to make the new directory...  
So, should I enter sudo passwd root....  and add it that way?

Yes you should.  The incantation is```
sudo mkdir /dx
```

Check the permissions with this ```
ls -ld /dx
```...post the results here.

---

### Post by trekbike on 2012-09-21
Ok...  Progress!

Here is the output of ls -ld /dx:

drwxr-xr-x 2 root root 4096 Sep 21 10:50 /dx

Thanks!

---

### Post by redmk2 on 2012-09-21
> **trekbike said:**
> Ok...  Progress!

Here is the output of ls -ld /dx:

drwxr-xr-x 2 root root 4096 Sep 21 10:50 /dx

Thanks!
Now you should be able to mount the partition with this command```
sudo mount /dev/sdb1 /dx
```

Try navigating to the folder /dx and see what is in it.  What are the permissions of the folders?

This is a temporary mount so don't worry about what the permissions are.  If all is well next we will add the mount to the /etc/fstab file.  This will make it auto mount at the correct location.  Then we will set up the permissions.

---

### Post by trekbike on 2012-09-21
One little problem...  The response came back:

mount: you must specify the filesystem type...

Guessing that somewhere in the string we need Ext4 ?

Thanks!

---

### Post by redmk2 on 2012-09-21
> **trekbike said:**
> One little problem...  The response came back:

mount: you must specify the filesystem type...

Guessing that somewhere in the string we need Ext4 ?

Thanks!

Then we will have to specify like this ```
sudo mount -t ext4 /sdb1 /dx
```

---

### Post by trekbike on 2012-09-21
Now it is saying that sdb1 does not exist....  

mount: special device /sdb1 does not exist.

---

### Post by redmk2 on 2012-09-21
> **trekbike said:**
> Now it is saying that sdb1 does not exist....  

mount: special device /sdb1 does not exist.

My mistake.  It should be ```
sudo mount -t ext4 /dev/sdb1 /dx
```

---

### Post by trekbike on 2012-09-21
Something else... ??

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Something I did?

---

### Post by redmk2 on 2012-09-21
> **trekbike said:**
> Something else... ??

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Something I did?

Not that you did at this time.  Possible problems from the original format.  :-(   The partition may be corrupted or it has other problems.


I want to wait until I return this afternoon as per my PM.

[COLOR="Blue"]Update: The partition has been mounted.  Between sessions we found the enumerated name /dev/sdb1 changed to /dev/sdb2.  When the OP mounted the partition using the UUID the mount worked fine.  This was added to the fstab file and the machine now auto mounts the partition.  The only thing left is to share the desired directories using Samba. [/COLOR]

---

### Post by trekbike on 2012-09-21
Sounds good!  Thanks!   Should I start a backup?

---

