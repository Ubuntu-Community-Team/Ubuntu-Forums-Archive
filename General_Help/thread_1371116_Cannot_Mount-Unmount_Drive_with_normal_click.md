---
title: "Cannot Mount-Unmount Drive with normal click"
date: 2010-01-03
forum: General Help
---

### Post by anur.bhargav on 2010-01-03
[FONT=Comic Sans MS]Hello everybody
Ubuntu(9.10) does not let me the permission to mount/unmount any NTFS partition with a  [COLOR=Red]normal click [/COLOR]. I have to do it by using sudo mount command like below every time.

"[SIZE=3]sudo mount /dev/sda6 /media/sda6[/SIZE]"

and a similar command to Unmount
When I try to mount using the normal click I get the following error message
-----------
[SIZE=3]Error unmounting: umount exited with exit code 1: helper 
failed with:
umount: only root can unmount /dev/sda6 from /media/sda6[/SIZE]
------------
And a similar error for mounting
[COLOR=Red]This problem started when I used storage device manager(pysdm) to mount the drives[/COLOR]
I have the same problem with all the drives  
Please Help!!!

[/FONT]

---

### Post by anur.bhargav on 2010-01-03
> **anur.bhargav said:**
> [FONT=Comic Sans MS]Hello everybody
Ubuntu(9.10) does not let me the permission to mount/unmount any NTFS partition with a  [COLOR=Red]normal click [/COLOR]. I have to do it by using sudo mount command like below every time.

"[SIZE=3]sudo mount /dev/sda6 /media/sda6[/SIZE]"

and a similar command to Unmount
When I try to mount using the normal click I get the following error message
-----------
[SIZE=3]Error unmounting: umount exited with exit code 1: helper 
failed with:
umount: only root can unmount /dev/sda6 from /media/sda6[/SIZE]
------------
And a similar error for mounting
[COLOR=Red]This problem started when I used storage device manager(pysdm) to mount the drives[/COLOR]
I have the same problem with all the drives  
Please Help!!!

[/FONT]


[FONT=Comic Sans MS]I thought the the output from the Terminal (Applications-Accessories-Terminal) commands as below will help
[/FONT]     
Code:
     mount
sudo blkid
cat /etc/fstab 
                                                                  

[FONT=Comic Sans MS]the output of the terminal goes like this
-------------------------
vaibhav@vaibhav-desktop:~$ mount
/dev/sda8 on / type ext4 (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
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
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /media/sda6 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /media/sda7 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/vaibhav/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=vaibhav)

vaibhav@vaibhav-desktop:~$ sudo blkid
/dev/sda1: UUID="D0CC76F6CC76D666" TYPE="ntfs" 
/dev/sda5: UUID="B4847C76847C3CC4" TYPE="ntfs" 
/dev/sda6: UUID="0A7C9CE27C9CC9B9" TYPE="ntfs" 
/dev/sda7: UUID="6C8C43258C42E962" TYPE="ntfs" 
/dev/sda8: UUID="9add4f41-0e02-4086-98e9-e9c492f59fff" TYPE="ext4" 
/dev/sda9: UUID="729af3c6-afbc-419c-9811-18960a0609ff" TYPE="swap" 

vaibhav@vaibhav-desktop:~$ cat /etc/fstab
UUID=B4847C76847C3CC4                      /media/sda5  ntfs-3g  defaults  0  0  
UUID=9add4f41-0e02-4086-98e9-e9c492f59fff  /            ext4     defaults  0  1  
UUID=729af3c6-afbc-419c-9811-18960a0609ff  /swap        swap     sw        0  0  
/dev/sda6                                  /media/sda6  ntfs     defaults  0  0  
/dev/sda7                                  /media/sda7  ntfs     defaults  0  0  
-------------------------
[/FONT]

---

### Post by rnerwein on 2010-01-03
hi
here is my /etc/fstab - and it works fine. on each boot the windoof files are mounted ro.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=7b6def34-adb2-41fc-81b6-56f28b95d32e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9479039f-f5d7-4a4b-8ff3-5afd28bb3e16 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# insert by richi
/dev/sda2 /vista_root ntfs ro,nosuid,allow_other,default_permissions,    0    0
/dev/sda3 /vista_data ntfs ro,nosuid,allow_other,default_permissions,    0    0

the mount points /vista_root and /vista_data has to be created via mkdir 
to mount / umount filesystem can be done only by super users !
cia

---

### Post by Leppie on 2010-01-03
add yourself to the FUSE group

---

### Post by anur.bhargav on 2010-01-03
> **Leppie said:**
> add yourself to the FUSE group

How do I add a FUSE group

---

### Post by audiomick on 2010-01-03
The group should be there already. Leppie's suggestion was to add yourself to it. Don't know how to do that, sorry...

---

### Post by Leppie on 2010-01-03
> **anur.bhargav said:**
> How do I add a FUSE group

Go to System>Administration>Users and Groups, unlock the applet by clicking the keys icon and entering your password, select your account and click properties, go to the "User Privileges" tab, select the "Mount user-space filesystems (FUSE)", click ok and close the applet. You may have to log out and log back in again for this to take effect.

---

### Post by audiomick on 2010-01-03
@ Leppie
I think my brain is turned off...
If I go to System>Administration>Users and Groups and then "administer groups", select fuse and check the box next to my user name, is that the same thing?

