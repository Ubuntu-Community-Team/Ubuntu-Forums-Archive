---
title: "Read write permissions on storage drive"
date: 2009-08-21
forum: General Help
---

### Post by joebob213 on 2009-08-21
I have been battling this for weeks!  Searched all around this forum and google and nothing works.  I have a dual boot drive with Ubuntu 9.04 and Windows XP plus another 500 gig drive for storage only.  On the storage drive I can access the files just fine but I can't save anything to it or delete anything without using nautilus.  I have Storage Device Manager installed and I've tried using it to own the drive, doesn't work.  I've also tried several "chown" commands without resolution.  My wife also has a profile on the system and we are both in the group "admin".  I would like to make it so we both have full permissions to this drive.  Possible?

---

### Post by howefield on 2009-08-21
I do not know what you have tried, but in the same position, all I had to do was type the following in terminal

```
sudo chown username Data
```

"username" being mine, and "Data" being the disk label.

What do you mean exactly by this...

> but I can't save anything to it or delete anything without using nautilus.

---

### Post by bryncoles on 2009-08-21
or you can press alt and f2 to bring up the run dialogue. type ```
gksudo nautilus
```to open the file browser as root (be careful here - you are now able to do really stupid things to your computer!). brows to the /media location, right click your drives and fiddle the properties from there!

---

### Post by DaithiF on 2009-08-21
Hi, it would be useful to know what kind of filesystem you have on the data drive, plus how you are mounting it.

can you run & post the output from:
sudo fdisk -l

---

### Post by DaithiF on 2009-08-21
sorry, hit enter too soon :)

thats a lower-case L in the previous command

and can you also post the contents of /etc/fstab

thanks

---

### Post by joebob213 on 2009-08-21
> **howefield said:**
> I do not know what you have tried, but in the same position, all I had to do was type the following in terminal

```
sudo chown username Data
```


"username" being mine, and "Data" being the disk label.

That does not work.  I am not on my computer right now but if I remember correctly it returns an error somewhere along the lines of "changing ownership not allowed.  permission denied"  I'm sure that's not the exact message but it's close.


> **howefield said:**
> What do you mean exactly by this...

> **joebob213 said:**
> I can't save anything to it or delete anything without using nautilus.  

I mean the only way I can write files to the drive or delete files from it is by using ```
gksudo nautilus
``` as bryncoles suggested.

---

### Post by joebob213 on 2009-08-21
> **DaithiF said:**
> Hi, it would be useful to know what kind of filesystem you have on the data drive, plus how you are mounting it.

can you run & post the output from:
sudo fdisk -l

It's a fat32 drive and it mounts at boot.  I will post the fdisk output when I get home today.

---

### Post by howefield on 2009-08-21
> **joebob213 said:**
> That does not work.  I am not on my computer right now but if I remember correctly it returns an error somewhere along the lines of "changing ownership not allowed.  permission denied"  I'm sure that's not the exact message but it's close.

The only way I can replicate the error is by not prefacing the chown command with sudo. 

eg

```
****@****-desktop:/media$ chown root Data
chown: changing ownership of `Data': Operation not permitted
****@****-desktop:/media$
```

---

### Post by justleen on 2009-08-21
Sounds like your not putting "sudo" in front of the commands, if gksudo nautilus is the only way to get it working.

Change the ownership of the whole drive i'd say!
```
sudo chown -R username:groupname /media/disk/ 
```

---

### Post by DaithiF on 2009-08-21
Hi,
since its a fat32 drive then it doesn't have inherent user/group permissions, only what the system assigns to it at mount time based on whatever is specified in /etc/fstab.

chown is only going to affect ownership up until the next reboot, or the next remount.
so if you want yourself & your wife to permanently have access then i would suggest setting group ownership (gid=xxx) to a group you & your wife already share, or a new group you set up for this purpose.

Also give it a umask=002 parameter, which will make permissions RWX for user, RWX for group and RX for everyone else

so basically, in the mount options for this drive in /etc/fstab, add options like:
umask=002,gid=yourgroupname

hope this helps

---

### Post by joebob213 on 2009-08-21
> **justleen said:**
> Sounds like your not putting "sudo" in front of the commands, if gksudo nautilus is the only way to get it working.

Change the ownership of the whole drive i'd say!
```
sudo chown -R username:groupname /media/disk/ 
```

I was most certainly using sudo before the commands :confused:

> **DaithiF said:**
> Hi,
since its a fat32 drive then it doesn't have inherent user/group permissions, only what the system assigns to it at mount time based on whatever is specified in /etc/fstab.

chown is only going to affect ownership up until the next reboot, or the next remount.
so if you want yourself & your wife to permanently have access then i would suggest setting group ownership (gid=xxx) to a group you & your wife already share, or a new group you set up for this purpose.

Also give it a umask=002 parameter, which will make permissions RWX for user, RWX for group and RX for everyone else

so basically, in the mount options for this drive in /etc/fstab, add options like:
umask=002,gid=yourgroupname

hope this helps

I tried all that before.  We are both in group "admin" and we supposedly owned that drive.  

I saved myself some headaches and formatted the drive to NTSC... everything works great now!  Thanks guys.

---

