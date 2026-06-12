---
title: "Headless? Keep me out of my loft!"
date: 2011-01-31
forum: General Help
---

### Post by Halkus on 2011-01-31
Yesterday my storage array died. So I decided it was a good opportunity to dump Windows Home Server. I installed Ubuntu 10.4. I was going to use the server version, but I saw it had no GUI, and I'd like to have a GUI for remote connection.

I've been having a lot of problems so far with having to climb back into my loft to click on something or input a password. The latest one is if it can't find a drive (I have a couple of backup drives and one has a loose SATA cable). 

I've got it setup now to log automatically into an admin account, and to allow connections with a password without clicking on screen.

Is there some kind of global setting, or something I can do which will force Ubuntu to always behave as if it's a headless server, and to get to the desktop even if there are errors/problems? I really don't enjoy climbing up into my loft continually!

---

### Post by Halkus on 2011-01-31
And since I posted this message I've been up the loft again.

And now I can't connect again, so I'm going to have to go up AGAIN. :(

---

### Post by Halkus on 2011-01-31
The problem seems to stem from me telling Ubuntu to mount a pair of NTFS formatted disks automatically when it boots.

It had a problem because one of the SATA cables I used had a clip, which was very prone to coming out of the motherboard header. It did that twice causing me to open up the loft, climb up and sort it.

Now that I've replaced the cable, Ubuntu needs me to press S when booting because it can't find a drive I've told it to mount every boot - I guess because I changed the port I put the SATA cable in.

I think then what I'm looking for in the short term is a way for Ubuntu to boot, regardless if it encounters an error mounting a drive. And for the long term some way of prevening any error type like this occurring.

---

### Post by Darkness Des on 2011-01-31
Try running the command
```

gksudo gedit /etc/fstab

```
and removing the two entries for the drives.

---

### Post by djeikyb on 2011-01-31
I don't have any ideas for the short term yet. Long term, make sure you're using the new uuid reference in fstab instead of the old sdc4 or hdb9 way:
```
UUID=AAFD-01C2     /media/ipod     vfat     user,noauto,relatime 0  0
```

EDIT: I'm not sure what your experience level is. If you need more info, I can give a longer explanation : )

---

### Post by Halkus on 2011-02-01
Des, that's exactly the answer I was looking for. I can now edit the table - and remove the entry that's causing the problem.

Djeikyb, my experience level with Ubuntu is near zero. However I think I understand where you're going with that. You're saying there's at least two different ways to edit the config file that lists what Ubuntu should mount at boot, and that the way you are suggesting, a newer way, is more robust than the other way. However I cannot understand the sytnax you've used without doing a bit of research into it. I'm happy to work it out though, don't feel obliged to explain it all.

You've essentially told me what the solution is, and now I know what I need to work out.. I should be able to manage. At least for the mean time Des has given me a solution that should allow a reboot without me having to go up into the loft!

---

### Post by Halkus on 2011-02-01
However, before I edit the table down I thought I'd try two things. I tried a GUI for managing fstab, which I don't think I like as it doesn't seem to show everything - it doesn't seem to list (or at least I don't comrehend it enough to see) the problem mounting.  In all honesty I prefer a config file over a GUI. It's nice to have the GUI at times though, but I think I'm perfectly happy with the config file.

So I'm now looking at fstab and trying to piece together not everything in it at this stage, but what the problems are, what the devices are etc.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sdb1	/	ext4	defaults,errors=remount-ro	0	0
/dev/sdc1	/media/Backup_1	ntfs	defaults,nls=utf8,umask=0222	0	0
/dev/sdd1	/media/Backup_2	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077	0	0
/dev/sdb1	/media/New_Volume	ntfs	defaults,nls=utf8,umask=0222	0	0
/dev/sda1	/	ext4	errors=remount-ro	0	1
/dev/sda5	none	swap	sw	0	0

```

I don't know where Ubuntu lists what hardware is attached. I'm not even sure if there is a rough equivalent of Windows device manager. Because of that I can only deduce what the devices are rather than be sure.

As I understand the fstab table, the devices are listed and Linux gives them all a location. I do not understand where it gets the sdx? from. I'm guessing perhaps static device, character, number. Perhaps controllers get characters and then the number of the device from that controller is appended?

In any case it would seem that it might be a problem if there are several listings for the same item. 

The motherboard has 6 SATA ports - I believe the SB750 chipset has 4 standard, and 2 on a different controller for a total of 6. There's also a 3805 RAID card with a single array on it. The array is actually unformatted, and has just been rebuilt to RAID6. It was 8 drives in RAID5, until two drives decided to fail at the same time... meaning it changed to 6 drives of usless data. I'm waiting on replacement drives, so I've not put any data back on yet. So there's the one 4TB array connected to the 3805, and there are 2 2TB drives (which are the (thankfully recent) backups of the array). There's also the boot drive, a 150GB raptor.

sdc1 - 2GB Seagate backup drive 1
sdd1 - 2GB Seagate backup drive 2
sda5 - Swap file, likely based on the main drive?
sdb1 is listed twice. Once is the spurious New_Volume which doesn't exist and prevents a boot to desktop. I'll be deleting that line.
The other sdb1 I don't understand. Since there's no /media/name then I assume it isn't mounted? 
The same goes for sda1... 
However one of those might be the RAID array, and the other surely has to be the main drive with the filesystem on it?

Edit : And a light just came on in my head. I now nearly understand Djeikyb, he's saying there's a better way to reference the device rather than sdc1 he has UUID. I should be able to fathom that out and why it's better. :)

Edit edit : And I now appear to have enough scope of things to be able to find the solutions, I've found what appears to be a very good explanation of UUID, and I should be able to get a complete understanding of fstab in the same manner.

Thanks folks :)

---

### Post by djeikyb on 2011-02-01
Apologies, I should have been a bit more thorough. Looks like you managed to work through it though! But yes, as of some kernel update we can reference disks by a UUID instead of absolute device path (ie, /dev/sda1). You should link to the UUID explanation you found, might be good reading for others.

For a use case, consider my iPod. It's a hot swappable device, and has a chance of getting mapped to a different device path each time it's plugged in. So I changed this line in my /etc/fstab:
```
/dev/sde1     /media/ipod     vfat     user,noauto,relatime 0  0
```
to
```
UUID=AAFD-01C2     /media/ipod     vfat     user,noauto,relatime 0  0
```
The question then is, how the heck did I know its UUID?
```
jake@daedalus:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2011-01-08 22:48 045c5eba-b658-4190-91e4-a800651bdd61 -> ../../sda1
lrwxrwxrwx 1 root root 10 2011-01-08 22:48 25cc9b74-c9af-4ecc-a4e7-ef4b8863bd32 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2011-01-08 22:48 2c49a6e2-b6f3-4ce8-8e85-ca0df0ce086f -> ../../sda6
lrwxrwxrwx 1 root root 10 2011-01-08 22:48 51bb8f67-b8d1-4603-b9bc-56af84f2dde1 -> ../../sda5
lrwxrwxrwx 1 root root 10 2011-01-08 22:48 E488E92988E8FB46 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2011-01-08 22:48 ec17259e-f872-457d-8321-5a2af8bf684f -> ../../sdd1
```
I don't have the ipod plugged in just now, but you see how to translate the device path to UUID. UUID's are created for a partition when the partition is formatted.

---

### Post by Halkus on 2011-02-02
I'll find out where I found the link and link it back in this post with an edit. [Here.]("http://linux.byexamples.com/archives/321/fstab-with-uuid/")

Again thanks for the reply. The only piece of the puzzle I'm not sure on now is that although I know what the UUID is, and the device path... but how do I find out what the devices actually are. For example is it an OCZ Vertex2 with 100GB of space, or is it an ADAPTEC SCSI array with 6TB of space?

---

### Post by nothingspecial on 2011-02-02
The gui way would be to have a look at gparted

or type

```
sudo fdisk -l
```

Thats a little L by the way not a number one.

That will list your drives (partitions actually) by device and space.

Another way of listing partitions in fstab is by label like so
```

LABEL=backup /media/backup ext3 defaults 0 0 
LABEL=music  /home/ns/music/flac ext3 defaults 0 0
LABEL=lacie  /home/ns/music/mp3  ext4 defaults 0 0
```

It can make fstab a little easier to read. You can label drives with gparted or various cli tools, see here

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Aslong as you don`t relabel the drive it is just as robust as by UUID

---

### Post by Halkus on 2011-02-03
I'm starting to grasp things now.

"Storage Device - Letter" is the way names are allocated, and the number indicates the partition.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sdb1	/	ext4	defaults,errors=remount-ro	0	0
/dev/sdc1	/media/Backup_1	ntfs	defaults,nls=utf8,umask=0222	0	0
/dev/sdd1	/media/Backup_2	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077	0	0
/dev/sda1	/	ext4	errors=remount-ro	0	1
/dev/sda5	none	swap	sw	0	0
```

```

Disk /dev/sda: 3998.6 GB, 3998614552576 bytes
255 heads, 63 sectors/track, 486137 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001ddc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       17496   140530688   83  Linux
/dev/sdb2           17496       18242     5990401    5  Extended
/dev/sdb5           17496       18242     5990400   82  Linux swap / Solaris

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xae8c6dfd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001    7  HPFS/NTFS

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2dc28b30

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001    7  HPFS/NTFS
```

So I now understand that Ubuntu assigns a letter to each storage device. Storage Device A - SDA, etc.

A is the Adaptec array, and as I type this UPS have just delivered the two advanced RMA drives from WD. So that'll be getting rebuild shortly.

B is the boot drive. Which has been split into the normal drive, and also (gparted showed this more clearly) a swap drive which is somehow wrapped in an extended partition.

C and D are my backup drives for the array that's going to get rebuilt. There is nothing remarkable about them. 

However, if I look at the way things are mounted...

A1 - My filesystem is mounted first, that makes perfect sense. C1 and D1 are mounted - although I must have used different methods to mount em, as they have different mounting options (that's for me to work out later).

A1 and A5 make no sense to me. From fstab I would expect A5 to be the swap disk, but it isn't. A5 would be on the Adaptec array not the Raptor boot disk.

Likewise /dev/sda1	/	ext4	errors=remount-ro	0	1 doesn't make sense either... the adaptec array hasn't got the file system.

Is possible that because I've booted up at least once without the Adaptec card connected the fstab has gotten a little confused?

Should I just delete the last two lines? Am I correct in thinking that using UUIDs would stop this happening in future?

Edit : I'm also unsure of where to find a reference to all the different options for mounting. I'm sure there's some of them that would be best to use or avoid.

Edit : Edit: I've gone and cut it right down. I suspect the way the storage drives were mounted was why Samba wasn't working on them, I'll know more about that when I try to use Samba on the proper storage array once the rebuild is finished.

So I've cut it right back to 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sdb1	/	ext4	defaults,errors=remount-ro	0	0
/dev/sdb5	none	swap	sw	0	0
``` Next I think I should be using UUIDs.

I still can't find a reference listing what the options are for mounting :/

---

### Post by djeikyb on 2011-02-03
Minor correction, sd stands for "scsi device", which applies to all devices that understand (at least some) scsi commands (except tape drives, which get their own special acronym: st "scsi tape"). IDE hard disks will be prefixed with hd instead.

You can get quite a bit of information from the man pages. Try these commands:
```
man fstab
man mount.ext4
man mount.smbfs
man mount.ntfs
```

I think what you're doing is good. Remove (or comment out) all the fstab entries you don't actually need. Just be sure and keep proc ; D  Then you can experiment adding mounts back in one by one, ensuring you have the ride options.

Also, you talk about A1-A5, but your fdisk -l command shows no partitions for sda (following what you said, because it's the array). I think you mean sdb?

---

### Post by Halkus on 2011-02-03
Ah, I had no idea there were built in manuals. I'll use those.

For some reason all drives on my server are showing as SCSI devices. Slightly unusual as it's normally only Nvidia or JMicron controllers that do that in Windows. But it's not important.

After editing my fstab file I seem to have fixed the issues that I had, I've confirmed my swap file still exists and the system is able to use it - although unlike Windows it doesn't seem to want to page everything out all the time. In fact Ubuntu seems to have a totally different approach to memory usage than Windows. Windows likes to use as much as it can to try to cause efficiency that way.

Next for me is to read those manuals and re-work my fstab to get things perfect.

If I make a dogs breakfast of it and Ubuntu won't boot - how should I try to recover.

Again, thanks very much for the reply! I really do appreciate the help!

---

### Post by djeikyb on 2011-02-03
Oh man, words cannot express my joy when I found out linux had useful documentation built into the system. Of course, I was 15, and getting help online meant dial-up at grandma's house. /nerd

Anyway, don't take me as RTFM'ing you, if you don't understand something, me or someone else will be glad to help make sense of it. I can't say I'm too familiar with some of the options that were in your fstab (nls, gid, nosuid, uhelper..)

Anything SATA should show up as SCSIish.

If you bork your boot fiddling with fstab, use a livecd, edit fstab, reboot. Prolly a trip to the loft : /

One more edit: take a look at mount --fake.
[quote=man mount]       -f, --fake
              Causes everything to be done except for the actual system call; if it's not obvious, this ``fakes'' mounting the filesystem.  This option is
              useful in conjunction with the -v flag to determine what the mount command is trying to do. It can also be used to add entries  for  devices
              that were mounted earlier with the -n option. The -f option checks for existing record in /etc/mtab and fails when the record already exists
              (with regular non-fake mount, this check is done by kernel).[/quote]

---

### Post by Halkus on 2011-02-03
Indeed. Dial up was not the friendliest way to do things, epecially before the world wide web. I never played with Linux much until now though.

I really should either fire a DVD drive in the server or get some more USB keys. But yep, I could work it out with a live cd. That makes sense.

I don't understand the -fake option. Perhaps I will after I read the manuals... at the moment I'm repacking the drives that failed which caused this switch to Ubuntu to send back to WD, following their "We want to reject your RMA" rules :)

---

### Post by djeikyb on 2011-02-03
Haha, I at least had the www when I started. 56k + Netscape starts sounding luxurious when I hear people recounting the days of dial-up bbs and 2400 baud modems.

Livecd, liveusb, whatever.

I was thinking the --fake option might be useful with -a (mount all filesystems) to check that your fstab is basically sane. I forgot to mention -a earlier. Oops.

---

### Post by Halkus on 2011-02-03
So you're meaning if I stick the fake on and it's a completely screwy one it'll turn out an error and offer to skip rather than try to do the impossible and bomb out?

---

### Post by djeikyb on 2011-02-03
No, it looks like the fake flag is more about checking command sanity before you commit to adding lines to fstab and booting. Maybe it's of less use than I thought.

The fstab line:
```
/dev/sdc1	/media/Backup_1	ntfs	defaults,nls=utf8,umask=0222	0	0
```
using the mount command translates to:
```
mount -t ntfs /dev/sdc1 /media/Backup_1 -o defaults,nls=utf8,umask=0222
```

All this is just to quickly play with mounting without editing the fstab.

---

### Post by JKyleOKC on 2011-02-03
Your two listings are not consistent with each other, and this is undoubtedly causing you some confusion! The sda, sdb, and so on names are assigned to the devices in the order in which they are encountered during the boot process -- and it's quite possible for this order to change the next time you boot. That's the main reason that Ubuntu changed over to use UUID designations instead of the /dev/sd* notation.

Try running those two commands again without rebooting in between, and the results should be consistent. In particular, it looks as if the drive identified as sdb in the second listing is actually the same drive as the one known as sda in the fstab listing, since those are the only ones in each listing that contain a partition 5.

The conventional partition table has space for only four partition definitions, and that's why the "extended" partition was invented. It provides additional space so that you can have more than just four definitions. In Linux, any partition numbered 5 or higher is actually defined within the single extended partition, which can have the number 2, 3, or 4 (when it's created, it gets the first unused number of the four primary spaces available). Your fdisk listing shows the extended partition; it won't be listed in fstab since it's only a container for other partitions and does not itself contain a file system.

In the fstab listing, the column headed "mount point" can tell you a lot about the device contents. If it's "/" by itself, that's the root of the entire filesystem tree and is where almost all of your Linux installation resides. I see that you have two devices listed for the same mount point -- which is a definite error. You can issue the command "mount" to see which device is actually being used, and correct fstab accordingly. This will give you a listing that looks a lot like fstab, but shows what is actually mounted where fstab is your instruction to the system telling it what, and where, you want things mounted.

There's a huge amount of information in these listings, and it will take you quite a bit of reading and study to comprehend it all. Meanwhile just yell for help here and some of us will chime in and try to shed some light on the situation.

---

### Post by Halkus on 2011-02-03
Well, I have corrected my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sdb1	/	ext4	defaults,errors=remount-ro	0	0
/dev/sda1	/media/New_Volume	ntfs	defaults,nls=utf8,umask=0222	0	0
/dev/sdc1	/media/New_Volume_	ntfs	defaults,nls=utf8,umask=0222	0	0
/dev/sdb5	none	swap	sw	0	0
```

And (after some Adaptec bugs) my RAID6 array has cleared, and Ubuntu has partitioned it (I used gpt instead of msdos when I googled it, remembering that above a certain size there might be problems). I now have a filesystem on it, ext4, and it's ready to mount so I can copy across data overnight.

The array is going to be shared with Samba to the other PCs in the house. I expect to put directories on it such as \movies \dave \backups \incoming and share those directories with particular access requirements etc. Samba did not do very well at all when I tried with the storage drives, but they are NTFS and they were mounted funny.

I'm thinking it should be ok to just mount the array any old way and shove the data across from the backups, and then worry about mounting it properly afterwards... I can't think why that'd be an issue.

---

### Post by JKyleOKC on 2011-02-03
That looks a lot better! Glad you've got things going.

I notice that each of your entries ends with "0  0" which tells the system to NEVER check the drives for possible corruption. If this is how you want it to work, that's fine, but problems can then blindside you. Changing that last digit from 0 to 1 can get you an automatic check every nth reboot, where n is usually 30. If you don't reboot often that may not make much difference, though...

---

### Post by Halkus on 2011-02-03
The server should only get rebooted if something goes wrong... so it won't have an effect.

I am not having any success with Samba and these NTFS drives at all. I'm going to have fun with that tomorrow. I seem to need to find a way to restart both Ubuntu and Windows (especially Windows) so that they stop using cached information. I think I have the way to restart samba on Ubuntu - sudo restart smbd

However for tonight all I need to do is start the files copying to the array. I'm thinking I just mount the array any old way and copy the files across using the GUI file explorer?

---

### Post by djeikyb on 2011-02-03
I think it's more exciting to use `rsync -rP`, but yes, a simple gui file copy will work. Also, if the copy fails midway for some reason, re-running the rsync command will pick up where it left off.

And like JKyleOKC is saying, switch to UUID in your fstab sooner than later. I know you don't reboot much, but if sdd now is picked up as sdb later, it'll be a major PITA. I had a server once that worked fine unless you rebooted with a flash drive plugged in. Stupid flash drive would get marked as sda, so fstab was insistently trying to mount its 256mB fat32 partition as the root file system. And that was when I switched to UUID.

---

### Post by Halkus on 2011-02-03
I started the copying from both drives simultaneously... sadly it seems RAID6 is as slow as I had expected and it's only going at 120MB/sec.

I intend to sort out UUIDs tomorrow. At that point I'll have the backup drives data on the array and I can unmount them, and leave them that way.

I should then have a tidy fstab, just the boot drive, swap, and RAID array.

And then it's time to get stuck into Samba!

Thanks again for all the help!

---

### Post by Halkus on 2011-02-04
```
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
UUID=936cf8a0-5c04-4016-8140-5ccabacff9d1	/	ext4	defaults,errors=remount-ro	0	0
UUID=8e5196ea-8fb3-455d-a3f5-20398bb7d94b	none	swap	sw	0	0
UUID=f4027f7a-a1d5-4321-9d83-b4d9afa5c849     /media/array     ext4     defaults 0  0
```

Array added, and I've switched to UUIDs.... and I can reboot and it works just perfectly.

I am wondering if the ```

proc	/proc	proc	nodev,noexec,nosuid	0	0
``` line is a remnant of something and should be deleted...

And now sadly I come to Samba, and Samba failing to work properly for me. But the solution there seems to be to reboot... I think I'll manage to get Samba sorted out too this evening.

---

### Post by JKyleOKC on 2011-02-04
Samba can be extremely puzzling. Part of the problem with it is that Microsoft has changed the CIFS protocol several times, and the Samba team has had to do reverse engineering to remain compatible with it. Also, Samba 4 has just made its appearance, and that may make some existing how-to documents incorrect.

When my little LAN was running a mix of Win98 and Linux machines, I had to have Samba servers installed on each of the Linux machines to make them available to the Windows boxes. I found that installing the "swat" package, which is a GUI for configuring Samba, was the simplest way to get a consistent starting point. Also, the "testparm" command became my best friend for troubleshooting the configuration files.

---

### Post by Halkus on 2011-02-04
Any ideas if the line I put in code markers above should be removed?

As for Samba I'm already using that bit of software. I just need to remember to restart the service any time I make changes.

I've already got all the shares set up... but I've hit a problem, the Windows PCs don't seem to have write access - although as far as I can tell I've set up Samba to correctly allow it.

---

### Post by nothingspecial on 2011-02-04
> **Halkus said:**
> Any ideas if the line I put in code markers above should be removed?


No, do **[COLOR="Red"]not[/COLOR]** remove /proc from fstab. It is a virtual file sytem that needs to be mounted at boot.

---

### Post by Halkus on 2011-02-04
I think that's advice worth taking :) Proc gets to stay!

Thanks!

---

### Post by nothingspecial on 2011-02-04
No problem, if you are interested read this

[http://www.linuxinsight.com/proc_filesystem.html](http://www.linuxinsight.com/proc_filesystem.html)

click the blue links for a short explanation of whats going on.

---

### Post by JKyleOKC on 2011-02-04
> **Halkus said:**
> I've hit a problem, the Windows PCs don't seem to have write access - although as far as I can tell I've set up Samba to correctly allow it.You can set Samba's shares to log in as a specific user whenever a Windows box connects to them, and could even create a special user for that purpose and make that user a member of the same group that owns your array's shared directories.

However, read up on "umask" and use it in the definitions of the Samba shares. A umask of 000 will give read-write permission to everyone and this may be what you want to do.

If you have any need for security precautions (adolescent users who may be inclined to pranks, for example) you may want to study the "group" concept of Linux. It's intended to allow you to give specific permissions to a limited set of users without opening the door to everyone.

p.s. +99 to the warning to leave the "proc" line in place. Without it your machine would not boot.

There's lots of options available. Which to use depends on what you deem most important in your case!

---

### Post by Halkus on 2011-02-04
It's quite interesting to be honest. I can see the benefits in it.

However, I'm knee deep in Samba right now :( Still can't get write access

---

### Post by nothingspecial on 2011-02-04
> **Halkus said:**
> It's quite interesting to be honest. I can see the benefits in it.

However, I'm knee deep in Samba right now :( Still can't get write access

Not my forte I`m afraid, no Windows here :tongue:

---

### Post by Halkus on 2011-02-04
> **JKyleOKC said:**
> You can set Samba's shares to log in as a specific user whenever a Windows box connects to them, and could even create a special user for that purpose and make that user a member of the same group that owns your array's shared directories.

I think that's what I've managed to achieve. I have, for example, speech-dispatcher who is really windows user Dave, and I've stored my own Windows password in Samba... I've got it set to read/write permission, and I was stunned that I just need to browse there and my Windows password seemed to do the job. However...that's when I realised I did't have write access.

> **JKyleOKC said:**
> 
However, read up on "umask" and use it in the definitions of the Samba shares. A umask of 000 will give read-write permission to everyone and this may be what you want to do.

If you have any need for security precautions (adolescent users who may be inclined to pranks, for example) you may want to study the "group" concept of Linux. It's intended to allow you to give specific permissions to a limited set of users without opening the door to everyone.

p.s. +99 to the warning to leave the "proc" line in place. Without it your machine would not boot.

There's lots of options available. Which to use depends on what you deem most important in your case!

Unmask seems to be what I need to do - I'm off to read into that!

---

### Post by Halkus on 2011-02-04
Would anyone be able to point me at something I could read on it? Google turns out masses of stuff I just cannot comprehend... 

I understand the basic principle of the permissions in Linux. 777 being full read/write/execute, but that's as far as I can get.

---

### Post by nothingspecial on 2011-02-04
> **Halkus said:**
> Would anyone be able to point me at something I could read on it? Google turns out masses of stuff I just cannot comprehend... 

I understand the basic principle of the permissions in Linux. 777 being full read/write/execute, but that's as far as I can get.

Have a look at this

[http://linuxcommand.org/lts0070.php](http://linuxcommand.org/lts0070.php)

Infact, when you have time, read the whole site. Very well explained.

---

### Post by nothingspecial on 2011-02-04
And I`m not sure if you`ve seen this

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

but it is a very well written introduction to fstab

---

### Post by Halkus on 2011-02-04
Well, that's a good explanation of the shell. That's the only part of linux I had used prior to installing Ubuntu, I have a debian slice on a Leaseweb server I use as a SOCKS proxy and seedbox.

It does go into a very good explanation of what chmod is, and how permissions work, but that's not what I'm struggling with. I'm struggling with how to get samba to grant read/write permissions as shown in the GUI (and in the text file). The clue I have is umask, but any searches I do seem to just turn out lots of people asking questions on directory and file creation permissions... most of which I cannot understand.

---

### Post by nothingspecial on 2011-02-04
AFAIK, and as I said, I don`t have windows or a mac for that matter, umask sets permissions for filesystems that do not natively support linux file permissions at the point they are mounted.

That`s what you are trying to achieve, that may help you refine your search but I think I`ll duck out now till someone who knows about samba etc pipes in.

Good luck.

---

### Post by Halkus on 2011-02-04
Aha. That might be the solution... it might need me to mount the array differently - I'm trying to use umask inside my Samba config. 

I feel like a lightbulb just went on :)

The server is rebooting, so in a few minutes I'll know if it worked.

Edit : A trip up the loft :(

---

### Post by Halkus on 2011-02-04
I think umask is a red herring.. I think it only applies to non-Linux partition filesystems. Adding ,umask=000 to the fstab for the array caused it to fail to load (and a trip up the loft). 

I'm now thinking it must be something specific to the Samba config.

---

### Post by CharlesA on 2011-02-04
Read my howto here:

[http://charlesa.net/tutorials/debian/debiansamba.php](http://charlesa.net/tutorials/debian/debiansamba.php)

---

### Post by Halkus on 2011-02-04
That's a nicely written howto. But it doesn't address the problem I have.

```
[bob_backup]
	path = /media/array/bob_backup
	writeable = yes
;	browseable = yes
	valid users = games, speech-dispatcher
```

Doesn't allow either user to create or delete a file.

---

### Post by CharlesA on 2011-02-04
It's writing to an NTFS drive, right? Try using forceuser and forcegroup to get around the permissions problem.

---

### Post by Halkus on 2011-02-04
No, it's an ext4 partition on 8 drive in RAID6.

---

### Post by CharlesA on 2011-02-04
> **Halkus said:**
> No, it's an ext4 partition on 8 drive in RAID6.

Ah. What are the permissions of the mountpoint?

Also, did you create any samba users with smbpasswd -a ?

---

### Post by Halkus on 2011-02-04
I don't know what the permissions of the mountpoint would mean.

I created the users in the GUI Samba - it gives me an unusual unix name and asks me to assign a Windows name to it, and a password. I've been using the logins for the network and they allow access as expected... but no write.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
UUID=936cf8a0-5c04-4016-8140-5ccabacff9d1	/	ext4	defaults,errors=remount-ro	0	0
UUID=8e5196ea-8fb3-455d-a3f5-20398bb7d94b	none	swap	sw	0	0
UUID=f4027f7a-a1d5-4321-9d83-b4d9afa5c849     /media/array     ext4     defaults 0  0
```

If that helps that is my fstab.

---

### Post by CharlesA on 2011-02-04
Post the output of this:

```
ls -ld /media/array
```

---

### Post by Halkus on 2011-02-04
```
drwxr-xr-x 9 root root 4096 2011-02-04 20:08 /media/array
```

---

### Post by CharlesA on 2011-02-04
You can either change the permissions, or change the owner/group of that folder.

---

### Post by Halkus on 2011-02-04
I think I've grasped it now.

I had somehow created the array and contents as read only, except by root.

I had already picked up how to start a Nautilus instance with admin rights, so I created one of those, went to permissions on media/array and I've altered them to allow read/write/execute by anybody.

It makes sense now, but I was barking up completely the wrong tree!

Thanks very much Charles!

---

### Post by CharlesA on 2011-02-04
Glad you got it working.

Don't forget to mark the thread as solved from thread tools. :)

---

### Post by Halkus on 2011-02-04
The only thing remaining related to this is if there's an fstab option which will cause the OS not to halt and wait on an instruction if a mount fails...  But even if I don't get an answer to that...

Less than one week after the death of my Windows Home Server array (which I had to rearm because their beta ended before a new beta came out) I have a new server running, with a functional array, both dead hard drives replaced by WD... and I can backup my PCs again. Plus I've got access to my music etc again :)

Up until now it's been a headache and a push to try to get function back, hopefully from this point on I can take my time and carefully tinker things right.

I do appreciate all the help I've been given. I hope you understand that with the whole home network in tatters my primary aim wasn't to learn Linux properly, it was to get things working, but now that they're working the pressure is off :)

---

### Post by CharlesA on 2011-02-04
Put 'nobootwait' in fstab. :)

That'll make it not hang if that device fails to mount.

---

### Post by Halkus on 2011-02-04
You have no idea how many times I've pulled down the ladder, climbed up the loft, and sat uncomfortably with the keyboard trying to fix it...

If only I'd known that at the start...

Although I can't find it in any manuals... do I just add it after default?  E.g.

```
UUID=f4027f7a-a1d5-4321-9d83-b4d9afa5c849     /media/array     ext4     defaults,nobootwait 0  0
```

---

### Post by CharlesA on 2011-02-04
Put it instead of defaults. :)

