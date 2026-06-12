---
title: "Replace Ubuntu/MythTV hard drive with larger drive?"
date: 2009-12-04
forum: General Help
---

### Post by horkthegreen on 2009-12-04
I just purchased a 1.5TB green SATA drive and would like to replace (not just add) the 200GB drive in my Ubuntu mythbox with the larger drive, without changing/losing anything on the drive (including mythtv recordings). 

Are there instructions anywhere for how to do this? I'm not great at linux, so need fairly detailed instructions. 

I have an Ubuntu Live CD (or a Live USB flash drive), and here are the contents of my fstab file before I've done anything:


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=939083d5-be90-49bc-9fc9-634658c09b71 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/hda5
UUID=73298705-e48d-4632-a43a-ba2246f4c86c none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```


Can someone please walk me through this? Thanks!

---

### Post by horkthegreen on 2009-12-04
BUMP

Help?

---

### Post by jonny on 2009-12-05
> **horkthegreen said:**
> Are there instructions anywhere for how to do this? I'm not great at linux, so need fairly detailed instructions.
This is major system surgery, and if, as you say, you're not terribly confident with Linux, I'd recommend that you add the drive instead of replacing your original.  If your PC is short of physical space, perhaps you could put the new drive in an enclosure and use it as an external USB drive.

If you do want to go ahead, the process is broadly as follows:

[LIST]
[*]Connect the new drive to your PC at the same time as the old
[*]Boot from a live CD or USB drive (this is important, as you don't want to clone a moving target)
[*]Partition the new drive
[*]Synchronise the old and new drives, making sure that you retain all file ownership, permissions, symbolic links.  The command line tool rsync is my preferred way of doing this, and you'll need to run it with root permissions or some files will be missing
[*]edit /etc/fstab and /boot/grub/menu.lst (assuming you're using Jaunty or earlier - there's an equivalent for Karmic but I'm not sure what it is) on the new drive to make sure that the correct partitions are loaded
[*]Remove the old drive and reboot into the live CD environment
[*]chroot into your new system and install the GRUB bootloader
[/LIST]

You can find information for all these steps with a little googling, but they're not for the faint hearted!

---

### Post by zaphod777 on 2009-12-05
> **jonny said:**
> This is major system surgery, and if, as you say, you're not terribly confident with Linux, I'd recommend that you add the drive instead of replacing your original.  If your PC is short of physical space, perhaps you could put the new drive in an enclosure and use it as an external USB drive.

If you do want to go ahead, the process is broadly as follows:

[LIST]
[*]Connect the new drive to your PC at the same time as the old
[*]Boot from a live CD or USB drive (this is important, as you don't want to clone a moving target)
[*]Partition the new drive
[*]Synchronise the old and new drives, making sure that you retain all file ownership, permissions, symbolic links.  The command line tool rsync is my preferred way of doing this, and you'll need to run it with root permissions or some files will be missing
[*]edit /etc/fstab and /boot/grub/menu.lst (assuming you're using Jaunty or earlier - there's an equivalent for Karmic but I'm not sure what it is) on the new drive to make sure that the correct partitions are loaded
[*]Remove the old drive and reboot into the live CD environment
[*]chroot into your new system and install the GRUB bootloader
[/LIST]

You can find information for all these steps with a little googling, but they're not for the faint hearted!

Not major surgery at all actually it is pretty dang easy.

use a clonzilla boot cd to backup an image to an external HDD.

[http://clonezilla.org/](http://clonezilla.org/)

then insert your new HDD and boot from the CD and restore to the new HDD.

You might need to use a live CD and GPARTED afterwards to expand your Linux partition to use the rest of the disk.

---

### Post by horkthegreen on 2009-12-05
Zaphod777 - Thanks! I was just about to ask about Clonezilla. 

After I use Clonezilla, to I need to do anything with the disk IDs? My reading seems to indicate I might need to edit a couple of files to change the ids?

---

### Post by Gillingham on 2009-12-05
You will need to find the uuid of the new drive.  I've just done a quick check, and to find the UUID you can use the command

```
ls -l /dev/disk/by-uuid
```

I haven't checked that this works from a live CD, but would imagine it will.

By the way looking at the fstab file you posted you might want to look at partitioning your new drive.  Say one partition for the root filesystem, one for your home directory and one for your mythtv files. 

There are ample instructions for partitioning a drive to help you.  In terms of moving your home directory I used this guide...[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")

---

### Post by horkthegreen on 2009-12-05
What's the rationale for partitioning like that? I mainly use this computer as my mythtv box... I don't do a lot in my home directory. Is it to make a transition like this easier in the future?

Your link didn't work for me. Can you check it?

Can anyone list the files I would need to update with the new disk ID?

Thanks!

Bill

---

### Post by zaphod777 on 2009-12-05
When I upgraded my HDD on 9.04 I didn't have to do anything with the UID or fstab file it just worked. I did have to expand the partition using GPARTED after though. 

The only problem I had was at the time EXT4 was new so I had to download the latest beta of clonezilla to work with ext4 but now it should not be a problem.

---

### Post by zaphod777 on 2009-12-05
As far as repartitioning goes the benefit of having your home directory on a separate partition is if you ever have to completely reinstall then you don't lose the data in your home directory. However since you have a backup just save the backup image and you are set.

When it comes to IT (professionally and personally) i like to live by the motto K.I.S.S. (Keep it Simple Stupid!) over complicating things tends to make more problems than its worth. 

If this was a fresh rebuild then I would think about repartitioning but at this point I think it is more trouble than it is worth since you will have a good backup image to roll back too.

I am sure it is more of a pain to rebuild from scratch than re-record your shows at a later date.

---

### Post by Gillingham on 2009-12-06
As Zaphod said there is a better security and protection of settings if you have to reinstall, or if one of the partitions gets corrupted, basically anytime you need to reformat a partition.  Unlike him I would say now is the time to consider it, once you have the new drive installed and before you change the size of the existing partition.



Sorry for the broken link I mis-used the link button and got two http:// in the address.

---

### Post by horkthegreen on 2009-12-22
I've decided to use Clonezilla, but I don't have enough external backup space to backup the current drive to an image. 

If I put the new drive in, use clonezilla to duplicate the old to the new, then remove the old drive, what do I need to watch out for?

---

### Post by zaphod777 on 2009-12-22
It work s great just choose local disk to local disk. Be carfull choosing the source and destination you will need to expand the
 partition with gparted after using a live CD.

I have done this many times on laptops using a USB HDD case and cloning the one inside the laptop to the external one and then swaping the HDD and then resizing the partition using gparted.

It works great with ubuntu and Windows.

---

### Post by horkthegreen on 2009-12-22
Okay, I used Clonezilla.  I still need to boot directly in and see if it worked. However...

I booted an Ubuntu 9.10 live CD and fired up gparted to look at resizing the ext3 partition. It's not intuitive to me how I do this. 

Here's my partition table as per gparted:

/dev/sda1 ext 184.88GB total 96.54GB used 88.34GB unused boot
/dev/sda1 extended 1.42 GB total
    /dev/sda5 linux-swap 1.42GB total
unallocated unallocated 1.18TB total

When I look at the options to resize the ext3 partition, it doesn't give me an option to make it much larger than it already is. 

Do I need to format the unallocated space as ext3 in a new partition? Once I do that, do I merge the partitions? Am I going to need to move my swap partition, as it seems to be between the sda1 partition and the new unallocated space?

---

### Post by horkthegreen on 2009-12-22
If I understand this correctly after a little bit of RTFMing, I will need to do the following:

Turn Swapoff on the swap drive to unlock it. 

Move the swap drive to the end of the unallocated space. I may increase the size of it just in case I add some more memory to the system later. 

Once the move is complete, I should have unallocated space near my ext3 partition and I can tell it to resize into the unallocated space and use it all. 

Sound right?

---

### Post by horkthegreen on 2009-12-22
Just FYI, I was able to boot up the system fine and everything seemed to be working correctly. Now I just need to do the gparted thing. 

Here's what I'm figuring out that I need to do because my swap partition is inside an extended partition next to unallocated space, but between the unallocated space and the ext3 partition.

* Use Swapoff to turn off swap and unlock the swap and extended partition

* Resize the extended partition to take up the entire unallocated space. 

* Move the swap space from the left of the extended position to the right of the extended position. Note: I'm making my swap space bigger right now in case I add more memory.

* Resize the extened partition so the left side is to the left of the swap space. This makes it the same size as the swap, like before, and now the unallocated partition is next to the ext3 position.

* Resize the ext3 partition to take all of the unallocated space. 

* Turn swap back on.

---

### Post by egalvan on 2009-12-22
> **horkthegreen said:**
> Just FYI, I was able to boot up the system fine and everything seemed to be working correctly. Now I just need to do the gparted thing. 


* Move the swap space from the left of the extended position to the right of the extended position. Note:** I'm making my swap space bigger** right now in case I add more memory.



I'm probably too late, but here goes.

MAKE A NOTE OF THE ORIGINAL SWAP UUID BEFORE YOU MAKE ANY CHANGES TO SWAP.

 Run
 ```
  sudo blkid -c /dev/null
