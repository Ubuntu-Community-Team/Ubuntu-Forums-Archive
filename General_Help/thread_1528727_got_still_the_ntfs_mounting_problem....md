---
title: "got still the ntfs mounting problem..."
date: 2010-07-11
forum: General Help
---

### Post by konnigbg on 2010-07-11
Edit:
[COLOR=Red]the problem is solved, i couldnt mount the drive because ist was dynamic, i had to delete the both dynamic drives with the windows partition tool (system reserved and the real one) format the whole drive to ntfs so that it was back in basic mode, and now its working fine[/COLOR] 
**[COLOR=Red]thank you all fort your great help[/COLOR]**

hey folks, a few weeks ago i switched from win7 to ubuntu 10.04 and im quite happy with it ;)

but there is still  a problem i couldnt solve with all the google and forum researches:

i have a 1tb hard-drive formated in NTFS with a lot of data on it and i cannot mount it

on startup its says "an error occurred while mounting press s to skip or m to mount manually", 
ok i tried to edit my fstab, tried ntfs configuartion tool set myself to user group FUSE (even i dont know what this mean), i checked the drive at windows for errors , and i created a mount point at media/1tb

if i try to open the drive in my gnome desktop i get this message:
```
Unable to mount 1.0 TB Filesystem
Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged
```here is my blkid (some times it detects the EE60D5FE60D5CD89 drive, which is the 1tb drive not as NTFS but as SFS):
```
/dev/sda1: LABEL="System-reserviert" UUID="A238424338421727" TYPE="ntfs" 
/dev/sda2: UUID="A07045D57045B2B8" TYPE="ntfs" 
/dev/sdb2: UUID="EE60D5FE60D5CD89" TYPE="ntfs" 
/dev/sdc1: UUID="0573c3b3-0fb4-474b-b546-978db55e47a0" TYPE="ext4" 
/dev/sdc5: UUID="cd1a36cf-c606-4890-a84b-96265c93b18f" TYPE="swap" 
```here is my fstab (actually im wondering where the fiorst lines are?!)
```
UUID=0573c3b3-0fb4-474b-b546-978db55e47a0 / ext4 defaults 0 1
UUID=cd1a36cf-c606-4890-a84b-96265c93b18f swap swap sw 0 0
UUID=EE60D5FE60D5CD89 /media/1tb ntfs-3g user,auto,locale=en_US.utf8    0    0
UUID=A238424338421727 /media/System_reserviert ntfs-3g defaults 0 0
UUID=A07045D57045B2B8 /media/sdb2 ntfs-3g nosuid,nodev,noexec,umask=000 0 0
```maybe you can help me...

---

### Post by WorMzy on 2010-07-11
From the looks of things, your terabyte drive should be mounting fine. Is /media/1tb empty? What about /media/sdb2 and /media/System_reserviert?

---

### Post by konnigbg on 2010-07-11
hi, thx for your fast reply and help, actually i have no idea where "system_reserviert" comes from.. maybe some old windows partition? sdb2 is my other harddrive with 500gb weheras windows7 is located, this one works fine (on screenshot sitll countig the files), 
take a look

[IMG]http://img189.imageshack.us/img189/8886/screenshot1xh.png[/IMG]

---

### Post by WorMzy on 2010-07-11
Can you run ```
sudo mount -a
``` It may print out an error that tells us why it's failing to mount. I think system_reserviert is probably a backup partition for the OS that your PC originally came with.

---

### Post by Pizack on 2010-07-11
[http://ubuntuforums.org/showthread.php?t=1528486](http://ubuntuforums.org/showthread.php?t=1528486)
try the fix towards the bottom of this thread suggested by bodhi.zazen, it seems to fix permission errors.

---

### Post by konnigbg on 2010-07-11
@WormZy:

here it is:
```
Failed to read last sector (1953517567): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```
@Pizack: thx but this seems not to work

i tried it like this:
```
sudo chown "myusername":users /media/1tb
sudo chmod 770 /media/1tb
```
right?

---

### Post by Morbius1 on 2010-07-11
> UUID=EE60D5FE60D5CD89 /media/1tb ntfs-3g user,auto,locale=en_US.utf8    0    0Get rid of the "user" option. In fact you might want to do a cleanup of the whole expression:
```
 UUID=EE60D5FE60D5CD89 /media/1tb ntfs-3g defaults,nls=utf8 0 0
```Or you could use the default expression that Ubuntu uses during an install if you had asked it to mount these non-system partitions:
> UUID=EE60D5FE60D5CD89 /media/1tb  ntfs    defaults,nls=utf8,umask=007,gid=46 0       0

---

### Post by Morbius1 on 2010-07-11
> **konnigbg said:**
> [/CODE]@Pizack: thx but this seems not to work

i tried it like this:
```
sudo chown "myusername":users /media/1tb
sudo chmod 770 /media/1tb
```right?
Can't chown or chmod an NTFS or FAT32 partition. There aren't any ownership or permissions "bits" to set on a Windows filesystem.

---

### Post by WorMzy on 2010-07-11
I've never had any problems with the user option myself.

That message, coupled with it periodically detecting it as SFS leads me to believe that it is corrupted in some way. If you have any valuable data on it, I would attempt to recover it with some form of data recovery software, such as TestDisk, back it up somewhere safe, then reformat the partition.

---

### Post by konnigbg on 2010-07-11
i tryed morbius1 fstab entry an got this error, its the same error i got when i installed ubuntu, the errors changed while playing arround with fstab & co ;):
```

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb2 on /media/1tb
```

