---
title: "Permission problems samba unbuntu 10.04 64bit"
date: 2011-09-08
forum: General Help
---

### Post by brownn74 on 2011-09-08
So i set up a samba file server on my computer to access my movies from any computer or share files and what not.  I followed this [guide]("https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html") to the T, and got my ext4 formatted partition that runs the os to work (read/write, accounts can access it from ubuntu and windows 7).  I have 2 raided harddrives formatted ntfs and tried to share them.  I used these commands (yes i changed the paths to suit my configuration)
[B]
sudo mkdir -p /srv/samba/share[/B] 
[B]sudo chown nobody.nogroup /srv/samba/share/

[/B]and they show up on the network but i can not read/write to them from anywhere.
I right click the specific folders and hover to permisions and it does not let
me change the group to sambashare.  IS there another command that i missed?
I've been trying for a week to solve this.  Any help would be great!

---

### Post by papibe on 2011-09-08
> **papibe]Try this on the server:
```
$ sudo chmod 777 /srv/samba/share
```
Or this, if you have subdirectories under share:
```
$ sudo chmod -R 777 /srv/samba/share
```
Regards.[/QUOTE]

[QUOTE=brownn74 said:**
> I have 2 raided harddrives formatted ntfs and tried to share them.
Oops, I missed that part. That is not valid for that.

Regards.

---

### Post by Morbius1 on 2011-09-08
You can't chmod or ch-anything an ntfs partition. 

You're going to have to declare what permissions you want in fstab. But with ntfs, the permissions declared in fstab will pertain to every subdirectory and every file unless you use something like bindfs.

---

### Post by brownn74 on 2011-09-08
how would i go about doing that?

---

### Post by Morbius1 on 2011-09-08
How are you mounting the ntfs partitions now?

If it through fstab post it's contents:
```
cat /etc/fstab
```

And are you sharing the entire partition or just a folder within it?

---

### Post by Morbius1 on 2011-09-08
Just thought of something - it happens to me every now and then. You stated this:
> So i set up a samba file server on my computer to access my movies from any computer or share files and what not.So you set this up on your own machine instead of a dedicated server machine? That means you log into it with a real username. If that's the case there's an easy way out of this.

Change the share definition from this:
> [share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755
To this:
> [share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    [COLOR=Blue]force user = morbius[/COLOR][COLOR=Blue]*Change morbius to the username you use to log into that machine.*[/COLOR]

Then restart samba:
```
sudo service smbd restart
```

---

### Post by brownn74 on 2011-09-09
[FONT=monospace]
cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/cciss/c0d1p1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/cciss/c0d1p5 during installation
UUID=e45a5335-ec8c-4e74-9e79-f5ff76fed84e none            swap    sw              0       0
UUID=XXXXXXXX /media/400GB  ntfs    defaults,umask=007,uid=1000,gid=1000 0       0
UUID=XXXXXXXX /media/300GB  ntfs    defaults,umask=007,uid=1000,gid=1000 0       0

[/FONT]

---

### Post by Morbius1 on 2011-09-09
You have created a share that allows guest access but your ntfs partitions will not allow guests ( i.e. users other than you ) to access the partition itself.

2 choices:

[1] Change the fstab entries form this:
> [FONT=monospace]UUID=XXXXXXXX /media/400GB  ntfs    defaults,umask=007,uid=1000,gid=1000 0       0[/FONT]To this:
> [FONT=monospace]UUID=XXXXXXXX /media/400GB  ntfs    defaults,**[COLOR=Blue]umask=000[/COLOR]**,uid=1000,gid=1000 0       0[/FONT]**OR:**

[2] Add force user to your share definitions as I described above:
> [share-name]
    comment = Ubuntu File Server Share
    path = [FONT=monospace]/media/400GB/share-name[/FONT]
    browsable = yes
    guest ok = yes
    read only = no
    [COLOR=Blue]**force user = morbius**[/COLOR][COLOR=Blue][I]
Change morbius to the username you use to log into that machine - the one that corresponds to "uid=1000"
[/I][/COLOR]

---

