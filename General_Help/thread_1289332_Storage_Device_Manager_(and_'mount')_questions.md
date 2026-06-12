---
title: "Storage Device Manager (and 'mount') questions"
date: 2009-10-12
forum: General Help
---

### Post by CovenStine on 2009-10-12
I'm running 9.04, and wanted to auto mount a hardware RAID array in my computer named 'RAID V' (by windows)
The solution I attempted to use was pysdm - Storage Device Manager.  In the process of using that tool, something I cannot explain/understand happened.  the 'RAID V' button in the 'Places' menu, takes me to /media/sdc1 instead of /media/RAID V.  Because of this, all the programs that I had I had already set up to use that drive (my Songbird library and several others) fail to find the /media/RAID V directory.  For some reason, there's still a /media/RAID V folder, but it is empty, and I cannot figure out how to automatically bind /media/sdc1 to /media/RAID V... perhaps because of the space.
I would like to revert to my pre-pysdm config and use a different tool (I'm sure one exists) to auto-mount /media/RAID V.
Any suggestions would be much appreciated.
If it's relevant, I'm a Windows power user, but had to look up every basic terminal command I've used yet.  Thanks much!

---

### Post by sisco311 on 2009-10-12
Open a terminal (Applications -> Accessories -> Terminal)
and post the output of:
```
cat /etc/fstab
```
and
```

ls -l /media
```

---

### Post by CovenStine on 2009-10-12
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sdb1 during installation
UUID=a4495db0-a021-4fc3-910f-b9f393ac484a  /               ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sdb7 during installation
UUID=f9e8f14a-947c-4184-b01b-dcbea32bb29b  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sdc1                                  /media/RAID V   ntfs         nls=iso8859-1,umask=000     0  0  
/dev/sdc1                                  /media/sdc1     ntfs         --bind,s

ls -l /media
total 28
lrwxrwxrwx 1 root root     6 2009-10-04 14:15 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2009-10-04 14:15 cdrom0
drwxr-xr-x 2 root root  4096 2009-10-04 14:15 cdrom1
lrwxrwxrwx 1 root root     7 2009-10-04 14:15 floppy -> floppy0
drwxr-xr-x 2 root root  4096 2009-10-04 14:15 floppy0
drwxr-xr-x 2 root root  4096 2009-10-11 14:04 RAID V
drwxrwxrwx 1 root root 12288 2009-10-11 13:05 sdc1



I have NO idea what I'm looking at here, it's not quite Russian or Chinese, but it's definitely at least German...
Thanks!

---

### Post by sisco311 on 2009-10-12
The second field, in fstab, describes the mount point for the filesystem. If the  name  of  the  mount point contains spaces these can be escaped as `\040'.

Edit the file:
```
gksu gedit /etc/fstab
```

and replace the 
```
/dev/sdc1 /media/RAID V ntfs nls=iso8859-1,umask=000 0 0
```
line with:
```
/dev/sdc1 /media/RAID**\040**V ntfs nls=iso8859-1,umask=000 0 0
```

save the file and close the editor.

mount the partition:
```
sudo mount -a
```

---

### Post by CovenStine on 2009-10-12
Thanks! \040 eh? Worked like a charm.  I uninstalled that pysdm package, and it still automounts. I'm assuming it's an argument somewhere?  Or does this fstab list get executed upon login?

---

### Post by sisco311 on 2009-10-13
The  file fstab contains descriptive information about the various file systems. Each filesystem is described on a separate line; fields on  each line are separated by tabs or spaces.  Lines starting with '#' are comments.

i.e.
```
[COLOR="Red"]/dev/sda1[/COLOR]    [COLOR="Blue"]/media/data[/COLOR]    [COLOR="Orange"]ext4[/COLOR]    [COLOR="Lime"]defaults[/COLOR]    0    [COLOR="Plum"]2[/COLOR]
```

[COLOR="Red"]/dev/sda1 - the name of the *block special device* (partition) or remote filesystem[/COLOR]

[COLOR="Blue"]/media/data - the mount point,  the location in the operating system's directory structure where a mounted file system appears.[/COLOR]

[COLOR="Orange"]ext4 - the type of the filesystem. i.e. vfat, ntfs, ext2, ext3, xfs...[/COLOR]

[COLOR="Lime"]defaults - the mount options. i.e. ro()read only, rw(read/write),[/COLOR]

The fifth field is  used  for  these  filesystems  by  the *dump*  command  to determine which filesystems need to be dumped. Dump examines files on an ext2 filesystem and determines which files need to be backed up. These files are copied to the given disk, tape or other storage medium for safe keeping.

[COLOR="Plum"]The  sixth field is used by the *fsck* program to determine the order in which filesystem checks are done at reboot time.[/COLOR]

[noparse]\040 - is an escape sequence. 040 is the ascii code, in octal(base 8) number system, of the space. [/noparse]The *mount* command interprets \040 as literal space in the mount point an not as a field separator.

i.e.
```
/dev/sdc1 /media/RAID V ntfs nls=iso8859-1,umask=000 0 0
```
/dev/sdc1 is the partition
/media/RAID is the mount point
V is the partition type (obviously not what you want)
ntfs is interpreted as the mount options... 


pysdm is GUI that allows full customization of hard disk mountpoints whitout manually access to fstab.

The partitions listed in fstab are mounted at boot time.


**References**

[thread=283131]How to fstab by bodhi.zazen[/thread]
```
man fstab
```
[Escape sequence - Wikipedia]("http://en.wikipedia.org/wiki/Escape_sequence")
[ASCII - Wikipedia]("http://en.wikipedia.org/wiki/ASCII")
[Octal number system - Wikipedia]("http://en.wikipedia.org/wiki/Octal")

---

