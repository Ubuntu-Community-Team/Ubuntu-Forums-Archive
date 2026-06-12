---
title: "Gtkpod errors &amp; Ipod will not mount"
date: 2010-01-22
forum: General Help
---

### Post by Nbala on 2010-01-22
I am using 9.10 Karmic Koala Oct 2009 release.
 Gtkpod does not show my ipod touch, and I can not mount the ipod.
 I realise there were problems with the ipod touch syncing/mounting but gtkpod has the touch option, and I have all the files from synaptic for using an ipod touch.
 

 When I run gtkpod its just blank, no music files show up.
 If I click load ipod I get the error:
 

 “Ipod Directory Structure not found”
 Could not find iPod directory structure at '/dev/sdc2'. 
 If you are sure that the iPod is properly mounted at '/dev/sdc2', it may not be initialized for use. In this case, gtkpod can initialize it for you. 
 Do you want to create the directory structure now?
 Then I choose ipod model and mount point and get the msg:
 Error initializing ipod: problem creating iPod directory or file: 'dev/sdc2'
 

 ALSO there is an secondary static ipod icon in file browser but if I try to mount or use it I get:
 Unable to mount location  
 Mount: special device /dev/sdc2 does not exist
 [this is probably from when I tried to manually mount it in the beginning – now I cant get rid of it, any advice on that would also help]
 

 Ive tried gtkpod from sudo, Ive also tried other apps, and all the packages supposed to enable USB connections for this very purpose etc.
 

 

 FSTAB:
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
 

 MTAB:
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
 

 I really want to update my ipod Im using music from 2 years ago, any ideas greatly appreciated! :)

---

### Post by zine92 on 2010-01-22
Hey anyways. My guess is that GtkPod does not support the newest Apple Fw. Cause [HTML]http://en.wikipedia.org/wiki/Comparison_of_iPod_managers[/HTML]. Scroll down to the bottom and see.

Anyways. if you really need to transfer the musics, i have seen somewhere that transferring songs in Linux requires Wifi, which means jail broken, =X.

---

### Post by Nbala on 2010-01-22
Thanks- I read the same article and wasn't going to bother at the get go..but:
1) In gtkpod it gives the options for ipod/nano/itouch/iphone mounting within the /dev/sdc2,->if gtkpod wasn't meshing with itouch why have it as an option
2) I dl'd packages for using USB devices in linux including one for ipods in specific (inc iTouch)
3) In hunting for an answer I've read other people resolve their problems with the same fw (2.0 not 3.0) of itouch as mine. 
RE: jailbreaking- there is a page on using Wine with iTunes, there is nothing mentioned about jailbreaking there either.
I agree about that wiki, but it does say things that I have found out are not accurate.
There are workarounds for each of the issues it lists.
But thanks, Ill read it again to be sure.

---

### Post by warfacegod on 2010-01-22
iPod Touch doesn't play well with Linux and iTunes doesn't very well in Wine. Your best bet is to run Windows in a Virtual Machine and install iTunes in it.

---

### Post by BelgianKiwi on 2010-12-19
Hi Guys, I am having a similar issue with Xubuntu 10.04. I have installed both gtkpod & amorok but to use either the Ipod must be mouted as an external device. I have tried the mount command in the terminal as advised in the help tab in Gtkpod but it advises me to use root but looking at the DEV and UDEV folders in the root menus I cannot find the device listed as Sda1 or Sda2.

Is there any workaround terminal command or software I can download to mount my (Invisible) Ipod Nano from the USB port it is plugged into so that either Gtkpod or Amorak can recognise it and update it?

---

