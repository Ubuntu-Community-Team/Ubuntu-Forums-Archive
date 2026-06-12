---
title: "Lucid Lynx - Some Windows users cannot map to shared drive"
date: 2011-05-18
forum: General Help
---

### Post by sdjon on 2011-05-18
I have a box with Lucid Lynx installed on a small internal hard drive.  I have installed a second internal drive that is auto-mounted on restart (done through pysdm).  My problem is that I have some users that can map the drive on their Windows XP machines, but other users cannot.  To make sure it is not a Windows issue, I can map the drive on each Win machine using some of the Linux user accounts, but not others. (ie. User A can map the drive on Windows A, but User B cannot map the drive on Windows A.)

I've checked the User settings on each user to verify they all have the same permissions and privileges.  The drive is open to read/write by using pysdm and setting "umask for file and directory permissions in octal  umask=000"

Any ideas what might be causing the hangup on certain users?

---

### Post by Morbius1 on 2011-05-18
Can you show us the complete line in /etc/fstab for this partition. Pysdm does some crazy things.

Also we don't know what samba method you are using ( there are 2 ) to share the folder so if you can post the output of these commands it will tell us all that:
```
net usershare info --long
``````
tesparm -s
```[COLOR=Blue]**EDIT1**[/COLOR]: That should have been:
```
 testparm -s
```**[COLOR=Blue]EDIT2:[/COLOR]** Just occurred to me that for some reason I assumed this was a samba issue because of your use of the word "map". Are you talking about a dual boot box or are you trying to reach this partition from another machine on the network?

---

### Post by sdjon on 2011-05-18
Thanks for the response Morbius.  I initially tried to use Samba, but ran into a bunch of issues, so I completely uninstalled Samba.  Do you still need the output from testparm and net usershare info?


Here is the /etc/fstab code:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=5fca3680-a07a-447d-b04d-37a9fa80e41d  /               ext4  errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation


[COLOR=Red][B]This is the drive in question:

UUID=f213ba2e-cb9e-45b7-951c-1dc10e8ea4ce  none            swap  sw                   0  0  [/B][B]
/dev/sdb1                                  /media/storage  vfat  umask=000            0  0 [/B][/COLOR] 



"Just occurred to me that for some reason I assumed this was a samba  issue because of your use of the word "map". Are you talking about a  dual boot box or are you trying to reach this partition from another  machine on the network?"

This is not a dual boot box.  I am trying to reach the partition from other (Windows) machines on the network.

---

### Post by Morbius1 on 2011-05-18
If you are not using Samba what are you using? 

That line in fstab for the Fat32 partition will mount as owner = root and with read / write / execute permissions for everyone so I don't think this is part of the problem.

---

### Post by sdjon on 2011-05-18
Not sure exactly how it happened, but I went back and found that Samba had been re-installed.  I must have been delirious and re-installed it without really thinking about it.  Anyway, at some point I believe I used Nautilus to share the drive.  I just looked in System->Administration->Shared Folders and found that the users that were unable to connect to the drive were not added to the list of valid users for Shared Folders.  I just clicked the box next to those users and Problem Solved.

As a side note:

I remember reading somewhere that Samba and Nautilus-Share can interfere with each other, which is probably what was happening to me in the first place (ie. trying to use both to share the drive).  That's possibly the reason that led me to remove Samba in the first place.

---

