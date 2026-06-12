---
title: "Problem with external Hard Disk: READ-ONLY"
date: 2010-02-21
forum: General Help
---

### Post by riuryK on 2010-02-21
Hi everyone,

Before posting this I've spent several hours reading threads in all fora, and trying all possible solutions with no success.

The problem is that my VERBATIM external USB disk drive has become _**read-only**_. It has FAT32 file system, and has been working fine till today. I've read over there that this issue happens when the computer goes in standby mode. Well, this is the case. I did it yesterday. I didn't plug the disk yesterday, but it's very suspicious that this is happening right now after having gone standby. Moreover because I've read several posts commenting this.

My permissions options look like this:

[[IMG]http://img191.imageshack.us/img191/327/pantallazopropiedadesdeh.th.png[/IMG]]("http://img191.imageshack.us/i/pantallazopropiedadesdeh.png/")

Before give me some tips let me post here some solutions I've read, and tried with the result obtained:

**Problem**: The disk has no user permssions.
**Action**: Permissions tried via right-click menu, and via "chmod" command.
[COLOR=Red]**Result**[/COLOR]: Although I use "sudo" command, I get the message that the unit is read-only. Thus the read-write permission cannot be granted. 

**Problem**: The disk is not owned.
**Action**: Permissions tried via "chown" command.
[COLOR=Red]**Result**[/COLOR]: Although I use "sudo" command, I get the message that the unit is read-only. Thus the this cannot be modified (I am the current owner, though).

**Problem**: The device has gone IDLE.
**Action**: "sdparm" command used on the terminal.
[COLOR=Red]**Result**[/COLOR]: The device doesn't seem to be idle. IDLE parameter = 0.

**Problem**: The device was unsafely removed from Windows.
**Action**: Plugged in to Windows, and safely removed succesfully.
[COLOR=Red]**Result**[/COLOR]: Still read-only. The device hadn't been mounted into Windows. However, I gave this a try.

**Problem**: ntfs-3g packages not/badly installed.
**Action**: Packages re-installed from Synaptics repository. Additional packages installed, in case that helped.
[COLOR=Red]**Result**[/COLOR]: Still read-only.

I don't know what else to do. Please give clear instrucctions to every command via terminal. I'm a completely newbie to Ubuntu.

:confused: Any tips? Thanks a lot in advance.

---

### Post by oldfred on 2010-02-21
How are you mounting this partition. You cannot change permissions or owership once mounted:

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by pastalavista on 2010-02-21
Try installing pysdm (Python Storage Device Manager)```
sudo apt-get install pysdm
```It will appear in the System|Administration menu.

---

### Post by riuryK on 2010-02-21
> **oldfred said:**
> How are you mounting this partition. You cannot change permissions or owership once mounted:

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

I'm not mounting it myself. I'm just plugging in my USB hard disk, and it already appears withing Nautilus. I've found out that it's dev/sdb1 device. Anyway I'm not using the terminal to mount it. I just plug it in.

I've just installed Pysdm. However this seems to me a graphical way to use the terminal to mount devices. I've also tried to mount the drive via this GUI leaving the options by default, but the drive still remains read-only. Nothing changed.

Just to remember that I'm doing nothing new. It has been working fine for one week, and yesterday it decided to stack read-only.

Thanks.

---

### Post by llamabr on 2010-02-21
how about:

```
cat /etc/fstab
```

```
mount
```

and 

```
ls -l /dev/sdb1
```

---

### Post by riuryK on 2010-02-21
Last update: I dug around, and played a little with the Pysdm wizard to grant some permissions through the three options that seem to allow this. The following vfat line has been generated for the mounting:

[COLOR=Blue]**umask=777,dmask=777,fmask=777**[/COLOR]

I don't know if it has something to do, but seemed promising. However, once again, after mounting nothing changed, and the drive is still read-only. I'm starting to lose the faith... :(

---

### Post by llamabr on 2010-02-21
I'm guessing that it's not a permissions problem, but rather a problem of ownership.  so:

```
ls -l /dev/sdb1
```

and then add yourself to the group, or else change the owner.

---

### Post by riuryK on 2010-02-21
In red the output to each command:

> **llamabr said:**
> how about:

```
cat /etc/fstab
```
```
[COLOR=Red]# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                       0  0  
# / was on /dev/sda1 during installation
UUID=b1629838-be06-4cef-b834-5bc08c126e6b  /              ext3         relatime,errors=remount-ro     0  1  
# swap was on /dev/sda5 during installation
UUID=9e09b1ae-dd7b-4e86-93d7-79ebeddcaf44  none           swap         sw                             0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8          0  0  
/dev/sdb1                                  /media/sdb1    vfat         umask=777,dmask=777,fmask=777  0  0[/COLOR]
```[COLOR=Red]  
[/COLOR]
> ```
mount
```and```
[COLOR=Red]/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/carlos/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=carlos)
/dev/sdb1 on /media/VERBATIM type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
[/COLOR]
```> 
```
ls -l /dev/sdb1
``````
[COLOR=Red]brw-rw---- 1 root disk 8, 17 2010-02-21 20:03 /dev/sdb1[/COLOR]

```Still read-only.

---

### Post by llamabr on 2010-02-21
```
sudo chown -R user:user /mountpoint

sudo chmod -R 755 /mountpoint
```

then unmount it.  you can remount it with 

```
mount -a
```

and it should be writable.

---

### Post by riuryK on 2010-02-21
> **llamabr said:**
> ```
sudo chown -R user:user /mountpoint

sudo chmod -R 755 /mountpoint
```then unmount it.  you can remount it with 

```
mount -a
```and it should be writable.

I did what you said, but it's still read-only. It's quite weird: although I used "carlos" (myself) as owner, now I look into properties, and the options are shaded, stating "your're not the owner of this device, thus you cannot change its properties". The owner now shows "root". I cannot mount nor unmount from Nautilus now. I have to do it through the console.

Any ideas?

---

### Post by llamabr on 2010-02-21
Just so i understand.  You should do this with the device unmounted:

```
sudo chown carlos:carlos /dev/sdb1
sudo chmod -R /dev/sdb1
mount -a
ls -l /dev/sdb1
```
You should now be the owner, and should have write permission.

---

### Post by llamabr on 2010-02-21
Sorry.  when i say chown mountpoint, i mean:

```
chown name:name /media/disk
```

or whatever.

---

### Post by riuryK on 2010-02-21
> **llamabr said:**
> Just so i understand.  You should do this with the device unmounted:

```
sudo chown carlos:carlos /dev/sdb1
sudo chmod -R /dev/sdb1
mount -a
ls -l /dev/sdb1
```You should now be the owner, and should have write permission.

I understand what you're trying to explain me. I did it, and the result of "ls -l" is this:

```
brwxr-xr-x 1 carlos carlos 8, 17 2010-02-21 21:29 /dev/sdb1

```So I'm supposed to have read-write permission. Then I open Nautilus, and try to copy something and bang!

[IMG]http://img693.imageshack.us/img693/7867/sinnombrei.png[/IMG]

Target is read-only! Gosh, I don't know what else to do.

---

### Post by aparigraha on 2010-03-07
I've had this exact problem and I tried everything. I solved it twice by **chown** and **chgrp**, but lately it has come back... and now there is nothing I can do. This has to be a file system error, so I suggest you back up what data you have on this drive.

---

### Post by riuryK on 2010-03-08
> **aparigraha said:**
> I've had this exact problem and I tried everything. I solved it twice by **chown** and **chgrp**, but lately it has come back... and now there is nothing I can do. This has to be a file system error, so I suggest you back up what data you have on this drive.
Thanks a lot for your advice. This must be a bug. I've read the same issue in many fora.

Hopefully this will be solved with some kind of patch.

Thanks a lot again.

---

