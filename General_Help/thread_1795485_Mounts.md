---
title: "Mounts"
date: 2011-07-02
forum: General Help
---

### Post by janarene on 2011-07-02
What the hell is wrong with 11.04?  One day I wake up and find all of my mounts functioning properly, the next day many are missing.  I've been running with the same fstab for years.  The problem isn't only with cifs shares, but even with internal ext4 shares.  I'm so disgusted I'm about to run to Windows after 10 or so years of prompting people to move to Linux.

---

### Post by janarene on 2011-07-02
And now that I've booted from 10.10 all of my mounts work correctly.

A very unhappy camper.

---

### Post by janarene on 2011-07-03
and today after booting 11.04 all of my internal shares are missing.  but if I su, and mount -a, everything comes together.  What the hell is going on here?

---

### Post by mikejonesey on 2011-07-03
lol update your fstab file to get disks by uuid instead of device id no thats the long string like 86576547-35434535-345435435-36546456 and can be found somewhere like /proc/disk/by-uuid also make sure the types are correct eg ext2 or ntfs... maybee copy from ur 10.10 part and edit apropriety, strange behaviour tho...

---

### Post by janarene on 2011-07-03
Mike,

I did what you said and changed my /dev/sda# to UUID.  Still no happy's happening over here.

My fstab is:
proc            /proc           proc    nodev,noexec,nosuid 0       0                                                                                                                         
/dev/sdb2       /               ext4    errors=remount-ro 0       1                                                                                                                           
/dev/sdb1       /boot           ext2    defaults        0       2                                                                                                                             
# swap was on /dev/sdc2 during installation                                                                                                                                                   
#UUID=a6506e8f-0564-4e64-adf6-cef8f56978c0 none            swap    sw              0       0                                                                                                  
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0                                                                                                                    
/dev/mapper/cryptswap1 none swap sw 0 0                                                                                                                                                       
                                                                                                                                                                                              
//TINKERBELL/IS.BACKUP                  /home/janarene/mnt/IS.BACKUP            cifs uid=janarene,gid=janarene,credentials=/root/.smbcredentials        0 0                                   
//TINKERBELL/FS.Sound_File_Library      /home/janarene/mnt/FS.Sounds            cifs uid=janarene,gid=janarene,credentials=/root/.smbcredentials        0 0                                   
//TINKERBELL/FS.OS_Images               /home/janarene/mnt/FS.OS_Images         cifs uid=janarene,gid=janarene,credentials=/root/.smbcredentials        0 0                                   
//TINKERBELL/FS.File_Archive_Library    /home/janarene/mnt/FS.Files             cifs uid=janarene,gid=janarene,credentials=/root/.smbcredentials        0 0                                   
//TINKERBELL/LAN.BACKUP                 /home/janarene/mnt/LAN.BACKUP           cifs uid=janarene,gid=janarene,credentials=/root/.smbcredentials        0 0                                   
//TINKERBELL/FULL_DVD                   /home/janarene/mnt/FS.FULL_DVD          cifs uid=janarene,gid=janarene,credentials=/root/.smbcredentials        0 0                                   
//TINKERBELL/FS.Audio_Books             /home/janarene/mnt/FS.Audio_Books       cifs uid=janarene,gid=janarene,credentials=/root/.smbcredentials        0 0                                   
//TINKERBELL/FS.Music_File_Library      /home/janarene/mnt/FS.Music             cifs uid=janarene,gid=janarene,credentials=/root/.smbcredentials        0 0                                   
//TINKERBELL/FS.Documentation_Library   /home/janarene/mnt/FS.Docs              cifs uid=janarene,gid=janarene,credentials=/root/.smbcredentials        0 0                                   
//TINKERBELL/FS.Graphic_Image_Library   /home/janarene/mnt/FS.GFx               cifs uid=janarene,gid=janarene,credentials=/root/.smbcredentials        0 0                                   
//TINKERBELL/FS.Video_File_Library_I    /home/janarene/mnt/FS.Video             cifs uid=janarene,gid=janarene,credentials=/root/.smbcredentials        0 0                                   
//TINKERBELL/KIOSK                      /home/janarene/mnt/KIOSK                cifs uid=janarene,gid=janarene,credentials=/root/.smbcredentials        0 0
//TINKERBELL/HiDef                      /home/janarene/mnt/HiDef                cifs uid=janarene,gid=janarene,credentials=/root/.smbcredentials        0 0
//TAK/www                               /home/janarene/mnt/FS.WWW               cifs uid=janarene,gid=janarene,credentials=/root/.smbcredentials        0 0
UUID=505630B556309DA2                   /home/janarene/mnt/INT.SHARED           ntfs-3g quiet,defaults,umask=007,gid=1000,uid=1000                      0 0
UUID=9E6CE7136CE6E54D                   /home/janarene/mnt/INT.WINXP            ntfs-3g quiet,defaults,umask=007,gid=1000,uid=1000                      0 0

Which probably looks like crap formatted on this forum, but it's somewhat readable.

mtab reports:
/dev/sdb2 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
/dev/sdb1 /boot ext2 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/home/janarene/.Private /home/janarene ecryptfs ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=59714d7a3c533753,ecryptfs_fnek_sig=6b95effcdd044e2a 0 0
//TINKERBELL/FS.Audio_Books/ /home/janarene/mnt/FS.Audio_Books cifs rw,mand 0 0
//TINKERBELL/FULL_DVD/ /home/janarene/mnt/FS.FULL_DVD cifs rw,mand 0 0
//TAK/www/ /home/janarene/mnt/FS.WWW cifs rw,mand 0 0
gvfs-fuse-daemon /home/janarene/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=janarene 0 0
//TINKERBELL/FS.File_Archive_Library/ /home/janarene/mnt/FS.Files cifs rw,mand 0 0
//TINKERBELL/LAN.BACKUP/ /home/janarene/mnt/LAN.BACKUP cifs rw,mand 0 0
//TINKERBELL/IS.BACKUP/ /home/janarene/mnt/IS.BACKUP cifs rw,mand 0 0
//TINKERBELL/FS.Video_File_Library_I/ /home/janarene/mnt/FS.Video cifs rw,mand 0 0
//TINKERBELL/FS.Documentation_Library/ /home/janarene/mnt/FS.Docs cifs rw,mand 0 0
//TINKERBELL/FS.Music_File_Library/ /home/janarene/mnt/FS.Music cifs rw,mand 0 0
//TINKERBELL/KIOSK/ /home/janarene/mnt/KIOSK cifs rw,mand 0 0
//TINKERBELL/FS.Graphic_Image_Library/ /home/janarene/mnt/FS.GFx cifs rw,mand 0 0
janarene@Cleo:~$

OS.Images isn't mounted
FS.Sounds isn't mounted
HiDef isn't mounted
INT.SHARED isn't mounted
INT.WINXP isn't mounted

If you or anyone has a clue please smack me beside my head NOW!  Because the next time I boot 11.04 this all changes.  ONE time I found my ntfs shares mounted correctly.  Today isn't one of those days.

---

### Post by janarene on 2011-08-01
Well as an update as of 8/1/11, after running updates again everything has worked for two days straight and multiple boots.  I think it's fixed.

---

