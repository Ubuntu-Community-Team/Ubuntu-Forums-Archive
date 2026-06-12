---
title: "mount: mount point swap does not exist"
date: 2011-04-25
forum: General Help
---

### Post by alaa_rabea2020 on 2011-04-25
[LEFT]when i test errors by "sudo mount -a" i got this 

mount: mount point swap does not exist

after writing this command "sudo gedit /etc/fstab" ,,,, i got this

UUID=5148630128FE30C4 /media/Collection\0401 ntfs-3g defaults 0 0
UUID=FE4C11644C1118CB /media/Collection\0402 ntfs-3g defaults 0 0
UUID=6e73cf26-edcd-42b0-884c-e2686dd70d15 / ext3 defaults 0 1
UUID= swap swap sw 0 0
UUID=7DF3923D63A29C0E /media/Eng ntfs-3g defaults 0 0
UUID=492905577CF6BDDF /media/Software ntfs-3g defaults 0 0
/dev/sr0 swap udf,iso9660 defaults 0 0

anyone have solution for my issue ???[/LEFT]

---

### Post by alaa_rabea2020 on 2011-04-25
i made something but i don't know reality of it 

i replaced this 
/dev/sr0 swap udf,iso9660 defaults 0 0

with this
 /dev/sda3 swap swap defaults 0 0

and after applying this command "sudo mount -a" ,,,, i got nothing !!
and even the message that appeared on boot screen 
"error mounting swap press s to skip mount swap or press v to manual recovery." 

disappeared !!! 
what's ur opinion about this crazy one ???

---

### Post by WorMzy on 2011-04-25
/dev/sr0 is not your swap partition, it is a CD/DVD drive, so trying to mount it as swap is not a good idea.

```
UUID= swap swap sw 0 0
```
This is your swap partition's mount line, but it's missing a UUID value. You can use ```
sudo blkid -c /dev/null
``` to list all the UUIDs for your partitions, but you can use /dev/sda3 instead, as you have done in your above example.

Also, to open gedit with root privileges, _don't_ use "sudo gedit", use ```
gksu gedit
``` or ```
gksudo gedit
``` instead. You can mess up your home folder by using sudo for graphical apps, so don't do it.

---

### Post by alaa_rabea2020 on 2011-04-25
first of all thanks wormzy ....
secondly 
when i use ur codes ,,, i got blank text !! and there is nothing on it ?? 
> **WorMzy said:**
> 
Also, to open gedit with root privileges, _don't_ use "sudo gedit", use ```
gksu gedit
``` or ```
gksudo gedit
``` instead. You can mess up your home folder by using sudo for graphical apps, so don't do it.

there is little thing if u want t complete ur kindness ....
when i boot .... i have a flash red ubuntu wallpaper and one red and half line ....suddenly disappeared and after that sound of ubuntu with black screen for 4 seconds  .

is there is a way to get rid of all that ???

---

### Post by WorMzy on 2011-04-25
Those codes were just examples, to show that you should use gksu or gksudo when opening graphical apps; both of them will just open a blank document in gedit. If you want to edit your fstab again, instead of using "sudo gedit /etc/fstab" like you mentioned in your first post, you should use

```
gksudo gedit /etc/fstab
```

As for your start up problem, I don't know. Sounds like a plymouth issue, but I don't know anything about that. You might want to create a new topic about it.

---

