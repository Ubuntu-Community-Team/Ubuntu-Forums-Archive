---
title: "Hide Partitions/Drives from Nautilus (side panel)"
date: 2010-05-29
forum: General Help
---

### Post by ixifx on 2010-05-29
I have 2 drives formatted NTFS, which I'm mounting with /etc/fstab to ~/Movies/ and ~/Music/ and an EXT4 partition on my primary drive for games, mounted to ~/Roms/  and I would like for these drives to NOT show up in the side panel of nautilus.

I've been doing some looking around, and what I've found so far is that supposedly if you mount a partition/drive somewhere besides /media/ nautilus will ignore it.  I'm finding this not to be the case, and it's driving me bonkers.

here's my fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c9af848e-ba1c-46bf-a687-d9d22fa89ebb none            swap    sw              0       0
# Roms on /dev/sda3
/dev/sda3	/home/john/Roms	ext4    errors=remount-ro 0       1
# Music on /dev/sdb1
/dev/sdb1	/home/john/Music	ntfs	rw,user,auto 0 0
# Movies on /dev/sdc1
/dev/sdc1	/home/john/Movies	ntfs    rw,user,auto 0 0

```

I'd like all the drives mounted with fstab to be hidden from the nautilus side panel, but would like to keep any removable media still visible there.

---

### Post by Penguin Guy on 2010-05-29
I had a similar problem not long ago: I didn't want any nautilus sidebar objects or any desktop icons linking to my [FONT="Courier New"]~/Home[/FONT] partition, but couldn't find any way to get rid of them. I eventually discovered that if I mounted the partition somewhere other than /media or /home and symlinked to it, the nautilus buttons would disappear. [Post here.]("http://ubuntuforums.org/showthread.php?t=1477938")

---

### Post by ixifx on 2010-05-29
I'll just give this a little
bump

---

### Post by Jeroensum on 2010-05-30
If you don't want a mount to show up in Nautilus just mount it under a subdir of /mnt and make a symlink to it from your homedir for easy access :)


mkdir /mnt/movies
sudo mount /dev/sdc1 /mnt/movies -o rw,user,auto
ln -s /mnt/movies /home/john/movies

---

### Post by ixifx on 2010-05-30
yup, that does the trick.

thanks =)

---

### Post by Penguin Guy on 2010-05-30
> **ixifx said:**
> yup, that does the trick.

thanks =)
Glad you've found what you wanted, but it would be helpful to others if you could [mark your thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). Thanks. :)

---

### Post by ixifx on 2010-05-31
indeed it would.

done and done =)

---

### Post by gsiliceo on 2010-06-03
This works as long as linux can mount the partitions i have a ZFS (Open solaris) slice that does not mount and i can't hide it using this method, any other ideas?

---

### Post by Penguin Guy on 2010-06-04
> **gsiliceo said:**
> This works as long as linux can mount the partitions i have a ZFS (Open solaris) slice that does not mount and i can't hide it using this method, any other ideas?
It probably would have been a better idea to start a new thread rather than re-using this one. As for your problem, make sure you have an fstab entry for your partition - if you need help making one, please post the output of [FONT="Courier New"]sudo fdisk -l[/FONT] and [FONT="Courier New"]sudo blkid[/FONT] .

---

### Post by gsiliceo on 2010-06-04
Is not adding to fstab the problem, ubuntu 10.04 cannot mount ZFS partitions doesn't matter what. But thanks
I'm guessing it has something to do with a hidden nautilus configuration that allows you to disable its autofind partitions.

---

### Post by Penguin Guy on 2010-06-05
> **gsiliceo said:**
> Is not adding to fstab the problem, ubuntu 10.04 cannot mount ZFS partitions doesn't matter what. But thanks
I'm guessing it has something to do with a hidden nautilus configuration that allows you to disable its autofind partitions.
No; as I said, it is done in FSTab by specifying a mount point other than [FONT="Courier New"]/media[/FONT] or [FONT="Courier New"]/home[/FONT]. You can specify a mount point for a device even if you can't mount it (try using the [FONT="Courier New"]noauto[/FONT] option).

---

### Post by gsiliceo on 2010-06-07
Tried it in fstab
#/dev/sda12 /mnt/dontopen noauto
#/dev/sda3 /mnt/dontopen1 noauto
Those are ZFS partitions, well ubuntu thinks that one of them is HFS for some reason, but thats actually the slice.
When booting it gives me an error at the ubuntu logo boot screen saying it couldn't mount them, "skip or mount manually" and when coming to the desktop nautilus still shows their entries in the places menu, but of course you cannot mount them.

I of course created the folders in /mnt/...

---

### Post by Penguin Guy on 2010-06-07
> **gsiliceo said:**
> Tried it in fstab
#/dev/sda12 /mnt/dontopen noauto
#/dev/sda3 /mnt/dontopen1 noauto
Those are ZFS partitions, well ubuntu thinks that one of them is HFS for some reason, but thats actually the slice.
When booting it gives me an error at the ubuntu logo boot screen saying it couldn't mount them, "skip or mount manually" and when coming to the desktop nautilus still shows their entries in the places menu, but of course you cannot mount them.

I of course created the folders in /mnt/...
You missed out some columns: fs-type, options, dump-freq, pass-num. Although it does seem weird that the partitions are still displayed in Nautilus.

---

### Post by gsiliceo on 2010-06-07
File type is ZFS, the problem is linux cannot mount that file system, i don't know what to put in the other columns, i never mounted a ZFS before.

---

### Post by Penguin Guy on 2010-06-08
> **gsiliceo said:**
> File type is ZFS, the problem is linux cannot mount that file system, i don't know what to put in the other columns, i never mounted a ZFS before.
Try:
```