thought about formating but there are 850gb files on it, hard to backup.. 
and in windows i have perfect access to all files (i have dual boot at the moment because i have some apps only running at windows), and chdsk found no errors, hard-drive seem to be healthy

---

### Post by WorMzy on 2010-07-11
That's a strange error to be getting from fstab, it's only ever run as root.

Can you try running
```
sudo mount -t ntfs /dev/sdb2 /media/1tb
```

If that fails then try booting into Windows and running chkdsk on the partition. It may fix any problems without needing to reformat the partition.

---

### Post by Morbius1 on 2010-07-11
Post your fstab again please

---

### Post by Morbius1 on 2010-07-11
BTW, you do realize that there is a mismatch in how you're looking at your partitions right?

From blkid:
> /dev/[COLOR=Sienna]sda2[/COLOR]: UUID="[COLOR=Blue]A07045D57045B2B8[/COLOR]" TYPE="ntfs" 
/dev/sdb2: UUID="EE60D5FE60D5CD89" TYPE="ntfs" 
From fstab:
> UUID=[COLOR=Blue]A07045D57045B2B8[/COLOR] /media/[COLOR=Sienna]sdb2[/COLOR] ntfs-3g nosuid,nodev,noexec,umask=000 0 0

---

### Post by konnigbg on 2010-07-11
i did the chkdsk in windows last day, so hd seems to be without errors :/

@morbius1

i tried to correct the blkid/fstab mistake, now it looks like this:

blkid:
```
/dev/sda1: LABEL="System-reserviert" UUID="A238424338421727" TYPE="ntfs" 
/dev/sda2: UUID="A07045D57045B2B8" TYPE="ntfs" 
/dev/sdb2: UUID="EE60D5FE60D5CD89" TYPE="ntfs" 
/dev/sdc1: UUID="0573c3b3-0fb4-474b-b546-978db55e47a0" TYPE="ext4" 
/dev/sdc5: UUID="cd1a36cf-c606-4890-a84b-96265c93b18f" TYPE="sw
```and fstab:
```
UUID=0573c3b3-0fb4-474b-b546-978db55e47a0 / ext4 defaults 0 1
UUID=cd1a36cf-c606-4890-a84b-96265c93b18f swap swap sw 0 0
UUID=EE60D5FE60D5CD89 /media/sdb2 ntfs-3g defaults,nls=utf8 0 0
UUID=A238424338421727 /media/System_reserviert ntfs-3g defaults 0 0
UUID=A07045D57045B2B8 /media/sda2 ntfs-3g nosuid,nodev,noexec,umask=000 0 0
```so now its correct right? but the same error occurs while mounting, just saying sdb2 instead of 1tb :/

---

### Post by Morbius1 on 2010-07-11
Something's not making sense. That is the exact output of:
```
cat /etc/fstab
```And just to make absolutely sure we're all doing the same thing here, the blkid command you used is this one?
```
sudo blkid -c /dev/null
```

---

### Post by WorMzy on 2010-07-11
What happened when you ran
```
sudo mount -t ntfs /dev/sdb2 /media/1tb
```

Any errors?

---

### Post by QLee on 2010-07-11
Just a hint, that sfs partition is probably a "dynamic" disk in Windows.

---

### Post by Jose Catre-Vandis on 2010-07-11
This is all I have in my fstab to mount my main W7 partition (Xubuntu installed after W7). Don't even remember having to install any nfts tools or helper programs.

```
UUID=DCE08D3CE08D1DC0  /media/W7 ntfs-3g defaults 0 0
```

Also use some slightly less confusing mountpoints to make it easier to spot what is going wrong

---

### Post by konnigbg on 2010-07-11
ok, i used

```
sudo blkid 
``` but thats the same output

and i used

```
sudu gedit /etc/fstab/

```and that is all what ist in the fstab file, normaly there are some headlines right? somehow they disappeared, but the error was already existing when the lines were there ;)
 
