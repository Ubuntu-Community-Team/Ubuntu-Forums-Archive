---
title: "Data partition does not load automatically"
date: 2011-10-03
forum: General Help
---

### Post by emailadress on 2011-10-03
Hello everyone!

I am currently using my laptop with a ubuntu, a windows and a data partition. I linked the ubuntu menus (and most programs saving data while I use them [calibre, thunderbird, ...]) directly with the data partition. 

The problem is, that I have to manually open that partition once after I start up my laptop in order to be able to use all the links. This means that if I forget this, calibre for example will change the default library to a location on my Linux partition (which is very small) because it cannot access the data partition. The links in the 'Places' menu also don't show up. 

Its of course nothing major, once I opened the partition everything works fine. It is a nuisance, however. Must be easy to solve, no?

Thank you so much in advance!

Jakob

---

### Post by TeoBigusGeekus on 2011-10-03
You need to edit your fstab file (File System TABle).
Mount the partition and post us the output of
```
mount
sudo blkid
```
as well as the contents of your fstab file
```
gedit /etc/fstab
```
Don't forget to mention the name of the disk.

---

### Post by emailadress on 2011-10-04
Ok, thanks for the answer!

> jakob@jakob-laptop:~$ sudo blkid
[sudo] password for jakob: 
/dev/sda1: LABEL="System-reserviert" UUID="D22E5A162E59F447" TYPE="ntfs" 
/dev/sda2: UUID="9410A49210A47D3C" TYPE="ntfs" 
/dev/sda3: UUID="a2298750-0c4e-4a62-b447-00cc8fce7643" TYPE="ext4" 
/dev/sda5: UUID="08F0DE17F0DE0AB8" TYPE="ntfs" 
/dev/sda6: UUID="129c8ccc-a265-4ba8-b886-4ca2f44d518c" TYPE="swap" 
and:
> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=a2298750-0c4e-4a62-b447-00cc8fce7643 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=129c8ccc-a265-4ba8-b886-4ca2f44d518c none            swap    sw              0       0The device is called 08F0DE17F0DE0AB8 for some strange reason, if someone can tell me how to rename that to "D", that'd be amazing! ;-)

Best and thanks!
Jakob

p.s.: The file "System Reserviert" seems to be a fourth partition of 1 GB size which Windows created on its installation. I did not do that. I just created a swap partition as a fourth partition. The Swap and the Data partition are logical partitions while the Lunix, the Windows and this strange "System Reserviert" partitions are primary ones.

---

### Post by TeoBigusGeekus on 2011-10-04
Ok:
```
sudo mkdir /media/D
```
to create the partition's mount point.
```
sudo chown +R yourusername: /media/D
```
to become the owner of the mount point (replace yourusername with your user name - duh!!!)
```
gksu gedit /etc/fstab
```
add this line at the end of the file
```
UUID=08F0DE17F0DE0AB8 /media/D ntfs defaults 0 0
```
save and exit.
```
sudo mount -a
```
to force the system to mount all the partitions mentioned in fstab and you're done.

---

### Post by emailadress on 2011-10-04
Getting closer, thanks!

The renaming worked perfectly, thanks a ton for that! However, ubuntu still doesn't mount the partition automatically. I have to click on it once before it adds the links to D to my 'Places' drop down menu. Thunderbird can't access the partition either before I have done that.

So something didn't work with that 'mount -a' command... 

In any case, thanks so much for your help, Mr Geekus! ;-) Any more ideas?

Jakob

p.s.: This is what fstab looks like now, maybe you can find a problem there?

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=a2298750-0c4e-4a62-b447-00cc8fce7643 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=129c8ccc-a265-4ba8-b886-4ca2f44d518c none            swap    sw              0       0 
UUID=08F0DE17F0DE0AB8 /media/D ntfs defaults 0 0

---

### Post by TeoBigusGeekus on 2011-10-05
Can you reboot and check again?

---

### Post by emailadress on 2011-10-05
yes, I dried that but without success.

fstab:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=a2298750-0c4e-4a62-b447-00cc8fce7643 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=129c8ccc-a265-4ba8-b886-4ca2f44d518c none            swap    sw              0       0 
UUID=08F0DE17F0DE0AB8 /media/D ntfs defaults 0 0

---

### Post by emailadress on 2011-10-05
*ack*

I'm so stupid... I have to create the links again so that they link to D!

---

### Post by emailadress on 2011-10-05
And now it works!

Thanks so much for your help Geekus! And to know that the fstab file exists can also come in handy I recon! I am really amazed at the support one can get here. I always try to solve my problems via existing posts but sometimes I can't (like in this case) and then its just great to find someone here who can help me out!

Thank you very much!
Jakob

---

### Post by TeoBigusGeekus on 2011-10-05
You're welcome Jakob; feel free to ask again anytime :D

---