```

 Include the -c /dev/null bit.
 If you run blkid without options it reads from its cache file.
 If you've run it before and any partition has changed you'll get erroneous results.


gparted at times changes the partition enough, and it gets a new UUID.

This will cause problems. Not impossible to fix, but problematic, and easily avoided.

Copy the original UUID and re-set it if it gets changed.

Note:
the file 
**/etc/initramfs-tools/conf.d/resume**
contains the UUID of swap, so all is not lost. Just get it from there if it got changed before you got a copy.

---

### Post by zaphod777 on 2009-12-22
> **horkthegreen said:**
> Just FYI, I was able to boot up the system fine and everything seemed to be working correctly. Now I just need to do the gparted thing. 

Here's what I'm figuring out that I need to do because my swap partition is inside an extended partition next to unallocated space, but between the unallocated space and the ext3 partition.

* Use Swapoff to turn off swap and unlock the swap and extended partition

* Resize the extended partition to take up the entire unallocated space. 

* Move the swap space from the left of the extended position to the right of the extended position. Note: I'm making my swap space bigger right now in case I add more memory.

* Resize the extened partition so the left side is to the left of the swap space. This makes it the same size as the swap, like before, and now the unallocated partition is next to the ext3 position.

* Resize the ext3 partition to take all of the unallocated space. 

* Turn swap back on.

since you are using a live cd no need to turn the swap on or off just move it to the far right then expand the ext3 partition. never had to do what the poster above me said but i guess it can't hurt to make the note.

---

### Post by horkthegreen on 2009-12-22
Got it done! As far as I can tell, the swap space seems to be working fine, but I wouldn't know how to tell one way or another unless something wonky started happening. I'll check the disk ID in the file the other poster mentioned. 

Strangely enough, even though I was using a live CD a lock showed up next to the extended partition and the swap space inside of it. Had to unlock it before I could resize or move it, then lock it again when done. 

Zaphod777, thanks for all your guidance during this! You are one hoopy frood who really knows where his towel is!

---

### Post by zaphod777 on 2009-12-22
Good work! It's not too hard once you have done it once. It's a nice trick to have in you back pocket when someone wants to upgrade their HDD. 

For most people they would rather buy a new PC than go through the trouble.

It's surprising how fast clonezilla will clone the drive.

Glad someone got the Hitchhikers Guide to the Galaxy reference.

:-)

---

### Post by egalvan on 2009-12-23
> **zaphod777 said:**
> **since you are using a live cd no need to turn the swap on or off **just move it to the far right then expand the ext3 partition.
 never had to do what the poster above me said but i guess it can't hurt to make the note.

This thread has been solved, but others may use it for reference...

Many LiveCD distros will search for, and use, a usable swap partition on a hard drive. This includes Ubuntu.
So turning the swap partition off is usually necessary if that partition is inside an extended that needs to be changed,
or if swap needs to be worked on.

When running partition tools, check if the "lock" symbol is shown for swap.

---

### Post by horkthegreen on 2009-12-24
Strange...

My Samba shares from this machine are no longer showing up on my windows network after I did this upgrade. 

I recently also replaced a G wireless bridge with an N wireless bridge, but I'm pretty sure the Samba shares were still visible to the Windows network after that. 

My Samba shares are still defined, but no users are checked in the users tab. 

My machine has a static IP, and I've confirmed that is still configured correctly. I've also verified the workgroup is the same as the Windows network's machines' workgroup.

My machine is showing up as a Media Server on some Windows XP machines, but it isn't seeing the Samba shares in My Network Places. 

Any ideas?

---

### Post by zaphod777 on 2009-12-24
Thats strange it shouldn't make a difference. 

I haven't used Samba much maybe the HDD in Samba has a different GUID than then new one.

---

### Post by lyall on 2009-12-24
I just brought a new Seagate 1TB hard drive and I used the CD that came with it to copy all data from the old 160 GB hard drive to the new 1 TB with no problems.  Just had to select clone drive

After cloning the drive I had to resize the partition from the 160 GB to the 1 TB.

I am am IT spec and I have Partiton Magic.  I just boot to the floppy and resize the drive partition.

Gparted will do the same thing.

good luck and have fun learning

---

### Post by zaphod777 on 2009-12-24
> **lyall said:**
> I just brought a new Seagate 1TB hard drive and I used the CD that came with it to copy all data from the old 160 GB hard drive to the new 1 TB with no problems.  Just had to select clone drive

After cloning the drive I had to resize the partition from the 160 GB to the 1 TB.

I am am IT spec and I have Partiton Magic.  I just boot to the floppy and resize the drive partition.

Gparted will do the same thing.

good luck and have fun learning

HE has already done that but can't see his samba shares from other pc's on the network since the change.

---

### Post by zaphod777 on 2009-12-24
> **horkthegreen said:**
> Strange...

My Samba shares from this machine are no longer showing up on my windows network after I did this upgrade. 

I recently also replaced a G wireless bridge with an N wireless bridge, but I'm pretty sure the Samba shares were still visible to the Windows network after that. 

My Samba shares are still defined, but no users are checked in the users tab. 

My machine has a static IP, and I've confirmed that is still configured correctly. I've also verified the workgroup is the same as the Windows network's machines' workgroup.

My machine is showing up as a Media Server on some Windows XP machines, but it isn't seeing the Samba shares in My Network Places. 

Any ideas?

Did your IP scheme happen to change after the network upgrade?

I found this:
> File Sharing (Advanced)
We started with the base of Samba file-sharing. The above-mentioned items should be enough to get you started. Next we will add details that you might or might not need.

If you have more than one network card
If you have more than one network card (or interface) then you have to define where you want Samba to run. In smb.conf under the [global] section, add:


interfaces = 127.0.0.1, 192.168.0.31/24
bind interfaces only = yes
The first address (127.0.0.1), is a loopback network connection (it's your own machine). The second address (192.168.0.31), is the address of the card you want Samba to run on, the second number (24) is the subnet default for a CLASS-C network. It may vary depending on your network.

With "bind interfaces only" you limit which interfaces on a machine will serve SMB requests.

You can limit which IP address can connect to your Samba server adding these lines:


hosts allow = 127.0.0.1, 192.168.0.31, 192.168.0.32
hosts deny = 0.0.0.0/0
The loopback address must be present in the first line. The second line deny access from all IP address not in the first line.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Samba uses ports 

UDP ports 137 and 138
TCP ports 139 and 445

can you test from another pc using a port scanner to see if the ports are accessible?

What happens if you try and access them by IP?

Also here is a good troubleshooting guide for Samba
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting)

---

### Post by horkthegreen on 2009-12-25
I'm not sure how it happened, but Samba seemed to be disabled. It might have happened after I ran the mythtv backend configution the other day. 

I ran it again today and noticed that it said access via Samba was turned off. I told it to turn it on, and it looked like it re-installed Samba. 

After that, my shares showed up again. iTunes from the Windows box upstairs seems to be able to see the songs stored on my mythbox, and now my son can sync his new iPod nano to all the indie music he's downloaded.

Thanks again!

---

### Post by crtlbreak on 2009-12-27
Hi horkthegreen
The best and simplest (and possibly also the most dangerous tool) is dd - i think it was named data duplicate (but has also been nicknamed "data destroyer" for a reason").

first after an 
```
fdisk -l
```
find out which one is your mythtv source (that will be the if) and then the 1,5TB destination (of) will fit in to the below.

then

```
dd if=/dev/source of=/dev/target bs=4096 conv=notrunc,noerror
```

or more specifically in your case

```
dd if=/dev/mythtv of=/dev/1point5tb bs=4096 conv=notrunc,noerror
```

this will do a byte by byte duplicate from source (if) to destination (of).

a little note - [COLOR="Red"]DO NOT mix up[/COLOR] the if (input function) with of (output function) [COLOR="Magenta"][B]or you will overwrite the whole mythtv drive with blank data from the new 1,5TB drive.
[/B][/COLOR]

You might want to also carefully go through the following article

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/")

it is a blow-by-blow of how to duplicate partitions, and make restore images etc

hope this info helps?

---

### Post by zaphod777 on 2009-12-27
> **crtlbreak said:**
> Hi horkthegreen
The best and simplest (and possibly also the most dangerous tool) is dd - i think it was named data duplicate (but has also been nicknamed "data destroyer" for a reason").

first after an 
```
fdisk -l
```
find out which one is your mythtv source (that will be the if) and then the 1,5TB destination (of) will fit in to the below.

then

```
dd if=/dev/source of=/dev/target bs=4096 conv=notrunc,noerror
```

or more specifically in your case

```
dd if=/dev/mythtv of=/dev/1point5tb bs=4096 conv=notrunc,noerror
```

this will do a byte by byte duplicate from source (if) to destination (of).

a little note - [COLOR="Red"]DO NOT mix up[/COLOR] the if (input function) with of (output function) [COLOR="Magenta"][B]or you will overwrite the whole mythtv drive with blank data from the new 1,5TB drive.
[/B][/COLOR]

You might want to also carefully go through the following article

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/")

it is a blow-by-blow of how to duplicate partitions, and make restore images etc

hope this info helps?

Your a bit late to the party everything is done and working.

So long and thanks for all of the fish...

---

### Post by crtlbreak on 2009-12-27
> **zaphod777 said:**
> Your a bit late to the party everything is done and working.

So long and thanks for all of the fish...

zaphod777
You might have missed who I addressed my message to??

---

### Post by zaphod777 on 2009-12-27
The original poster has already cloned the HDD to the new one expanded the partition and fixed his samba issue. 

So I was a bit confused on why you would add in another solution when it is already working on the new HDD.

Sorry if I came off a bit rude but lately I have been seeing a lot of people posting their 2 cents in after an issue has already been resolved or not reading through the thread before posting.

---

