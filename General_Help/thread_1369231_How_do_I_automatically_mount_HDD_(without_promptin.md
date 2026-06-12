---
title: "How do I automatically mount HDD (without prompting for password)"
date: 2009-12-31
forum: General Help
---

### Post by Eugene_Bondarenko on 2009-12-31
Hi,

I have a 1TB HDD with Linux and until recently I had another 1TB HDD with Windows. I formatted the windows HDD several minutes ago and now want to use it for storing movies and other similar stuff. However when I try accessing it, Ubuntu asks me to enter password. Is there any easy fix for this?

I also have a 1TB backup HDD that resides in USB box and it functions just like I want it to. When my Ubuntu loads, it is already mounted and no passwords are required to access it. I would like the former Windows HDD to function exactly like that. 

PS. Happy New Year!!! :mrgreen:

---

### Post by tom4everitt on 2009-12-31
All you need to do is to add a line to the file /etc/fstab. For me to tell you exactly what to write, I need to know what the file system is and if the hard drive is /dev/sdb1 or something else.

---

### Post by Eugene_Bondarenko on 2009-12-31
Thanks! GParted says that it is /dev/sdb and it has an entry 
/dev/sdb1 labeled "extended" which has a /dev/sdb5 ext4 sub-entry.

---

### Post by dcstar on 2009-12-31
> **Eugene_Bondarenko said:**
> Hi,

I have a 1TB HDD with Linux and until recently I had another 1TB HDD with Windows. I formatted the windows HDD several minutes ago and now want to use it for storing movies and other similar stuff. However when I try accessing it, Ubuntu asks me to enter password. Is there any easy fix for this?


Install the **pysdm** package and use that.

---

### Post by Rayve on 2009-12-31
Check out the thread linked in my signature about "How to fstab", which will tell you about mounting hard drives.  That will explain a lot and you can learn quite a bit as you do the steps yourself.  :)  If you have any questions from there, let us know.

---

### Post by Eugene_Bondarenko on 2009-12-31
Thanks, this helped! :)
Also I've noticed that when these HDDs get mounted, an undeletable icon gets created on the desktop. Is there any way to tell Ubuntu that I don't want these icons on the desktop?

---

### Post by Morbius1 on 2009-12-31
If your mount point is in /home or /media you will get a desktop icon

If your mount point is in /mnt or off the /  directory you will not get an icon. You will also not get a lising under 'Places" but that's easily fixed.

So if you don't want the icon change the mount point.

---

### Post by mc4man on 2009-12-31
The other way is** not to auto-mount at boot**, just access your drive from places when desired.

It's quite simple to remove the need to authenticate when mounting internal file-systems on karmic. ( lucid has already removed this unnecessary authentication.

---

### Post by tom4everitt on 2010-01-01
[http://nocostsoftware.blogspot.com/2008/05/using-ubuntus-gnome-configuration.html](http://nocostsoftware.blogspot.com/2008/05/using-ubuntus-gnome-configuration.html)

I'm pretty sure there's a gnome setting for whether mounted hard drives should be shown on the desktop or not.

---

### Post by Elfy on 2010-01-01
There is - /apps/nautilus/desktop - disable volumes visible 

But that means that cdroms/usb drives will not show there either.

I mount mine in /mnt and leave the show volumes enabled.

---

### Post by Eugene_Bondarenko on 2010-01-01
Thanks for your help, I did it!

---

### Post by Eugene_Bondarenko on 2010-01-03
I've just realized that the whole thing doesn't yet work perfectly. The hdd does get auto-mounted however it is owned by root and I can't do anything in it. What is the correct fix for this?

---

### Post by Morbius1 on 2010-01-03
Can you post your fstab please. In a terminal type** cat /etc/fstab**

---

### Post by Eugene_Bondarenko on 2010-01-03
Sure, thanks for your help!
```

eugene@eugene-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults               0  0  
# / was on /dev/sda3 during installation
UUID=67e42d9a-6ed4-4866-973b-1cbc044ec231  /              ext4         errors=remount-ro      0  1  
# /home was on /dev/sda5 during installation
UUID=8b7fc830-3543-41d4-9271-a35693c67600  /home          ext4         defaults               0  2  
# swap was on /dev/sda1 during installation
UUID=45fcba68-cf2a-4f7a-ac7f-20347c9a7026  none           swap         sw                     0  0  
# swap was on /dev/sdb9 during installation
UUID=47bea749-feae-4645-9b8c-5800b7de037f  none           swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0  
/dev/sdb5                                  /media/sdb5    ext4         defaults               0  0  
/dev/sdc1                                  /media/sdc1    ntfs         defaults               0  0  

```
The HDD with problem is sdb5.

---

### Post by Morbius1 on 2010-01-03
Sorry, for some reason I thought the problem was the ntfs partition.
Didn't you start this post with a problem with the ntfs partition?

Anyway if you really want to take possession of /media/sdbd you need to issue a chown command:

sudo chown -R eugene:eugene /media/sdb5

This will make you the owner of the mount point and all its contents.

[B][COLOR=Blue]This ( sdb5 ) is just a data partition right. If it's another linux OS the chown command will pretty much bork it.

[/COLOR][/B][COLOR=Blue][COLOR=black]You may need to do a chmod command as well but I don't know what your requirements are. Let me know if you need to alter the read /write permissions.[/COLOR][/COLOR][B][COLOR=Blue]
[/COLOR][/B]

---

### Post by Eugene_Bondarenko on 2010-01-03
LOL I've just did chown and came here with the intention to ask if the solution is good. Seeing that the fix is to do exactly chown makes me think that I am learning something :mrgreen:

Don't worry, that HDD doesn't have anything useful. At the current moment it's completely empty and soon it will simply be a place for storing movies.

---

