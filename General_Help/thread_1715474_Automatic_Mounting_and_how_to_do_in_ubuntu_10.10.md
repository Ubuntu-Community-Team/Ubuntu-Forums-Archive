---
title: "Automatic Mounting and how to do in ubuntu 10.10"
date: 2011-03-27
forum: General Help
---

### Post by nikieme on 2011-03-27
Hello everyone, my name is nish. I am new here and i need some helping in mounting my sda5 drive during bootup.

Currently i am able to manually mount this sta5 ntfs drive, but i want to ask how to edit and what to put in fstab in order to mound it on bootup.

Below is what i have in my fstab :-

[FONT=monospace]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid      0  0  
# / was on /dev/sda3 during installation
UUID=cf0025b5-b35f-4f1a-ba8f-348f8da0971f  /            ext4  errors=remount-ro        0  1  
# swap was on /dev/sda2 during installation
UUID=ca0bd38d-9b1e-4f25-a120-dc18efbc5354  none         swap  sw                       0  0  
/dev/sda5                                  /media/sda5  ntfs  nls=iso8859-1,umask=000  0  0  
/dev/sda1                                  /media/sda1  vfat  defaults                 0  0  


[Update]
I tried installing the following programs :-
1) Storage Device Manager
2) Ntfs Configuration tools

Now after messing up with both of them i am able to mount my sda5 drive, but somehow
i am still having issues with it. My sda1 was also mounted along with sda5. I have no
clue how that happened.

Below is my updated 'fstab' file content :-

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda3 :
UUID=cf0025b5-b35f-4f1a-ba8f-348f8da0971f    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=07DA-0718    /media/sda1    vfat    defaults    0    0
#Entry for /dev/sda5 :
UUID=FEE28AA7E28A63AD    /media/sda5    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sda2 :
UUID=ca0bd38d-9b1e-4f25-a120-dc18efbc5354    none    swap    sw    0    0

PS: I don't know how to read fstab file.

Thanks in advance
Nish

[/FONT]

---

