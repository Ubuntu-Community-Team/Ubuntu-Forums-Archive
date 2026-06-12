---
title: "no space"
date: 2009-10-04
forum: General Help
---

### Post by shaullx on 2009-10-04
i've installed ubuntu jaunty on my acer aspire one netbook
on the partition manager i've selected something that mix it with windows
now i cant download anything because i get the error that there is no space left
im trying to resize the partition but no luck so far
here is a screenshot from GParted(see attachment)
i want to format the entire hdd to have only linux and another partition for music and stuff like that
i can't use the liveCD because my netbook doesnt have a cdrom and i cant use live USB because i can't download the image 
so any help would be appreciated:)

---

### Post by 3rdalbum on 2009-10-04
You can't modify the Linux partition from within a system running on that partition; so you must find a way to run a live CD or live USB. Borrow someone's external drive maybe?

And then when you do, it would be better to just reinstall Ubuntu to use the whole drive (because you won't be able to resize that big light-blue Extended partition anyway).

---

### Post by SuperSonic4 on 2009-10-04
Why not delete some stuff? Like the package cache

---

### Post by snowpine on 2009-10-04
Not your fault... there is a major bug in the Ubuntu installer that sets the default partition size to 2.3gb (much too small). 

You need to reboot using a Live CD or Live USB, then run gparted from a live session. I recommend 8gb or larger. Good luck! :)

---

### Post by shaullx on 2009-10-04
> **snowpine said:**
> Not your fault... there is a major bug in the Ubuntu installer that sets the default partition size to 2.3gb (much too small). 

You need to reboot using a Live CD or Live USB, then run gparted from a live session. I recommend 8gb or larger. Good luck! :)

i cant download the Live USB gparted either.. 
no space because tmp folder is at the root partition
i tried to mount the usb device as tmp but now whenever i try to run anything i just get the error:
 (firefox:5781): WARNING **: Wrong permissions for /tmp/ ........
i tried to change permissions using "chmod 777 /tmp/"
but no luck there

---

### Post by drs305 on 2009-10-04
As snowpine says, it's a bug that unfortunately has not yet been fixed. I've written two posts about it.

You have two options - reinstall and do things a bit differently in Step 4 (Partitioning) or try to resize the / partition.

2.5 GB REINSTALL OR REPARTITION

If you have a 2.5 GB partition and want to reinstall:
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

If you have a 2.5 GB partition and want to resize the partition:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by SuperSonic4 on 2009-10-04
> **snowpine said:**
> Not your fault... there is a major bug in the Ubuntu installer that sets the default partition size to 2.3gb (much too small). 

You need to reboot using a Live CD or Live USB, then run gparted from a live session. I recommend 8gb or larger. Good luck! :)

*ignore me*

---

### Post by shaullx on 2009-10-04
> **drs305 said:**
> As snowpine says, it's a bug that unfortunately has not yet been fixed. I've written two posts about it.

You have two options - reinstall and do things a bit differently in Step 4 (Partitioning) or try to resize the / partition.

2.5 GB REINSTALL OR REPARTITION

If you have a 2.5 GB partition and want to reinstall:
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

If you have a 2.5 GB partition and want to resize the partition:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

im unable to resize the root partition
i dont have the option of resize

---

### Post by snowpine on 2009-10-04
> **shaullx said:**
> im unable to resize the root partition
i dont have the option of resize

You have to reboot your system from a Live CD/Live USB... you can't resize a mounted partition, just like you can't change the tires on your car while you're driving it. :)

---

### Post by grturner on 2009-10-04
here is a stupid idea. you said you have a dual boot so What is stopping you from booting into windows, and creating the ubuntu usb boot drive?

---

### Post by drs305 on 2009-10-04
> **shaullx said:**
> im unable to resize the root partition
i dont have the option of resize

If you want to try to resize the / partition, follow the instructions of the link I provided. If you run into problems we can sort it out here.

---

