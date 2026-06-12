---
title: "Help with pysdm"
date: 2011-01-31
forum: General Help
---

### Post by grindboy on 2011-01-31
Hi Guys,

It would appear I'm having an ongoing problem with my second "data" hard drive.

I have it set up so that on boot my second internal disk gets mounted to /home/michael/Data its formatted to FAT32 so that I can share it with my Window 7 partition.

Ever since I set this up the first time I've been having random niggily problems like not being able to change something on the drive to an executable and running it (I've had to copy it over to my home directory then run it from there).

Anyway so I tried using dropbox (stored on my data drive) to sync my Minecraft world to the cloud and everything went smoothly except the program goes to a black screen after login in. (At this point you're think "why isn't he asking this on the minecraft forums?")

I thought the problem was with my Data drive not having executable access so I started tweaking things in psydm and later in FSTAB and now my drive mounts as root but doesn't allow root to change any of the settings such as owner.

Could someone please step in and tell me how to mount the Data drive so I have all the same permissions as User as I do in my home directory.

I'm now comfortable using psydm and FSTAB so instructions for either would be fine.

Thanks

Grindboy

---

### Post by Morbius1 on 2011-01-31
Please post the output of the following command:
```
cat /etc/fstab
```

---

### Post by grindboy on 2011-01-31
Thanks for replying :-)

```
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                <mount point>     <type>  <options>                    <dump>  <pass>
proc                                       /proc               proc  nodev,noexec,nosuid          0  0  
# / was on /dev/sda5 during installation
UUID=6c13cb1c-fb15-4f62-a507-89d17dcd4555  /                   ext4  errors=remount-ro              0  1  
# swap was on /dev/sda6 during installation
UUID=86f734f0-0e74-444b-a14a-5c95036e7352  none                swap  sw                             0  0  
UUID=6732-CECC                             /home/michael/Data  vfat  relatime,errors=remount-ro           0  1  

```

---

### Post by Morbius1 on 2011-01-31
> UUID=6732-CECC                             /home/michael/Data  vfat  relatime,errors=remount-ro           0  1It should look like this:
```
 UUID=6732-CECC /home/michael/Data  vfat defaults,utf8,umask=007,uid=1000,gid=46 0 1
```umask=007 will allow read / write / execute permissions to owner and group.
uid=1000 will make you the owner.
gid=46 will make it so all local login users will also have r/w/e access to the mount point.

---

### Post by grindboy on 2011-01-31
Brilliant, works perfectly and solved the Minecraft problem.

Thanks Morbius

---

