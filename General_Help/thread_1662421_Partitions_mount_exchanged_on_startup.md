---
title: "Partitions mount exchanged on startup"
date: 2011-01-08
forum: General Help
---

### Post by wkcchampion on 2011-01-08
Hello buddies,
Ii'm encountering this weird issue

I have Ubuntu 10.10 Maverick Meerkat on a quite old desktop PC,  up-to-date. 
I have two hard disks. On the first one, there are installed both WinXP and Ubuntu, while the second one is just for my personal stuff.

I installed the program named Storage Device Manager. This allows me to automatically mount the 2nd hard disk and the WinXP partition of the 1st HD as Ubuntu starts.

I expect them to be assigned as the following:

[LIST]
[*]\dev\sda1 --> 1st HD, WinXP partition
[*]\dev\sdb1 --> 2nd HD
[/LIST]
Now, the problem is that sometimes... they get inverted! :confused:
I mean, at random intervals, Ubuntu assigns *sda1* to the 2nd HD and *sdb1* to the 1st one (WinXP partition).
This doesn't always happen, some boots go the right way, others the wrong one. I do nothing else then powering up the computer and logging in. 
This is a nuisance, because if the partitions mount inverted, my MP3 list gets screwed and i have to reboot, hoping that the HDs mount correctly.

I have Ubuntu 10.10 Netbook edition on my Asus netbook and this doesn't happen there.

Any ideas?

Thank you

---

### Post by tredegar on 2011-01-08
Please post the output of **cat /etc/fstab** from the desktop PC

---

### Post by wkcchampion on 2011-01-08
> **tredegar said:**
> Please post the output of **cat /etc/fstab** from the desktop PC

Hi, here it is

marco@casa:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid               0  0  
# / was on /dev/sda5 during installation
UUID=25e8016f-636d-4f33-b6fe-be00a7121cb0  /               ext4  defaults                          0  1  
# swap was on /dev/sda6 during installation
UUID=0642c2f8-b02f-4f81-b017-028c89b2421b  none            swap  sw                                0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8          0  0  
 
/dev/sdb1                                  /media/sdb1     ntfs  nls=iso8859-1,ro,users,umask=000  0  0  
/dev/sda1                                  /media/sda1     ntfs  nls=iso8859-1,ro,users,umask=000  0  0

---

### Post by tredegar on 2011-01-08
Thank you.

"Storage Device Manager" has made a mess of your fstab

You need to change these lines 
```
/dev/sdb1 /media/sdb1 ntfs nls=iso8859-1,ro,users,umask=000 0 0
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,users,umask=000 0 0
```
not to use **/dev/sd??** but to use UUID

In a terminal give the command **blkid** This will list your disk partitions and their UUIDs. Make a note of the UUIDs for **/dev/sda1** and **/dev/sdb1**

Now edit your fstab
```
sudo nano /etc/fstab
```
Replace **/dev/sdb1** with the UUID of **/dev/sdb1**
Same for **/dev/sda1**

So now the lines look something like this:
```
UUID=ECD4F00BD4EFD5BC  /media/sdb1 ntfs nls=iso8859-1,ro,users,umask=000 0 0
UUID=4C7AD7C27AD7A74C  /media/sda1 ntfs nls=iso8859-1,ro,users,umask=000 0 0
```
Save the changes.

Reboot, and the mountpoints should be stable.

---

### Post by wkcchampion on 2011-01-08
mmm... if I give the command **blkid**, nothing happens.

---

### Post by tredegar on 2011-01-08
Maybe you need to run it as root: **sudo blkid**
On 10.04, it runs as a normal user

---

### Post by wkcchampion on 2011-01-08
> **tredegar said:**
> Thank you.

"Storage Device Manager" has made a mess of your fstab

You need to change these lines 
```
/dev/sdb1 /media/sdb1 ntfs nls=iso8859-1,ro,users,umask=000 0 0
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,users,umask=000 0 0
```not to use **/dev/sd??** but to use UUID

