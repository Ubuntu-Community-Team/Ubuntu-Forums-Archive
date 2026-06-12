---
title: "mounting issues"
date: 2012-01-21
forum: General Help
---

### Post by tru infini on 2012-01-21
I am running Ubuntu 10.04
I have a hard drive that I use to keep all my stuff protected in case my primary which has my OS installed on it, decides to fail.
Along with all my stuff is my music library
Whenever I restart my computer, I have to open the hard drive to get my music program to see my library. If I log out and back in then It works fine but every time I reboot it's like something resets.
I thought it was a mounting issue so I installed pysdm and followed some instructions I found on a ubuntu tips and tricks article. made things slightly worse as I can't unmount the drive by right clicking. When I do I get this message
Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount /dev/sdb1 from /media/sdb1
but I can unmount it through pysdm
Is there any way to fix this problem and make so I don't have to open the hard drive myself to get my music program (and all other programs) to see it?
Much appreciated and if this is in the wrong section, feel free to move it to the correct one.

---

### Post by carranty on 2012-01-21
Have you included the drive in your fstab file?  If you have please post it here because I think there must be an error in it.  If not, the below link explains how to do it.  Once done the drive should automatically mount everytime you boot up.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Morbius1 on 2012-01-21
I don't understand the nature of the problem. 

You want to have the partition automount so you used PySDM. Now you want to be able to unmount it as a regular user? If you want it to automount why do you want to unmount it? The "only root can unmount" is not an error message it's a statement of fact. 

I'm confused.

---

### Post by raja.genupula on 2012-01-21
First uninstall that pysdm (better go for purging for complete removal). Then install it again, but this time be careful with configuration of it .

I hope this link can provide some more valuable inforamtion.
[http://ubuntuforums.org/archive/index.php/t-1309751.html](http://ubuntuforums.org/archive/index.php/t-1309751.html)

All the best.

---

### Post by tru infini on 2012-01-21
this is what my fstab file looks like, it is on Sdb1. any changes that could be made to this to fix it?

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda6 during installation
UUID=e8b8b14f-1769-4d02-920b-1d2f3d220b7f  /            ext4  defaults             0  1  
# swap was on /dev/sda7 during installation
UUID=70f2ad83-db48-411d-9e20-bb231ca20813  none         swap  sw                   0  0  
/dev/sdb1                                  /media/sdb1  ext3  errors=remount-ro    0  0  
/dev/sda1                                  /media/sda1  ntfs  defaults             0  0

---

### Post by tru infini on 2012-01-21
> **Morbius1 said:**
> I don't understand the nature of the problem. 

You want to have the partition automount so you used PySDM. Now you want to be able to unmount it as a regular user? If you want it to automount why do you want to unmount it? The "only root can unmount" is not an error message it's a statement of fact. 

I'm confused.


I thought psydm would be able to make so I wouldn't have to open Sdb1 every time I reboot my system. I don't recall it ever telling em I couldn't unmount a drive like that before (I may be wrong though) 
The main objective here is to be able to turn my computer on, and open and run my music program without having to open the drive where all my music is located first. maybe I don't need psydm, I'm not sure at this point.

---

### Post by carranty on 2012-01-21
> **tru infini said:**
> this is what my fstab file looks like, it is on Sdb1. any changes that could be made to this to fix it?

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda6 during installation
UUID=e8b8b14f-1769-4d02-920b-1d2f3d220b7f  /            ext4  defaults             0  1  
# swap was on /dev/sda7 during installation
UUID=70f2ad83-db48-411d-9e20-bb231ca20813  none         swap  sw                   0  0  
/dev/sdb1                                  /media/sdb1  ext3**  errors=remount-ro**    0  0  
/dev/sda1                                  /media/sda1  ntfs  defaults             0  0

Try replacing the second to last line with
```

/dev/sdb1      /media/sdb1  ext3 **defaults**    0  0  
```Also, it's better to identify drives by their UUID, rather than the /dev/sdb1 term.  To get the UUID simply mount the drive (by opening it with your file browser) and then enter the below into a terminal
```

sudo blkid | grep /dev/sdb1
```Then just copy and paste the UUID into your fstab.  For instance in my case

```
carranty@carranty-desktop ~/test $ sudo blkid | grep /dev/sdb1
/dev/sdb1: UUID="4f754843-a651-4329-b8b7-1b8a9f03a861" TYPE="ext3" 
```Therefore in my fstab the line would be 

```
 UUID=4f754843-a651-4329-b8b7-1b8a9f03a861 /media/sdb1  ext3 defaults    0  0
```Note that you do **not** copy the quotation marks.

---

### Post by tru infini on 2012-01-21
That did it. much appreciated.
I'll change the thread to [solved]

---

