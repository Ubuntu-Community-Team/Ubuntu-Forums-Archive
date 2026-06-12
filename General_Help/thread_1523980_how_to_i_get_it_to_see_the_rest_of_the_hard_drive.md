---
title: "how to i get it to see the rest of the hard drive"
date: 2010-07-04
forum: General Help
---

### Post by cdoublejj on 2010-07-04
It's not a bios limit. I have dual boot with 98se so it's a fat32 not ntfs like most guides talk about. how do i get xubuntu 9.04 to see the my 98se partition i know it's /dev/sda1 but, then again isn't the whole hard drive /dev/sda1 i only have 1 hdd since it is a laptop.

---

### Post by VCoolio on 2010-07-04
All partitions have their own number in /dev. Try the following in a terminal: 
```
sudo mount /dev/sda1 /media/disk
```
Make sure the folder where you mount to exists (else do: "sudo mkdir /media/disk"). Do 'man mount' to read more about it.

---

### Post by cdoublejj on 2010-07-04
will it stay mounted even after reboot?

---

### Post by Jose Catre-Vandis on 2010-07-04
No you will have to make an entry in /etc/fstab. Create a mount point and then make the entry, something like this:

```

sudo mkdir /media/Win98

then for fstab:

sudo nano /etc/fstab

add this:

/dev/sda1 /media/Win98 vfat default 0 0
```

If you want to clever you can substitute the UUID for /dev/sda1. To find out what it is do this:

```
sudo blkid
```

then you fstab line will look something like this (with your own number):

```
UUID=05AAD3F55A0B9BDA /media/Win98 vfat default 0 0
```

---

### Post by cdoublejj on 2010-07-04
it doesn't mount after restart maybe the number is required? i'll double check.

---

### Post by cdoublejj on 2010-07-06
it doesn't work even if i use the uuid after reboot the folder is empty

---

### Post by Jose Catre-Vandis on 2010-07-07
But
```
sudo mount /dev/sda1 /media/Win98
```
works?

---

### Post by cdoublejj on 2010-07-07
yes it does work thats how i have been using it since it doesn't mount after boot. does it matter that instead of win98 i made folder called 98SE?

UUID=xxxx-xxxx /media/98SE vfat default 0 0
would changing vfat to fat32 do anything? also would adding ,rw make so i can delete files?

---

### Post by Jose Catre-Vandis on 2010-07-08
vfat is the correct filesystem under linux for fat32

Try expanding your fstab line:
```
UUID=XXXXXXXXXXXXXX /media/98SE vfat auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
```
{use your UUID}
and have a read of [this thread]("http://ubuntuforums.org/showthread.php?t=283131"):

---

### Post by Morbius1 on 2010-07-08
Excuse the interruption, tiny typo at the end:
> dmask=027,fmask=1 37 0 0Should be:
> dmask=027,fmask=137 0 0

---

### Post by cdoublejj on 2010-07-08
IT LIVES!!!! that seems to have done the trick. Thank you guys. 1 more thing to mark off the list.

 :guitar:

---