---

### Post by Halkus on 2011-02-04
Ok.. next question then... 

I was unable to find that - where did you get the answer from? If I'm going to make the most of the server up my loft then I need to be able to use the available reference well!

---

### Post by CharlesA on 2011-02-04
Trial and error. I found it on launchpad after I ran into a problem on 10.04. I'll have to find the link at home.

EDIT: Here's the link: [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571444](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571444)

---

### Post by Halkus on 2011-02-05
Ah. I'm less concerned now that it wasn't an blatantly obvious thing.

---

### Post by JKyleOKC on 2011-02-05
Back to an explanation of "umask" since I'm the one who offered you that red herring. I'll assume that you're familiar with the "mask" concept, where one pattern filters another. That is, an octal (base eight) value of 777 filtered through a mask (also octal) of 022 would give a result of 755. That's taking each digit by itself, and subtracting the value of the corresponding digit in the mask. It's actually an exclusive-or operation instead of ordinary subtraction, but in this case the result is the same either way.

Umask itself applies in many places throughout Linux file systems. The default value is 022, but you can set it to any 3-digit octal value. It's applied when a new file is created, and works on the old-style octal value of the file's permissions. If you're not familiar with that, it's a bit pattern composed of three groups of three bits each. Within each group, the 1-bit gives execute permission to files and browse permission to directories, the 2-bit allows writing, and the 4-bit allows reading. Thus a group of 7 gives rwx permission, 6 gives rw-, 5 gives r-x, 4 is r--, 3 is -wx, 2 is -w-, 1 is --x, and 0 is --- or no permission at all.

The leftmost group sets permissions for the owner, the middle one for the group, and the rightmost for the rest of the world. Thus 755 would be rwxr-xr-x.

A newly created file starts out with 777 permission; applying the default umask of 022 changes that to 755, which is what you were seeing. Setting the (appropriate) umask to 000 would make it leave the original 777 permissions alone.

Now as to where you can set the umask: it can be set in the smb.conf file to apply to Samba connections, either globally or specifically for each defined share. It's set for each user in ~/.bashrc at login time, and you can edit that file to change what each user gets upon logging in. And finally some filesystems recognize options in their fstab entries to set it at mount time. That's only the most often encountered options for it; I'm sure that more exist! And I'm not certain which settings override which others, so study and a bit of experimenting are a must.

Sorry to have misled you. It's still useful information to know, though...

---

### Post by Halkus on 2011-02-06
I see. I can see why that'd be useful. At the moment it doesn't seem to be of any use to me, but as I expand what I'm doing with Ubuntu - today I mounted a remote server as a local disk for example - things like this might come in handy later.

Thanks for all your help Jim!

---