---

### Post by anur.bhargav on 2010-01-03
> **Leppie said:**
> Go to System>Administration>Users and Groups, unlock the applet by clicking the keys icon and entering your password, select your account and click properties, go to the "User Privileges" tab, select the "Mount user-space filesystems (FUSE)", click ok and close the applet. You may have to log out and log back in again for this to take effect.
[IMG]http://ubuntuforums.org/home/vaibhav/Desktop/Screenshot.png[/IMG]
[IMG]file:///home/vaibhav/Desktop/Screenshot.png[/IMG]
The user has already been added to the FUSE group...yet it doesn't solve my problem

---

### Post by Leppie on 2010-01-03
if it all started after installing pysdm, why don't you try to remove it?

---

### Post by anur.bhargav on 2010-01-03
> **Leppie said:**
> if it all started after installing pysdm, why don't you try to remove it?

I did it just now...i guess its an irreversible process

---

### Post by Leppie on 2010-01-03
> **audiomick said:**
> @ Leppie
I think my brain is turned off...
If I go to System>Administration>Users and Groups and then "administer groups", select fuse and check the box next to my user name, is that the same thing?
yes, that's the same thing ;)
or even:
```
$sudo adduser mick fuse
```

---

### Post by prshah on 2010-01-03
> **anur.bhargav said:**
> ```

vaibhav@vaibhav-desktop:~$ cat /etc/fstab
[color=red]UUID=B4847C76847C3CC4                      /media/sda5  ntfs-3g  defaults  0  0  [/color]
UUID=9add4f41-0e02-4086-98e9-e9c492f59fff  /            ext4     defaults  0  1  
UUID=729af3c6-afbc-419c-9811-18960a0609ff  /swap        swap     sw        0  0  
[color=red]/dev/sda6                                  /media/sda6  ntfs     defaults  0  0  [/color]
[color=red]/dev/sda7                                  /media/sda7  ntfs     defaults  0  0  [/color]

```

Simply comment out the lines in red by placing a "#" before them; Eg Press Alt+F2, give the command ```
gksudo gedit /etc/fstab
``` and then comment out the lines as follows (DO NOT COPY/PASTE THIS CODE INTO YOUR FSTAB FILE)```

[color=red]#[/color]UUID=B4847C76847C3CC4                      /media/sda5  ntfs-3g  defaults  0  0
UUID=9add4f41-0e02-4086-98e9-e9c492f59fff  /            ext4     defaults  0  1  
UUID=729af3c6-afbc-419c-9811-18960a0609ff  /swap        swap     sw        0  0  
[color=red]#[/color]/dev/sda6                                  /media/sda6  ntfs     defaults  0  0
[color=red]#[/color]/dev/sda7                                  /media/sda7  ntfs     defaults  0  0  

```

From 8.10 onwards, in order to reduce dependence on static files (such as /etc/fstab) for configuration, ntfs / removable drives / zip drives / optical drives etc are all handled by fuse (Filesystem in Userspace) and so should not have entries in /etc/fstab unless necessary. 

By placing a "#" in front of these lines, they are effectively ignored. If all seems fine, you can then delete these lines altogether (though there is no harm if you just leave them there).

---

### Post by anur.bhargav on 2010-01-03
> **prshah said:**
> Simply comment out the lines in red by placing a "#" before them; Eg Press Alt+F2, give the command ```
gksudo gedit /etc/fstab
``` and then comment out the lines as follows (DO NOT COPY/PASTE THIS CODE INTO YOUR FSTAB FILE)```

[COLOR=red]#[/COLOR]UUID=B4847C76847C3CC4                      /media/sda5  ntfs-3g  defaults  0  0
UUID=9add4f41-0e02-4086-98e9-e9c492f59fff  /            ext4     defaults  0  1  
UUID=729af3c6-afbc-419c-9811-18960a0609ff  /swap        swap     sw        0  0  
[COLOR=red]#[/COLOR]/dev/sda6                                  /media/sda6  ntfs     defaults  0  0
[COLOR=red]#[/COLOR]/dev/sda7                                  /media/sda7  ntfs     defaults  0  0  

```From 8.10 onwards, in order to reduce dependence on static files (such as /etc/fstab) for configuration, ntfs / removable drives / zip drives / optical drives etc are all handled by fuse (Filesystem in Userspace) and so should not have entries in /etc/fstab unless necessary. 

By placing a "#" in front of these lines, they are effectively ignored. If all seems fine, you can then delete these lines altogether (though there is no harm if you just leave them there).

[SIZE=5]Thank U.... It worked[/SIZE]

---

### Post by tstorm007 on 2010-01-14
Ok, I had the same problem after updating to 9.10.  This fix got the drive mounted again, but now instead of /media/sda2, it's /media/5040E..... some crazy name. How do I change where the drive is mounted under this new setup?

---

### Post by Leppie on 2010-01-14
> **tstorm007 said:**
> Ok, I had the same problem after updating to 9.10.  This fix got the drive mounted again, but now instead of /media/sda2, it's /media/5040E..... some crazy name. How do I change where the drive is mounted under this new setup?
unmount the drive and rename the label of the drive with an application like gparted.

---

