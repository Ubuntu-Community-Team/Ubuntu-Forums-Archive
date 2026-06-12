---
title: "iPod Mounting Errors"
date: 2010-01-22
forum: General Help
---

### Post by Nbala on 2010-01-22
I am using 9.10 Karmic Koala Oct 2009 release.
 **Gtkpod does not show my ipod touch**, and **I can not mount the ipod**.
 I realise there were problems with the ipod touch syncing/mounting but gtkpod has the touch option, and I have all the files from synaptic for using an ipod touch.
 When I USB connect the ipod touch I get a photo icon and access to photos.
 BUT I also have a permanant Ipod icon in file browser which will not mount.
 I have ensured there IS a /dev/sdc2

  

 When I run gtkpod its just blank, no music files show up.
 If I click load ipod I get the error:
 

 “Ipod Directory Structure not found”
 Could not find iPod directory structure at '/dev/sdc2'. 
 If you are sure that the iPod is properly mounted at '/dev/sdc2', it may not be initialized for use. In this case, gtkpod can initialize it for you. 
 Do you want to create the directory structure now?
 *Then I choose the ipod model and the mount point and then get the msg:*
 **Error initializing ipod:** problem creating iPod directory or file: 'dev/sdc2'
 

 *ALSO there is an secondary static ipod icon in file browser but if I try to mount or use it I get:*
 Unable to mount location  
 Mount: special device /dev/sdc2 does not exist
 

  Ive tried gtkpod from sudo, Ive also tried other apps, and all the packages supposed to enable USB connections for this very purpose etc.
 

 **HERE IS MY OUTPUT**

 **FSTAB**:
 # /etc/fstab: static file system information. 
 # 
 # Use 'blkid -o value -s UUID' to print the universally unique identifier 
 # for a device; this may be used with UUID= as a more robust way to name 
 # devices that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    defaults        0       0 
 # / was on /dev/sda1 during installation 
 UUID=b9d57231-8a16-40f3-af45-edece8976ea7 /               ext4    errors=remount-ro 0       1 
 # swap was on /dev/sda5 during installation 
 UUID=a435018d-13d8-48f0-83c9-dedb5f5ee58e none            swap    sw              0       0 
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
 /dev/sdc2 /media/iPod vfat nosuid,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0
 [ yes I removed noauto on the advice of a netizen ]  
 

 **MTAB**:
 /dev/sda1 / ext4 rw,errors=remount-ro 0 0 
 proc /proc proc rw 0 0 
 none /sys sysfs rw,noexec,nosuid,nodev 0 0 
 none /sys/fs/fuse/connections fusectl rw 0 0 
 none /sys/kernel/debug debugfs rw 0 0 
 none /sys/kernel/security securityfs rw 0 0 
 udev /dev tmpfs rw,mode=0755 0 0 
 none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0 
 none /dev/shm tmpfs rw,nosuid,nodev 0 0 
 none /var/run tmpfs rw,nosuid,mode=0755 0 0 
 none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0 
 none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0 
 binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0 
 gvfs-fuse-daemon /home/ablanathanalba/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ablanathanalba 0 0 
 /dev/sr0 /media/cdrom0 iso9660 ro,nosuid,nodev,utf8,user=ablanathanalba 0 0
  
 When I run gtkpod from terminal with sudo I receive:
 (gtkpod:31159): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkImageMenuItem 
 (gtkpod:31159): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated 
 

 -seems like graphical errors (from a theme) and unrelated but thought I'd mention it
 

 **LUSB:**

  Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth 
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 **Bus 001 Device 008: ID 05ac:1291 Apple, Inc. iPod Touch 1.Gen :confused:**
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

 

 So to break it down:
 
[LIST=1]
[*]**ipod is not read as a music device**
[*]**ipod will not mount**
[*]**all proper software is there, and others have made it work with the same setup ( same Ubuntu, same ipod firmware )- so Im thinking it is possible.**
[*]**If I try to mount the ipod icon in the file browser I am told it is not a "block" device. Does it need to be? and ifso, how do I set this?**
[/LIST]
 Ive been loving Ubuntu but Im still pretty new so I dont know all the secrets yet.
 **Any ideas greatly appreciated! :)**

---

