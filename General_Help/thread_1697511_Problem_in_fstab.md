---
title: "Problem in fstab"
date: 2011-02-28
forum: General Help
---

### Post by RBruiser on 2011-02-28
So, recently I began getting an error message when I booted that read

"The disk drive for on is not ready or is not present"

I just always pressed "s" but I'm getting fairly sick not having DVD's play so, I followed some thread advice and tried to delete a UUID I thought was the right one, without knowing that you '#" it out, I simply deleted it.  Now, this is what I have:

  	 	 	 	p { margin-bottom: 0.08in; }  # /etc/fstab: static file system information. 
 # 
 # Use 'blkid -o value -s UUID' to print the universally unique identifier 
 # for a device; this may be used with UUID= as a more robust way to name 
 # devices that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    nodev,noexec,nosuid 0       0 
 # / was on /dev/sda1 during installation 
 #               ext4    errors=remount-ro 0       1 
 # swap was on /dev/sda5 during installation 
 # UUID=a362b091-54b2-4df9-a35d-c038c7de0cde none            swap    sw              0       0 
  
 /dev/sr1 on /media/WD SmartWare type udf (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,noauto) 
 

I am the opposite of computer savvy.  I use these forums to cut and paste things into my terminal and thats about it.  Help?

---

### Post by Hedgehog1 on 2011-02-28
> **RBruiser said:**
> 
 # 
 # Use '**_[COLOR="Red"]blkid -o value -s UUID[/COLOR]_**' to print the universally unique identifier 
 # for a device; this may be used with UUID= as a more robust way to name 
 # devices that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    nodev,noexec,nosuid 0       0 
 # / was on /dev/sda1 during installation 
 #               ext4    errors=remount-ro 0       1 
 # swap was on /dev/sda5 during installation 
 # UUID=a362b091-54b2-4df9-a35d-c038c7de0cde none            swap    sw              0       0 
  
 /dev/sr1 on /media/WD SmartWare type udf (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,noauto) 
 


Hey there!

To see the UUID for all your drives, the highlighted command:

```
sudo blkid -o value -s UUID
```

Will print out the UUID's for you.

Do you think you can put them back OK into the fstab file?

***The Hedge***

:KS

---

### Post by RBruiser on 2011-02-28
Thanks for the code!

I assume I could copy and paste them in a line break format?

The problem is, then I still have to fix the disk mounting error...

---

### Post by RBruiser on 2011-02-28
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
#               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
# UUID=a362b091-54b2-4df9-a35d-c038c7de0cde none            swap    sw              0       0
# 366d3561-f5f9-484c-a95f-51f403e50d61
# a362b091-54b2-4df9-a35d-c038c7de0cde
/dev/sr1 on /media/WD SmartWare type udf (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,noauto)

Not sure how to lay them in besides this...

---

### Post by RBruiser on 2011-02-28
The only concrete solution I can find is this:

1.Open your terminal by ctrl+alt+t or Applications –> Accessories –> Terminal
 2.use the below command in terminal,
 **gksudo gedit /etc/fstab**
 3.A file will open,find /boot line.It will look something like this ,
 ** /dev/sda2     /boot ext4 defaults    0   0**
 4.Now open another terminal and use the below command ,
 ** ls -l /dev/disk/by-uuid**
 5.Now find the UUID for /dev/sda2 and replace the below line in fstab ,
 ** /dev/sda2     /boot ext4 defaults    0   0**
 ** as**
 ** UUID=a647ea33-74ee-4123-84bf-7edc32e2e39b /boot ext4 defaults 0 0**
 ** [Replace the UUID number with your number]**
 6.save the file and restart the system.It will work fine.The same solution can be addressed for /dev/sda mounting problem.


Which would be great, barring step 5 as I don't have that anymore.

---

### Post by Hedgehog1 on 2011-02-28
> **RBruiser said:**
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
#               ext4    errors=remount-ro 0       1
[COLOR="Red"]UUID=366d3561-f5f9-484c-a95f-51f403e50d61  /                 ext4  errors=remount-ro    0  1[/COLOR]
# swap was on /dev/sda5 during installation
[COLOR="Lime"]UUID=a362b091-54b2-4df9-a35d-c038c7de0cde none            swap    sw              0       0[/COLOR]

/dev/sr1 on /media/WD SmartWare type udf (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,noauto)


I have added the line in RED

a362b091-54b2-4df9-a35d-c038c7de0cde is your swap, you can uncomment it out (GREEN).

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-01
> **RBruiser said:**
> The only concrete solution I can find is this:

1.Open your terminal by ctrl+alt+t or Applications –> Accessories –> Terminal
 2.use the below command in terminal,
 **gksudo gedit /etc/fstab**
 3.A file will open,find /boot line.It will look something like this ,
 ** /dev/sda2     /boot ext4 defaults    0   0**
 4.Now open another terminal and use the below command ,
 ** ls -l /dev/disk/by-uuid**
 5.Now find the UUID for /dev/sda2 and replace the below line in fstab ,
 ** /dev/sda2     /boot ext4 defaults    0   0**
 ** as**
 ** UUID=a647ea33-74ee-4123-84bf-7edc32e2e39b /boot ext4 defaults 0 0**
 ** [Replace the UUID number with your number]**
 6.save the file and restart the system.It will work fine.The same solution can be addressed for /dev/sda mounting problem.


Which would be great, barring step 5 as I don't have that anymore.

You were on the right track here.  You would have made it there without me. Eventually. 

I always learn the most when I break something (or I help someone who has broken something).

I wont name any names....

---

### Post by RBruiser on 2011-03-01
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
#               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
# UUID=a362b091-54b2-4df9-a35d-c038c7de0cde none            swap    sw              0       0
UUID=366d3561-f5f9-484c-a95f-51f403e50d61 / ext4 errors=remount-ro 0 1
UUID=a647ea33-74ee-4123-84bf-7edc32e2e39b /boot ext4 defaults 0 0
/dev/sr1 on /media/WD SmartWare type udf (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,noauto)

Well, I don't think I am on the right track though hopefully we are getting there!

This got me to "the disk drive for /boot is not ready or present yet"

So, at least something changed.

---

### Post by Hedgehog1 on 2011-03-01
> **RBruiser said:**
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
#               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
# UUID=a362b091-54b2-4df9-a35d-c038c7de0cde none            swap    sw              0       0
UUID=366d3561-f5f9-484c-a95f-51f403e50d61 / ext4 errors=remount-ro 0 1
**[COLOR="Red"]UUID=a647ea33-74ee-4123-84bf-7edc32e2e39b /boot ext4 defaults 0 0[/COLOR]**
/dev/sr1 on /media/WD SmartWare type udf (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,noauto)

Well, I don't think I am on the right track though hopefully we are getting there!

This got me to "the disk drive for /boot is not ready or present yet"

So, at least something changed.

Unless you have a separate partition for your '/boot' directory, you don't need that line.

Most folks either keep all data in '/', or split it between '/' for the OS and a second partition for '/home'

What is your layout?

---