each time i restart the computer the devices names change i guess, sometimes it is sdb2, sometimes sdc2

so now the actual blkid is:
```
/dev/sda1: UUID="0573c3b3-0fb4-474b-b546-978db55e47a0" TYPE="ext4" 
/dev/sda5: UUID="cd1a36cf-c606-4890-a84b-96265c93b18f" TYPE="swap" 
/dev/sdb1: LABEL="System-reserviert" UUID="A238424338421727" TYPE="ntfs" 
/dev/sdb2: UUID="A07045D57045B2B8" TYPE="ntfs" 
/dev/sdc2: UUID="EE60D5FE60D5CD89" TYPE="ntfs
```and fstab (all text in file!):
```
UUID=0573c3b3-0fb4-474b-b546-978db55e47a0 / ext4 defaults 0 1
UUID=cd1a36cf-c606-4890-a84b-96265c93b18f swap swap sw 0 0
UUID=EE60D5FE60D5CD89 /media/sdc2 ntfs-3g defaults,nls=utf8 0 0
UUID=A238424338421727 /media/System_reserviert ntfs-3g defaults 0 0
UUID=A07045D57045B2B8 /media/sdb2 ntfs-3g nosuid,nodev,noexec,umask=000 0 0
```if i use this:
```
sudo mount -t ntfs /dev/sdb2 /media/1tb
```now after "correctet fstab"
```
sudo mount -t ntfs /dev/*sdc2 */media/sdc2
```i get this,*same*:

[I]Edit... now thats what i got if i do it right:

Failed to read last sector (1953517567): Invalid argument[/I] [I]
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdc2': Invalid argument
The device '/dev/sdc2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around

[/I]
edit2:[I]
@[/I][Jose  Catre-Vandis]("http://ubuntuforums.org/member.php?u=78483"):
how do i delete the mountpoints? which shall i take? like 1tb 500gb 160gb for the devices or sdc2 sda2 sdb2 etc as it is sayd in blkid? the last ones are always changing

my other drive, the 500gb drive, is all the time mounted very well i have wirte and read access, this one is the one where w7 is installed, the 1tb drive is just data formated in ntfs

---

### Post by Morbius1 on 2010-07-11
These are more random thought than anything helpful I'm afraid.
> QLee
Just a hint, that sfs partition is probably a "dynamic" disk in  Windows.     If that is true then I'm not familiar with how that would impact mounting in linux. Did you set your disk to be dynamic in Windows?

If that is in fact the total output of fstab then you have a line missing:
> proc /proc proc    nodev,noexec,nosuid 0       0I'll have to go through my notes and find out the significance of and the results of not having that line in fstab.

I do remember that it's a memory resident virtual file system that basically keeps track of stuff but I'm not sure what happens when it's missing or if it's even relevant to this issue..

For the money I think QLee may have the cause. Care to share with us the answer?

---

### Post by konnigbg on 2010-07-11
i added the lines, without effect

---

### Post by WorMzy on 2010-07-11
Okay, it looks as though this is a problem with the partition, rather than a problem with the way you're mounting it. This link suggests some possible solutions: [http://www.tuxera.com/forum/viewtopic.php?f=3&t=124](http://www.tuxera.com/forum/viewtopic.php?f=3&t=124) but none of them have any indication of their success rate.

The problem is caused by the NTFS partition being smaller than it's reported size, so when you try to mount it under Linux you get an error because the end of the partition isn't readable (because it doesn't exist). You may be able to mount it as read only, but mounting it as read+write is likely to end in tears. Since chkdsk didn't report any problems, I can only recommend two things: 1) backup your data and resize the partition (if possible) so that when you mount it in Linux the end of the partition is readable, or 2) backup your data and reformat the partition as NTFS again.

Either way, it's not a particularly great solution. You could risk resizing the partition without backing up if you want to try that, but if the partition becomes corrupted, there's no guarantee that you'll be able to recover all your data.

---

### Post by Morbius1 on 2010-07-11
> The problem is caused by the NTFS partition being smaller than it's  reported size, so when you try to mount it under Linux you get an error  because the end of the partition isn't readable (because it doesn't  exist). Wouldn't that cause a problem when he boots into windows as well?

And wouldn't the same phenomenon happen if they were in fact dynamic disks? A dynamic disk isn't even limited to the same physical hard drive.

It would be helpfull though if konnigbg would tell us if he set them to be dynamic.

---

### Post by konnigbg on 2010-07-11
actually i dont know how to set a disk dynamic,
but i could try to find out

and ill also try the partioniering in windows and back up only the most important.
if u got some other helpfull ideas about this issue let me know.

ill report you wether i have some succes 

ill go for sleep
good night and thanks for your time

edit: 
ok i checked it, its a dynamic drive ill now backup my files and format the drive in basic

---