In a terminal give the command **blkid** This will list your disk partitions and their UUIDs. Make a note of the UUIDs for **/dev/sda1** and **/dev/sdb1**

Now edit your fstab
```
sudo nano /etc/fstab
```Replace **/dev/sdb1** with the UUID of **/dev/sdb1**
Same for **/dev/sda1**

So now the lines look something like this:
```
UUID=ECD4F00BD4EFD5BC  /media/sdb1 ntfs nls=iso8859-1,ro,users,umask=000 0 0
UUID=4C7AD7C27AD7A74C  /media/sda1 ntfs nls=iso8859-1,ro,users,umask=000 0 0
```Save the changes.

Reboot, and the mountpoints should be stable.

Done it. If I still have problems, I'll post back! Thank you! :KS

---

### Post by wkcchampion on 2011-01-23
Hi, I noticed a further related issue. The mounted hard disk are property of Root and therefore they are in read-only. Ubuntu doesn't allow me to change the properties to read and write. :(

Any way to solve this? I'd like to be able to read and write files from oen of the two HDs

---

### Post by tredegar on 2011-01-23
> Any way to solve this? I'd like to be able to read and write files from oen of the two HDs 

Change your /etc/fstab to look like this:
```
UUID=*whatever-it-is*  /media/sdb1 ntfs-3g defaults
UUID=*whatever-it-is*  /media/sda1 ntfs-3g defaults
```
The **ntfs** module does not allow write access, **ntfs-3g** does.
Also, change the permissions of the mountpoints:
```
sudo chmod 777 /media/sda1  /media/sdb1
```
Reboot.

Better?

---

### Post by wkcchampion on 2011-01-23
> **tredegar said:**
> Change your /etc/fstab to look like this:
```
UUID=*whatever-it-is*  /media/sdb1 ntfs-3g defaults
UUID=*whatever-it-is*  /media/sda1 ntfs-3g defaults
```The **ntfs** module does not allow write access, **ntfs-3g** does.
Also, change the permissions of the mountpoints:
```
sudo chmod 777 /media/sda1  /media/sdb1
```Reboot.

Better?

I changed the Fstab file:

```
UUID="CE7426A574268FEF"                   /media/sdb1     ntfs-3g  nls=iso8859-1,ro,users,umask=000  0  0  
UUID="4AB436A9B4369801"                   /media/sda1     ntfs-3g  nls=iso8859-1,ro,users,umask=000  0  0  
```

Then I ran that command both before and after reboot. Both HDs are still in Read-only. :shock:

---

### Post by vanadium on 2011-01-23
```

UUID="CE7426A574268FEF"                   /media/sdb1     ntfs-3g  nls=iso8859-1,ro,users,umask=000  0  0  

```
You need to remove "ro", which indicates to mount the volume "read only".

You *can* specify "ntfs" rather than "ntfs-3g" because ntfs now is the third generation driver.

You currently opened up all permissions setting umask to 000: anyone has read, write and execute rights. To avoid that text files are considered as executables, you might want to disable the execute bit, setting umask to 111.

---

### Post by wkcchampion on 2011-01-23
> **vanadium said:**
> ```

UUID="CE7426A574268FEF"                   /media/sdb1     ntfs-3g  nls=iso8859-1,ro,users,umask=000  0  0  

```You need to remove "ro", which indicates to mount the volume "read only".

You *can* specify "ntfs" rather than "ntfs-3g" because ntfs now is the third generation driver.

You currently opened up all permissions setting umask to 000: anyone has read, write and execute rights. To avoid that text files are considered as executables, you might want to disable the execute bit, setting umask to 111.

Perfect, it now works. Linux rocks!

Please have a look at my other issue with standby and network:
[http://ubuntuforums.org/showthread.php?t=1054768&page=2](http://ubuntuforums.org/showthread.php?t=1054768&page=2)

Thanks for the help :D

---