/dev/sda12 /mnt/dontopen zfs noauto 0 0
/dev/sda3 /mnt/dontopen1 zfs noauto 0 0

```
Even though it cannot mount the partitions, it should recognize the mount point. If it doesn't, then I don't know what else to try.

---

### Post by gsiliceo on 2010-06-19
Forgot to thank you penguin guy, those lines worked, it doesnt show anymore those zfs partitions my nautilus places menu, they show on /mnt but i don't mind :)

---

### Post by Kanji_Man on 2010-10-26
Sorry to dust off an old thread but this keeps coming up on google when trying to figure out how to hide the "ghost" zfs volumes from nautilus.

I've found that mounting the drive to /dev/null also works well and does not require you to litter your drive with extra directories.  I've also found that mounting the drive to the device ID instead of the /dev/path can avoid problems with hiding the wrong drives if your drives change order on the system. (to find the device ID, "ls /dev/disk/by-id/ -l").  My resulting /etc/fstab looks something like this:

```

# /etc/fstab: static file system information.
#
# <file system>					<mount point>	<type>		<options>			   <dump> <pass>
UUID=1a2b3c4d-1f2g-abcd-1234-915fae1831a2	none		swap		sw					0 0
UUID=5e6f7e8f-2a3b-abcd-4567-0f3eaba61763	/		ext4		errors=remount-ro			0 1
proc						/proc		proc		nodev,noexec,nosuid			0 0
/dev/scd0					/media/cdrom0	auto		user,noauto,exec,utf8			0 0
/dev/disk/by-id/scsi-SATA_ST31500341AS_6VS00011	/dev/null	zfs		noauto					0 0
/dev/disk/by-id/scsi-SATA_ST31500341AS_6VS00022	/dev/null	zfs		noauto					0 0
/dev/disk/by-id/scsi-SATA_ST31500341AS_6VS00033	/dev/null	zfs		noauto					0 0
/dev/disk/by-id/scsi-SATA_ST31500341AS_6VS00044	/dev/null	zfs		noauto					0 0

```

---

### Post by impert on 2010-11-22
Since this old thread is still staggering on, I thought I'd add my grain of salt.

I have rather a lot of partitions with different distros, so I wrote a little script to add the necessary lines to each /etc/fstab.
I was a bit worried that, if I changed the file system on a partition that it might get mounted with the wrong fs, particularly if the fs shown in fstab was ext4 and the fs was actually ext3. According to the [ext4 howto]("https://ext4.wiki.kernel.org/index.php/Ext4_Howto"), if an ext3 partition is mounted and written to as ext4, it may be impossible to return it to ext3, which is inconvenient if it has an old kernel which doesn't understand ext4.

A little experimentation showed that **mount** (at least v.2.16) doesn't seem to read the file type in fstab when the **noauto** option is present - the partition gets mounted with the right file type anyway. (Ain't Linux wonderful?) Just in case, though, I'd suggest using a nonsense file type - I tried "**pizza**" - the worst you get then should be an error message.

Now for the rant: Surely this ought to be considered a bug in Nautilus. It would be really nice to have the option of turning off the default listing of unmounted HD partitions - I can't see why anyone would want to see them.

---

### Post by gsiliceo on 2010-11-22
I think the "thread is dead" way of thinking is wrong, if this thread talks about a particular issue, everybody should use it instead of creating a new one(its the GTD philosophy), no matter how old is it <rant mode off> I would consider it as a bug also. Could you post your script, i think it could be useful for other people and i certainly would like to see it.

---

### Post by impert on 2010-12-05
Sorry for not replying sooner.
I blush for the simplicity of this, but since you asked for it:
```
#! /bin/bash
#nautilus_crap_fstab
#To get rid of unwanted devices in Nautilus - adds a lot of crap to fstab

for file in $(ls /SD); do
	if [[ ! $(grep sd$file /etc/fstab) ]]; then #don't overwrite existing entries
		echo "/dev/sd$file  /SD/$file  pizza noauto 0 0" >> /etc/fstab
	fi
done
exit
```
No warranty of fitness for purpose or anything else of course. If all your chickens die because of it curry them!
Edit:I forgot to explain that when I mount partitions which are not mounted at boot, I use folders called /SD/a5 /SD/a6 etc, (created by another trivial script). The reason is that if I mount more than one or two partitions simultaneously using names like /mnt/temp I forget which is which. Also, I don't have to type **sudo mkdir . . .** every time.

---

### Post by gsiliceo on 2010-12-05
Oh thats useful if you have tons of partitions to hide like i do :P thank you so much, its a little hacky, but all solutions that fix design errors are, why should we be forced to do what nautilus wants? isnt linux about customization? Thanks again

---

### Post by impert on 2010-12-06
You're more than welcome.

---

