---
title: "Troubleshooting - Mapping Windows directories to the Ubuntu filesystem"
date: 2011-08-01
forum: General Help
---

### Post by stevenswall on 2011-08-01
**Problem:**

Tried to mount (without shortcuts) Windows 'Documents' directory to Ubuntu 'Documents' directory, Windows 'Pictures' to Ubuntu 'Pictures' etc. all using fstab.

**Details:**

-Windows 7 partition auto-mounts at boot to /media/sda1
-Windows 7 partition is located at /dev/sda1
-Day old installation Ubuntu 11.04 64-bit

[B]Fstab:
<FSTAB01>[/B]
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro,user_xattr 0       1
/dev/sda3       none            swap    sw              0       0
/dev/sda1    /media/sda1    ntfs-3g    rw        0    0

#MAPS WINDOWS 7 DIRECTORIES TO UBUNTU FILESYSTEM

/media/sda1/Users/taylor/Documents    /home/taylor/Documents        ntfs-3g    rw        0    0
/media/sda1/Users/taylor/Downloads    /home/taylor/Downloads        ntfs-3g    rw        0    0
/media/sda1/Users/taylor/Dropbox    /home/taylor/Dropbox        ntfs-3g    rw        0    0
/media/sda1/Users/taylor/Music        /home/taylor/Music        ntfs-3g    rw        0    0
/media/sda1/Users/taylor/Pictures    /home/taylor/Pictures        ntfs-3g    rw        0    0
/media/sda1/Users/taylor/Videos        /home/taylor/Videos        ntfs-3g    rw        0    0
/media/sda1/Users/taylor/Ubuntu\040One    /home/taylor/Ubuntu\040One    ntfs-3g    rw        0    0
[B]<END FSTAB01>

<FSTAB02>
[/B] # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro,user_xattr 0       1
/dev/sda3       none            swap    sw              0       0
/dev/sda1    /media/sda1    ntfs-3g    rw        0    0

#MAPS WINDOWS 7 DIRECTORIES TO UBUNTU FILESYSTEM

mount --bind /media/sda1/Users/taylor/Documents    ~/Documents        
mount --bind /media/sda1/Users/taylor/Downloads    ~/Downloads
mount --bind /media/sda1/Users/taylor/Dropbox    ~/Dropbox
mount --bind /media/sda1/Users/taylor/Music    ~/Music        
mount --bind /media/sda1/Users/taylor/Pictures    ~/Pictures        
mount --bind /media/sda1/Users/taylor/Videos    ~/Videos        
mount --bind /media/sda1/Users/taylor/Ubuntu\040One    ~/Ubuntu\040One
**<ENDFSTAB02>**

**Ideal Solution:**

Correctly edit Fstab so that the NTFS directories are mounted within the /home/taylor/(docs, pics, etc.) directory on bootup.

---

### Post by stevenswall on 2011-08-07
**Solution:**

Used the 'bind' command to link directories in an auto-mounted NTFS partition (/dev/sda1 to /media/sda1) to their respective Ubuntu counterparts.

**<FINAL FSTAB>** (access using sudo gedit /etc/fstab)

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro,user_xattr 0       1
/dev/sda3       none            swap    sw              0       0
/dev/sda1    /media/sda1    ntfs-3g    rw        0    0

#MAPS WINDOWS 7 DIRECTORIES TO UBUNTU FILESYSTEM

/media/sda1/Users/taylor/Documents    /home/taylor/Documents    none    bind    0    0        
/media/sda1/Users/taylor/Downloads    /home/taylor/Download    none    bind    0    0
/media/sda1/Users/taylor/Dropbox    /home/taylor/Dropbox    none    bind    0    0
/media/sda1/Users/taylor/Music        /home/taylor/Music    none    bind    0    0
/media/sda1/Users/taylor/Pictures    /home/taylor/Pictures    none    bind    0    0
/media/sda1/Users/taylor/Videos        /home/taylor/Videos    none    bind    0    0
/media/sda1/Users/taylor/Ubuntu\040One    /home/taylor/Ubuntu\040One    none    bind    0    0


<END FSTAB>
[B]
Notes:[/B]
-Use "\040" to insert a space when mounting directories whose names contain a space.
-The final mounted partition should be used (/media/sda1) rather than the device location (/dev/sda1)
-When tabbing to the next option (<file system> <mount point... etc) it is permissible to align text, rather than to merely tab once for each option.

**Sources:**
*Blazemore's Blog*
<http://www.blazemore.net/2010/12/mirror-files-across-dual-boot.html>
*Community Fstab Documentation*
<https://help.ubuntu.com/community/Fstab>

**Conclusion:**
This information was overly difficult to find, and proved to be immensely helpful when dual booting with Windows 7. Perhaps a future version of Ubuntu could map these directories during the installation, rather than importing data (thereby creating duplicates and wasting HDD space.) This solution avoids sync issues, and streamlines production between the two OS environments.

---

