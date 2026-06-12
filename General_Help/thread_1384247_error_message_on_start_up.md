---
title: "error message on start up"
date: 2010-01-18
forum: General Help
---

### Post by shaunfromthewildwoods on 2010-01-18
macbook, using Ubuntu 9.10

get this before login:

one or more of the mounts listed in/etc/fstab cannot be mounted: swap = waiting f UUID = d4d71cbe-bcdd-4deb-85ae-83059czf02e
Press ESC to enter a recovery shell

once pushing ESC i log in and everything works fine,

some older threads on this allude that it may be just an aesthetic bug,

anyone know more about this?

---

### Post by wojox on 2010-01-18
Post:

```
sudo blkid
```

```
cat /etc/fstab
```

back up and let's have a look.

---

### Post by shaunfromthewildwoods on 2010-01-18
heres the output from the commands you supplied

  	 	 	 	 	 	  /dev/sda1: LABEL="EFI" UUID="3F3C-1AF6" TYPE="vfat"  
 /dev/sda2: UUID="561843e1-912a-3a37-a732-179538368381" LABEL="Macintosh HD" TYPE="hfsplus"  
 /dev/sda3: LABEL="BOOTCAMP" UUID="302E-13F3" TYPE="vfat"  
 /dev/sda5: UUID="63a4100d-47ed-402e-b5b1-9fa447580908" TYPE="ext4"  
 /dev/sda6: UUID="b896dfca-dd4e-4c10-bcce-f474e863304e" TYPE="swap"  
 /dev/sda8: UUID="f4142bc2-f4d1-4736-8b6b-8dad646693f9" TYPE="ext4"  
 /dev/sda9: UUID="5bb0f98f-bab8-4929-9767-4fd952ef3723" TYPE="swap"  
 /dev/sda11: UUID="e2719bec-4a43-4c22-b7cf-cf635daafc2f" TYPE="ext4"  
 

 

 # /etc/fstab: static file system information. 
 # 
 # Use 'blkid -o value -s UUID' to print the universally unique identifier 
 # for a device; this may be used with UUID= as a more robust way to name 
 # devices that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    defaults        0       0 
 # / was on /dev/sda11 during installation 
 UUID=e2719bec-4a43-4c22-b7cf-cf635daafc2f /               ext4    errors=remount-ro 0       1 
 # swap was on /dev/sda12 during installation 
 UUID=d4d71cbe-bcdd-4deb-85ae-83059cd7f02e none            swap    sw              0       0 
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by wojox on 2010-01-18
Okay if you look at fstab you'll see it's looking for swap on 

```
UUID=d4d71cbe-bcdd-4deb-85ae-83059cd7f02e
```

On blkid it's actually on:

```
UUID=5bb0f98f-bab8-4929-9767-4fd952ef3723
```

So you'll need to edit fstab and swap UUID with:

```
UUID=5bb0f98f-bab8-4929-9767-4fd952ef3723
```

```
gksudo gedit /etc/fstab
```

Save and reboot.

---

### Post by rnerwein on 2010-01-18
hi
but this serious - where does the wrong entry comes from. just a hint to use blkid to be sure what you see is what you got. do: blkid -c /dev/null  otherwise blkid reads from the cache file and this is not nessesary the actual state of your configuration.
ciao

---

### Post by shaunfromthewildwoods on 2010-01-18
Wojox, 

problem solved!


 thank you so much for your time,

---

### Post by arubislander on 2010-01-18
> **rnerwein said:**
> hi
but this serious - where does the wrong entry comes from. just a hint to use blkid to be sure what you see is what you got. do: blkid -c /dev/null  otherwise blkid reads from the cache file and this is not nessesary the actual state of your configuration.
ciao

The wrong entry probably results from installing another OS that reformatted the swap partition.

---

### Post by PCZahra on 2010-01-31
Dell 1525n with dist-upgrade

[QUOTE="blkid"]/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-061E" TYPE="vfat" 
/dev/sda2: LABEL="OS" UUID="2B88-E180" TYPE="vfat" 
/dev/sda3: UUID="ec976162-02f1-44f0-9392-ea15e7d30cbe" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" [/QUOTE]


[QUOTE="/etc/fstab"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ec976162-02f1-44f0-9392-ea15e7d30cbe /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=00195ad0-31b4-41a8-8955-d8cfeecf6223 none            swap    sw              0       0
/dev/sda2       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
[/QUOTE]

I didn't write mine down, but I'm pretty sure it's complaining about swap. Do I just replace the UUID in fstab with /dev/sda5 ?

---

