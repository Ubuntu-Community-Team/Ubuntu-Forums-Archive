---
title: "Linux renames hard drives for no reason"
date: 2012-01-25
forum: General Help
---

### Post by Levitys on 2012-01-25
Good Morning everyone.

I keep having an issue with Ubuntu (lucid lynx).
Whenever I add a new hard drive to my htpc linux renames all the drives!
So what was sda changes to sdc what was sdb changes to sdd and so on.
No rhyme or reason.
Then when I go into xbmc none of my movies work and I have to re-scan and re-download all of the movie information which takes forever!

Can someone please explain to me why adding one hard drive constitutes the renaming of every other hard drive in my computer?

It makes no sense.
Is there a way to stop this?

This is a common problem that I keep having to deal with.

---

### Post by Dngrsone on 2012-01-25
Are these SATA drives?

I am thinking that your existing drives are plugged into SATA ports 4,5,6 and so when you add another drive, on say port 3, everything gets renumbered.

---

### Post by Levitys on 2012-01-25
> **Dngrsone said:**
> Are these SATA drives?

I am thinking that your existing drives are plugged into SATA ports 4,5,6 and so when you add another drive, on say port 3, everything gets renumbered.

Yes these are Sata Drives. On my motherboard the Sata ports are labeled 1-6. My OS drive is in 1 and I have been adding them in order everytime I get a new drive. But it renames all the drives when I add one.

**_Another Issue: _**I neglected to mention: Ever since adding the new drive last night when I boot up I get an Ubuntu Startup error saying one of the drives won't mount. Press S to skip and M to manual.

I am pretty sure this is my swap partition it's talking about. I turned off "Mount at boot" on the swap partition and I didn't get the error any more but no I don't think my Swap partition is booting.

**_Another Issue: _**The newest hard drive I added yesterday isn't showing up under Sata it's showing up under Pata. but in bios it's showing as sata.

Ahhhh! lol

Thanks for your help
Jeremy

---

### Post by carl4926 on 2012-01-25
> **Levitys said:**
> Good Morning everyone.

I keep having an issue with Ubuntu (lucid lynx).
Whenever I add a new hard drive to my htpc linux renames all the drives!
So what was sda changes to sdc what was sdb changes to sdd and so on.
No rhyme or reason.
Then when I go into xbmc none of my movies work and I have to re-scan and re-download all of the movie information which takes forever!

Can someone please explain to me why adding one hard drive constitutes the renaming of every other hard drive in my computer?

It makes no sense.
Is there a way to stop this?

This is a common problem that I keep having to deal with.

Me thinks Not!

Obviously there is a reason if you are adding HD's
Usually the Modo manual will have SATA layout plan for the HD SATA slots. Make sure you observe that info.

---

### Post by Levitys on 2012-01-25
> **carl4926 said:**
> Me thinks Not!

Obviously there is a reason if you are adding HD's
Usually the Modo manual will have SATA layout plan for the HD SATA slots. Make sure you observe that info.

My Sata ports are clearly labeled 1 - 6. Trust me I'm adding them in order.

---

