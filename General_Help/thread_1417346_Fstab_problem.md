---
title: "Fstab problem"
date: 2010-02-27
forum: General Help
---

### Post by sigurnjak on 2010-02-27
As of yesterday i am having problem seeing my external usb drive . When i try using disk utility i get this message :
Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 14 in /etc/fstab is bad
[mntent]: line 15 in /etc/fstab is bad
[mntent]: line 16 in /etc/fstab is bad
[mntent]: line 17 in /etc/fstab is bad
mount: only root can mount /dev/sdc1 on /media/sdc1

This is my current fstab :
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults               0  0  
# / was on /dev/sda1 during installation
UUID=603b3447-1711-4cb1-b444-56d440b390c1  /              ext4         errors=remount-ro      0  1  
# swap was on /dev/sda5 during installation
UUID=27a2c7d5-90f8-409d-8e9e-fd54f0e5a5c2  none           swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0  
/dev/sdb1                                  /media/Vista drive   ntfs         defaults               0  0  
/dev/sdc1                                  /media/320 gb drive  ext3         defaults               0  0  
/dev/sdc1                                  /media/320 GB drive  ext3         errors=remount-ro,users,user           0  0  
/dev/sdb1                                  /media/Vista drive   ntfs         nls=iso8859-1,ro,users,umask=000,user  0  0  
/dev/sdc1                                  /media/sdc1    ext3         defaults               0  0 


 
BTW my 320 gig hd is now formated to ntfs , but i can format it to anything if neede , it is blank right now .
Wht do i do now ?

---

### Post by cong06 on 2010-02-27
Did you go in and edit the file?
First off, as you found out with line 18 (which is correct), you need to have no spaces in the mounted path.
This is why fstab is throwing errors.

You probably also shouldn't have the same drive mounted twice.

It looks like you have sdb1 mounted twice (14, and 17) and sdc1 mounted 3 times (15, 16, and 18)

So, just make the folders without spaces, and fix up your fstab, and you're good.

---

### Post by SecretCode on 2010-02-27
It should work if you escape the spaces - e.g. 
```
/dev/sdb1 /media/Vista drive ntfs defaults 0 0
``` 
becomes
```
/dev/sdb1 /media/Vista\ drive ntfs defaults 0 0
```

But creating directory names without spaces will be better.

---

### Post by sigurnjak on 2010-02-27
So if i comment out those line i would be good to go , like this :



# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults               0  0  
# / was on /dev/sda1 during installation
UUID=603b3447-1711-4cb1-b444-56d440b390c1  /              ext4         errors=remount-ro      0  1  
# swap was on /dev/sda5 during installation
UUID=27a2c7d5-90f8-409d-8e9e-fd54f0e5a5c2  none           swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0  
/dev/sdb1                                  /media/Vista drive   ntfs         defaults               0  0  
/dev/sdc1                                  /media/320 gb drive  ext3         defaults               0  0  
#/dev/sdc1                                  /media/320 GB drive  ext3         errors=remount-ro,users,user           0  0  
#/dev/sdb1                                  /media/Vista drive   ntfs         nls=iso8859-1,ro,users,umask=000,user  0  0  
#/dev/sdc1                                  /media/sdc1    ext3         defaults               0  0

---

### Post by SecretCode on 2010-02-27
No, you still have spaces in the directory names.

---

### Post by sigurnjak on 2010-02-27
I must be slow today ! ): 
Is this correct :
/dev/sdb1                                  /media/Vista\ drive   ntfs         defaults               0  0  
/dev/sdc1                                  /media/320 gb\ drive  ext3         defaults               0  0

---

### Post by SecretCode on 2010-02-27
Close - you still have a space in '320 gb'!

---

### Post by sigurnjak on 2010-02-27
So like this :


/dev/sdb1 /media/Vista\ drive ntfs defaults 0 0
/dev/sdc1 /media/320gb\ drive ext3 defaults 0 0

