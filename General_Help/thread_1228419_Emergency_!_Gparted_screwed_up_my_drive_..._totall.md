---
title: "Emergency ! Gparted screwed up my drive ... totally !! It says its no longer ntfs"
date: 2009-07-31
forum: General Help
---

### Post by zonemikel on 2009-07-31
Ok i have two hdd's in my system one was failing so i decided to move linux to the other hdd. 

This hd was 460gigs and had about 100gigs of freespace. So I loaded up the ubuntu live cd and started Gparted to partition some free space for the new installation. Gparted gave me a error and would not "resize" the drive. So i then used the installation cd and told it to repartition the drive using the free space, it got stuck on the "partitioning" part, never went past 0% and eventually told me it could not do it. 

Now i can no longer mount this drive. When i try and mount it, it says something like 
[PHP]The device '/dev/sdb' doesn't seem to have a valid NTFS.[/PHP]
or 
[PHP]Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
[/PHP]

And windows says "this drive does not seem to be formatted would you like to format it now ?" 

This drive was packed full of a lifetime worth of accumulated stuff, family pictures and dvds and such that cant be replaced. 

Is there any way i can fix it ?

---

### Post by merlinus on 2009-07-31
Try testdisk and photorec.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by SuaSwe on 2009-07-31
Possible data recovery solution that may be helpful should all else fail:

[[COLOR="Blue"]https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image[/COLOR]]("https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image")

---