### Post by Cheesemill on 2012-01-25
Try using UUID's in /etc/fstab instead of kernel naming descriptors (/dev/sd*)

 If your machine has more than one SATA, SCSI or IDE disk controller,  the order in which their corresponding device nodes are added is random.  This may result in device names like [COLOR=#222][FONT=monospace]/dev/**sda**[/FONT][/COLOR] and [COLOR=#222][FONT=monospace]/dev/**sdb**[/FONT][/COLOR]  switching around randomly on each boot, culminating in an unbootable  system, kernel panic, or a block device disappearing. Persistent naming  solves these issues.

---

### Post by Levitys on 2012-01-25
> **Cheesemill said:**
> Try using UUID's in /etc/fstab instead of kernel naming descriptors (/dev/sd*)

 If your machine has more than one SATA, SCSI or IDE disk controller,  the order in which their corresponding device nodes are added is random.  This may result in device names like [COLOR=#222][FONT=monospace]/dev/**sda**[/FONT][/COLOR] and [COLOR=#222][FONT=monospace]/dev/**sdb**[/FONT][/COLOR]  switching around randomly on each boot, culminating in an unbootable  system, kernel panic, or a block device disappearing. Persistent naming  solves these issues.

This sounds like my problem!

Although. I'm not sure it happens every boot.
Could you elaborate a little more on "Persistent Naming" , how to accomplish it and also UUID's etc/fstab and how to use it?

THANK YOU!!!!! :P

---

### Post by Cheesemill on 2012-01-25
To find the UUID's of your drives do:
```
sudo blkid
```Then just edit your fstab file using:
```
gksudo gedit /etc/fstab
```and replace all instances of /dev/sd* with UUID=xxx-xxx-xxx where xxx-xxx-xxx is the value you got from the first command.

An example fstab using UUID's

```
# <file system>                           <dir>         <type>    <options>             <dump> <pass>

tmpfs                                     /tmp          tmpfs     nodev,nosuid,noexec   0      0
 
UUID=24f28fc6-717e-4bcd-a5f7-32b959024e26 /     ext4              defaults,noatime      0      1
UUID=03ec5dd3-45c0-4f95-a363-61ff321a09ff /home ext4              defaults,noatime      0      2
UUID=4209c845-f495-4c43-8a03-5363dd433153 none  swap              defaults              0      0
```For more info:
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

### Post by Levitys on 2012-01-25
Thanks for your help Cheesmill,

One more question if you don't mind:
Is there a way to check and see if my system has more than one SATA controller?
and if so it there a way to make it so that only one works?
Thereby fixing the problem?

Thanks

---

### Post by Cheesemill on 2012-01-25
If you have more than 4 SATA ports then you almost definitely have 2 or more SATA controllers, one built into your chipset plus one or more extra on the motherboard.

Either google for your motherboard make/model and look at the full specs or post your hardware details here and I'll take a look for you.

---

### Post by dcstar on 2012-01-25
> **Levitys said:**
> Thanks for your help Cheesmill,

One more question if you don't mind:
Is there a way to check and see if my system has more than one SATA controller?
and if so it there a way to make it so that only one works?
Thereby fixing the problem?

Thanks

The "problem" is specifically why UUIDs exist. Use the mechanism as you are supposed to and there will be no "problem".

---

### Post by Levitys on 2012-01-26
Cheesemill,

I edited the fstab file as you suggested and it worked but not without another issue popping up:
I had 2 links for each hard drive in my sidebar. One looked like the regular hard drive icon and the other looked like a "slim" hard drive or possibly a "usb" ? it was white and slim. I changed the fstab file back to the way it was before until I speak with you further. I previously had been using pySDM to get the HDDs to mount at boot. I don't know if maybe this is why I'm getting "2" Icons per drive or what.

Anyways my motherboard is the ASUS M4A88T-M LE

Thanks man,
I REALLY APPRECIATE IT!
Jeremy

> **dcstar said:**
> The "problem" is specifically why UUIDs exist. Use the mechanism as you are supposed to and there will be no "problem".

I had no idea that UUIDs even existed till now. lol
But if that is the case Ubuntu should automatically use them.
Seems like a bunch of Hassle not to use UUIDs in the first place.

Thanks for your help
Jeremy

---

### Post by jocko on 2012-01-26
> **Levitys said:**
> 
I had no idea that UUIDs even existed till now. lol
But if that is the case Ubuntu should automatically use them.
Seems like a bunch of Hassle not to use UUIDs in the first place.
Ubuntu has been using UUIDs in fstab for years now...
The reason for your hassle must be that you set up the mount points for your drives using some tool (pySDM) that has not been updated the last five or six years...

---

### Post by Levitys on 2012-01-26
> **jocko said:**
> Ubuntu has been using UUIDs in fstab for years now...
The reason for your hassle must be that you set up the mount points for your drives using some tool (pySDM) that has not been updated the last five or six years...

I used Gparted To format/partition the drives and then I used pySDM to make the drives mount at boot. Why would they include something so outdated in the repository/distro? :(

How do I clear the problems that pySDM has created and fix the problems I mentioned in my earlier post about the Double sidebar icons? Also These drives are mounting in /Media/sd* Should they be in the media folder?

Thanks man
Jeremy

---

### Post by Levitys on 2012-01-26
[IMG]http://i41.tinypic.com/jkyrmo.png[/IMG]

This is a image to show you guys what i mean about the two icons per drive.....its really weird.

also i uninstalled pysdm and here is a copy of my fstab file.

whats goin on here guys?

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid                       0  0  
# / was on /dev/sda1 during installation
UUID=a272f969-9f57-4fbe-b034-eedfc326a5c2  /            ext4  errors=remount-ro                         0  1  
UUID=7592e4e9-1bf6-4067-9f77-40b59b2ffce3  none         swap  defaults
# swap was on /dev/sda5 during installation
UUID=7AE6E79A2B107BF3                      /media/sdb1  ntfs  nls=iso8859-1,umask=000,uid=jeremy        0  0  
UUID=2EB79EB0244E4C81                      /media/sdd1  ntfs  nls=iso8859-1,umask=000,uid=jeremy        0  0  
UUID=32219F6863BC1835                      /media/sdc1  ntfs  nls=iso8859-1,users,umask=000,uid=jeremy  0  0  
UUID=4A1EAB5F3F5FD97B                      /media/sde1  ntfs  nls=iso8859-1,users                       0  0  
```

---

### Post by Levitys on 2012-01-26
[http://i43.tinypic.com/2eeegck.png](http://i43.tinypic.com/2eeegck.png)

here is a better link of the photo so u can see it better.
if i vlivk on the drives at the bottom it gives me an error

unable to mount:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

---

### Post by Cheesemill on 2012-01-26
I'm probably wrong here but it could be because you are mounting them in /media 
This is where Ubuntu automatically mounts removable devices so this could be where the Removable Drive icons could be coming from.

Try mounting them somewhere else and see if it makes a difference. I usually mount my storage drives under /data

---

### Post by Levitys on 2012-01-26
OH MY GOD!

I just went into system manager for some random reason. 

IM NOT CRAZY!!!!

check out this screenshot:
The drives are mismatched!!!

[IMG]http://i44.tinypic.com/awvl15.png[/IMG]

ANyone know how to fix this?

---

### Post by Cheesemill on 2012-01-26
If I remember correctly blkid uses cached information by default.

If you issued the blkid command after the drives had switched descriptors but before the cache was updated you may have got incorrect information about which UUID was for which device.

To bypass the cache and directly probe each drive for it's UUID try:
```
sudo blkid -p /dev/sdb1
```

---

### Post by oldfred on 2012-01-26
I am like    	Cheesemill, except I mount my two data partitions as /mnt/shared (NTFS) &  /mnt/data (ext3) and link folders into /home.

I always label every partition when I create it or use Disk Utility to label it so any partitions I do not auto mount have labels as the default mount.

To prevent dual mounts do not mount in /home or /media. 

Duplicate mounts of partitions in Nautilus left panel
use /dev/disk/by-uuid/xxxxx...
[http://ubuntuforums.org/showthread.php?t=1561929](http://ubuntuforums.org/showthread.php?t=1561929)

If you mount a partition as music, it does not matter what the system thinks the drive is, it will always be music. Use names that mean something to you not drive numbers. One of the advantages of Linux is that you can mount by label and not just have c:, d: etc which have little meaning.

---

### Post by CharlesA on 2012-01-26
```
sudo blkid -c /dev/null
```

Would give you a good reading too.

I mount my data drives in a folder off of root and don't use either /mnt/ or /media/.

---

### Post by Levitys on 2012-01-26
ok guys so I took all of your advice and made the corrections. i believe it worked! its odd though now the drives aren't in the sidebar with the eject button but i think thats a good thing. i mounted all the drives in /dev/mnt/ 

here is a screenshot of the results 

[IMG]http://i39.tinypic.com/s3kgpj.png[/IMG]

The only thing that puzzles me is that the drives still aren't labeled in the order they are plugged in. well most of them are but 2 and 3 are switched around. I cant be reading the mobo wrong i just cant be it doesn't make any sense. I'm tempted to take a photo of it to post here lol.

anyways the drives seem stable so I'm gonna leave it the way it is. I suppose only time will tell if adding another hdd is going to jumble everything again.

thank you all for your help. you guys are all life saving geniuses lol

THANK U THANK U THANK U!!!!!

---

### Post by dcstar on 2012-01-27
> **Levitys said:**
> 
..........
anyways the drives seem stable so I'm gonna leave it the way it is. I suppose only time will tell if adding another hdd is going to jumble everything again.

thank you all for your help. you guys are all life saving geniuses lol

THANK U THANK U THANK U!!!!!

So the thread is now **Solved**, is it?

---

