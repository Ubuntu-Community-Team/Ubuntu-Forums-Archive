---
title: "Error Message  on Startup"
date: 2009-12-27
forum: General Help
---

### Post by kyle2595 on 2009-12-27
Hi, I am relatively new to Ubuntu and I am not the best when it comes to computers, so I was hoping someone could help me.  I was getting an error message while Ubuntu 9.10 was starting up.  I have included 2 pictures of the error message.  Thank you for helping me.

---

### Post by taurus on 2009-12-27
Looks like the UUID for your swap partition in /etc/fstab is wrong.  You should check the output of this command from a terminal for your swap partition and make sure it is matched with the one in /etc/fstab.

Applications -> Accessories -> Terminal
```
sudo blkid
gksudo gedit /etc/fstab
```

---

### Post by kyle2595 on 2009-12-27
The output of the "sudo blkid" is:
```
/dev/sda1: UUID="56E840D4E840B3D1" TYPE="ntfs" 
/dev/sda3: TYPE="swap" 
/dev/sda5: UUID="0e918612-6152-4c49-90f8-003759e886c4" SEC_TYPE="ext2" TYPE="ext3" 
```and the output for the "gksudo gedit /etc/fstab" command is:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# / was on /dev/sda5 during installation
UUID=0e918612-6152-4c49-90f8-003759e886c4  /              ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda6 during installation
UUID=b7e920ac-6d62-4858-9de0-689b25ada393  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sda1                                  /media/sda1    ntfs         nls=iso8859-1,umask=000     0  0  
```

---

### Post by taurus on 2009-12-27
There are others options but I will give you two.

Install gparted if you don't already have it in System -> Administration (it doesn't come with the system) and use it to make /dev/sda3 a swap partition.  Then run the sudo blkid again and this time, you should see an UUID for it.  Then, add the new UUID for swap partition in /etc/fstab.

Otherwise, just edit /etc/fstab 

```
gksudo gedit /etc/fstab
```
and place a # in front of the entry for the swap partition.

```

**[COLOR="Blue"]#[/COLOR]**UUID=b7e920ac-6d62-4858-9de0-689b25ada393  none           swap         sw                          0  0  

```
And add a new entry on the next line that looks like this.

```
/dev/sda3   none   swap   sw   0   0
```
Save it and run

```
sudo mount -a
free
```

---

### Post by kyle2595 on 2009-12-28
Thank you, I went with the second option that required me to directly edit the file.  You helped fix half of the problem, but the there is still a message that pops up.  I have included a picture of it as well.  I am not sure if the message is supposed to be there, it has not caused any harm as far as I can see.

---