Gosh , this is embarrassing   already  ! (:

---

### Post by SecretCode on 2010-02-27
That will work, as long as you've created directories with those names (why not just create directories without spaces? :))

---

### Post by sigurnjak on 2010-02-27
Here is a screen shot of my media folder , is this correct ?

---

### Post by sisco311 on 2010-02-27
In fstab, spaces are filed separators, you can't use a backslash or quotes to escape them. 

You have to convert a space to its octal representation: "\040".

i.e.: Vista drive => Vista**\040**drive.

---

### Post by sigurnjak on 2010-02-27
O.K. this is becoming way over my head . 

Here is my current fstab : 


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults               0  0  
# / was on /dev/sda1 during installation
UUID=603b3447-1711-4cb1-b444-56d440b390c1  /              ext4         errors=remount-ro      0  1  
# swap was on /dev/sda5 during installation
UUID=27a2c7d5-90f8-409d-8e9e-fd54f0e5a5c2  none           swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0  
/dev/sdb1                                  /media/Vista\ drive   ntfs         defaults               0  0  
/dev/sdc1                                  /media/320gb\ drive  ext3         defaults               0  0  
#/dev/sdc1                                  /media/320 GB drive  ext3         errors=remount-ro,users,user           0  0  
#/dev/sdb1                                  /media/Vista drive   ntfs         nls=iso8859-1,ro,users,umask=000,user  0  0  
#/dev/sdc1                                  /media/sdc1    ext3         defaults               0  0  

Could someone fix it for me so i can safely reboot  and mount my usb drive , please .  
So far  i am thinking to just reinstall whole thing , but i would rather learn how to fix it . I apologize if i sound grumpy , i am just scarred of loosing my stuff in ubuntu and now i can not mount my backup drive .

---

### Post by sisco311 on 2010-02-27
No problem. :)

```
/dev/sdb1 /media/Vista**\040**drive ntfs defaults 0 0 
/dev/sdc1 /media/320gb**\040**drive ext3 defaults 0 0
```

You don't have to reboot. 

Create the mount points if they don't exist:
```
sudo mkdir "/media/Vista drive"
sudo mkdir "/media/320gb drive"
```
and mount the partitions mentioned in fstab:
```
sudo mount -a
```

---

### Post by sigurnjak on 2010-02-27
Gosh darn it ,i am having a bad day ! 

I just suffered some brief power outage  as i applied your fix . 
So naturally my pc rebooted .  Now my vista drive mounted automatically and showed up on a desktop but not 320 gb drive . It also did not apear in my places bar  ( btw 320 gig  is ntfs drive  , if it makes any difference ) .
Also when i plugged id 8 gig thumbdrive , nothing happened  . I am sorry to bother you this much folks and i apologize , but where do i go from here . Should i format 320 gig  to ext4 just to make it more friendly with ubuntu .

---

### Post by cong06 on 2010-03-01
> **sigurnjak said:**
> Gosh darn it ,i am having a bad day ! 

I just suffered some brief power outage  as i applied your fix . 
So naturally my pc rebooted .  Now my vista drive mounted automatically and showed up on a desktop but not 320 gb drive . It also did not apear in my places bar  ( btw 320 gig  is ntfs drive  , if it makes any difference ) .
Also when i plugged id 8 gig thumbdrive , nothing happened  . I am sorry to bother you this much folks and i apologize , but where do i go from here . Should i format 320 gig  to ext4 just to make it more friendly with ubuntu .

Well... while formatting ext2, ext3, ext4 would be useful, it wouldn't interact with Windows very well. So if you're not using windows, it wouldn't be a bad idea (of course you'll need to **back up your data first**).

That being said, it shouldn't be *too* hard to get your ntfs partition to work if you're interested in investing a bit more time.

Looking over your fstab (or the other guys's suggestion for your fstab) I see this:
```
/dev/sdc1 /media/320gb\040drive ext3 defaults 0 0
```
You said it was ntfs, but here it's listed as ext3. You'll want to fix that.
Maybe also print your whole fstab to confirm.

Just one more suggestion. I'd suggest you switch from "/dev/sdXX" format in the start to "UUID=...."
With the current setup if one of the disks loads before the other, the "/dev/sdXX" format will change, and they'll get mounted to different locations.
With UUID, they get mounted based off some kind of Hard drive identification.

Just send us the output of:
```

ls -al /dev/disk/by-uuid/

```

---

### Post by sigurnjak on 2010-03-01
Hi there cong06 ! Thanks for your advice , albeit  a little too late . Since my last post i fell down the icy stairs and hurt my back  so i could not follow up on my problem . Since i had more time on my hands and was grumpy  i just used my recent backup via remastersys from 2 weeks ago  and reinstalled whole damn thing . I had my stuff backed up via Vista  a while back and i am back in business .  
 I guess this  was a lesson and i did learn something about Linux , but not by choice but from necessity . 
Thanks to all who offered help and advice !

---

