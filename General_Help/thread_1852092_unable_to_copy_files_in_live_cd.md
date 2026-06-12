---
title: "unable to copy files in live cd"
date: 2011-09-29
forum: General Help
---

### Post by zer0net on 2011-09-29
Hello,
I have ubuntu 8.04, the file system got corrupted somehow, and after running
```
 fsck 
```
It had deleted bunch of files/sectors and now when the system boots i can see the empty desktop but i cant open any folders (ie: my computer, documents etc)

gksudo nautilus doesnt work either, so i booted from live cd, but every time i try to copy files from drive it gives me some error message that "the folder cannot be handled because you do not have permission to read it"

Can someone please help?

Thank you

---

### Post by matt_symes on 2011-09-29
Hi

> gksudo nautilus doesnt work either, so i booted from live cd, but every  time i try to copy files from drive it gives me some error message that  "the folder cannot be handled because you do not have permission to read  it"

That does not sound good. 

The good thing is it boots to the desktop so it may just be your home directory that is corrupted.

From the liveCD, mount the partition, open a terminal and type

```
ls -l /home
```

and 

```
ls -l /home/<user_name>
```

and replace <user_name> with your user name. That is a small L after ls above. Post the results back here.

Also, i would create another user and try to login as that new user. You may need to chroot from the liveCD to do this or boot into recovery mode and add the new user that way.

Kind regards

---

### Post by blueridgedog on 2011-09-29
You will need to use sudo to copy the files as your LiveCD user is not the same as the user that owns the files on the disk.  You can use the commands that matt_symes posted, prefacing them with sudo.  

Additionally, you can copy them with sudo cp /path/to/file /path/to/new/location.

If you want to copy file with nautilus, you can run it as root, then access your files:

```
gksudo nautilus
```

Be careful when using a root session of nautilus.

---

### Post by zer0net on 2011-09-29
> **blueridgedog said:**
> You will need to use sudo to copy the files as your LiveCD user is not the same as the user that owns the files on the disk.  You can use the commands that matt_symes posted, prefacing them with sudo.  

Additionally, you can copy them with sudo cp /path/to/file /path/to/new/location.

If you want to copy file with nautilus, you can run it as root, then access your files:

```
gksudo nautilus
```

Be careful when using a root session of nautilus.

I launched gksudo nautilus from terminal in live cd,
i then opened my hard drive and tried to copy /etc folder to usb, it says 
"the folder cannot be handled because you do not have permission to read it"

---

### Post by zer0net on 2011-09-29
> **matt_symes said:**
> Hi



That does not sound good. 

The good thing is it boots to the desktop so it may just be your home directory that is corrupted.

From the liveCD, mount the partition, open a terminal and type

```
ls -l /home
```

and 

```
ls -l /home/<user_name>
```

and replace <user_name> with your user name. That is a small L after ls above. Post the results back here.

Also, i would create another user and try to login as that new user. You may need to chroot from the liveCD to do this or boot into recovery mode and add the new user that way.

Kind regards

```
ls -l /home
```
output: 
total 0
dwxr-xr-x 22 ubuntu ubuntu 760 2011-09-29 21:19 ubuntu

```
ls -l /home/zer0
```
output:
ls: cannot access /home/zer0: no such file or directory

---

### Post by zer0net on 2011-09-29
how can i copy the files that i need from hard drive to usb using live cd?

---

### Post by blueridgedog on 2011-09-29
The /home/<user_name> syntax will give you access to the temporary file system of the LiveCD, not your mounted/damaged volume on the disk drive.

If you went to /etc, you may have encountered the same issue.

To access your files, you will need to mount the drive and it may already be mounted.

What is the output of:

```
mount
```

and 

```
sudo fdisk -l
```

That is a lower case "L"...not a number 1.

??

---

### Post by LinuxFan999 on 2011-09-29
After backing up as much as you can, you should install Ubuntu 10.04 over 8.04, since the desktop version of 8.04 is no longer supported.

---

### Post by zer0net on 2011-09-29
> **blueridgedog said:**
> The /home/<user_name> syntax will give you access to the temporary file system of the LiveCD, not your mounted/damaged volume on the disk drive.

If you went to /etc, you may have encountered the same issue.

To access your files, you will need to mount the drive and it may already be mounted.

What is the output of:

```
mount
```

and 

```
sudo fdisk -l
```



That is a lower case "L"...not a number 1.




```
 mount

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb on /media/PENDRIVE type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdc1 on /media/USB DISK type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


 
```

and sudo fdisk -l

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30020   241135618+  83  Linux
/dev/sda2           30021       30394     3004155    5  Extended
/dev/sda5           30021       30394     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 2021 MB, 2021654528 bytes
63 heads, 62 sectors/track, 1010 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0xb0bcd68e

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      825235      888389   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(825234, 44, 50)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(888388, 51, 15)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      110823      309410   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(110822, 6, 14)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(309409, 54, 34)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      478639      969993   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(478638, 40, 56)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(969992, 62, 35)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      137582      139713     4161536    a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(137581, 61, 33)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(139712, 51, 38)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdc: 16.0 GB, 16039018496 bytes
247 heads, 25 sectors/track, 5073 cylinders
Units = cylinders of 6175 * 512 = 3161600 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        5074    15662028    b  W95 FAT32

```

---

### Post by zer0net on 2011-09-29
> **LinuxFan999 said:**
> After backing up as much as you can, you should install Ubuntu 10.04 over 8.04, since the desktop version of 8.04 is no longer supported.

i intend to :)

---

### Post by matt_symes on 2011-09-29
Hi

I should have been more specific about the mount point. Your Linux partition is mounted at sda1 by the looks of it.

So using that mount point it would be.

```
ls -l /media/disk/home
```

and

```
ls -l /media/disk/home/zer0
```

If you need to mount it from the terminal (assuming ext4)

```
sudo mkdir /media/disk
sudo mount -t ext4 /dev/sda1 /media/disk
```

and to unmount

```
sudo umount /dev/sda1
```

Kind regards

---

### Post by zer0net on 2011-09-30
> **matt_symes said:**
> Hi

I should have been more specific about the mount point. Your Linux partition is mounted at sda1 by the looks of it.

So using that mount point it would be.

```
ls -l /media/disk/home
```

and

```
ls -l /media/disk/home/zer0
```

If you need to mount it from the terminal (assuming ext4)

```
sudo mkdir /media/disk
sudo mount -t ext4 /dev/sda1 /media/disk
```

and to unmount

```
sudo umount /dev/sda1
```

Kind regards

by using the code
```
ls -l /media/disk/home
```

and

```
ls -l /media/disk/home/zer0
```

i see the files, now how do i copy them to usb drive? 
I tried
```
sudo chmod 755 /media/home/zer0/Documents
```
i applied the chmod to Documents folder because all the files i want to backup i was able to copy to the documents folder, (etc, var, and other folders), but when i try to copy paste into usb drive i still get errors

"Error making symbolic link: Operation not permitted"

maybe need to make the chmod command propagate throughout its sub dir as well.

---

### Post by zer0net on 2011-09-30
ok so i did
```
sudo chmod -R 777 /media/home/zer0/Documents
```
i get message that some *.js files No Such Directory,
after that if I do 
```
gksudo nautilus
```
and try to manually copy paste the folder to USB DISK I get  the error "Error making symbolic link: Operation not permitted".

any help will be greatly appreciated.

---

### Post by blueridgedog on 2011-09-30
It appears that your internal disk is mounted as:

/media/disk/home/zer0

and you have two options of where to copy files:
edit: I did not note the actual name of the USB drive as "USB DISK"  You will need to use quotes.
/dev/sdb on /media/PENDRIVE type vfat
/dev/sdc1 on /media/USB DISK

So, to copy the files:

```
sudo cp -R /media/disk/home/zer0 /media/PENDRIVE
```

or 
edit: added quotes

```
sudo cp -R /media/disk/home/zer0 "/media/USB DISK"
```

Other directories (/media/disk/etc for example) could be copied the same way.

---

### Post by zer0net on 2011-09-30
ok so
```

ubuntu@ubuntu:~$ sudo ls -l /media/
total 12
drwxr-xr-x 23 root   root 4096 2011-09-16 18:48 disk
drwx------  8 ubuntu root 8192 2011-09-30 12:25 USB DISK

```

and if i go

```

ubuntu@ubuntu:~$ sudo ls -l /media/USB DISK
ls: cannot access /media/USB: No such file or directory
ls: cannot access DISK: No such file or directory

```

I dont think it likes the space inbetween USB and DISK, how do i fix that?

---

### Post by blueridgedog on 2011-09-30
That would be:

```
sudo ls -l "/media/USB DISK"
```

Due to the space in the name.

---

### Post by zer0net on 2011-09-30
ahhh makes sense, however i popped it in windows computer and changed the name to USBDISK and then i tried the cp command that you have mentioned, it started to copy, but... i get all these errors,
there are many more which are not shown below

```

rk/if-up.d/wpasupplicant': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/network/if-down.d/wpasupplicant': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/network/if-pre-up.d/wpasupplicant': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/network/if-post-down.d/avahi-daemon': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/network/if-post-down.d/wpasupplicant': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K16dhcdbd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/S20sendsigs': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K50alsa-utils': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K20clamav-daemon': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K79quotarpc': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K21spamassassin': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K21postgresql-8.3': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K20avahi-daemon': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K01usplash': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K85bind9': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K99laptop-mode': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/S01linux-restricted-modules-common': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K20mailman': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/S90halt': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/S30urandom': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/S60umountroot': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K20apport': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/S15wpa-ifupdown': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K23mysql-ndb-mgm': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/S40umountfs': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K59mountoverflowtmp': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K09apache2': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K50proftpd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K20saslauthd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K21mysql': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/S89casper': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K85quota': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/S31umountnfs.sh': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K01gdm': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K25hwclock.sh': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K20clamav-freshclam': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K10webmin': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K20postfix': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc0.d/K22mysql-ndb': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/sites-enabled/genvion.ca.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/sites-enabled/000-default': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/status.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/rewrite.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/dir.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/mime.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/dav_svn.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/dav.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/negotiation.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/ssl.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/authn_file.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/actions.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/authz_default.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/ssl.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/env.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/setenvif.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/authz_user.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/dav_fs.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/fcgid.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/proxy.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/alias.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/autoindex.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/authz_groupfile.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/php5.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/dir.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/actions.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/auth_digest.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/ruby.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/cgi.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/mime.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/autoindex.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/status.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/dav_fs.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/fcgid.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/authz_host.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/dav_svn.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/setenvif.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/alias.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/php5.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/auth_basic.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/proxy.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/negotiation.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apache2/mods-enabled/suexec.load': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/skel/Examples': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apm/resume.d/00hwclock': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apm/resume.d/20alsa': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apm/suspend.d/80alsa': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apm/suspend.d/99hwclock': Operation not permitted
cp: cannot access `/media/disk/home/administrator/Documents/etc/apm/event.d': Input/output error
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S24dhcdbd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S20clamav-freshclam': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S16ssh': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S50proftpd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S99rmnologin': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S10powernowd.early': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S99lookup-domain': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S05vbesave': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S99acpi-support': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S18mysql-ndb': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S24dovecot': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S10xserver-xorg-input-wacom': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S99webmin': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S25bluetooth': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S24hal': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S18avahi-daemon': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S19postgresql-8.3': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S20cupsys': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S29ubiquity': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S20nvidia-kernel': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S98usplash': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S20rsync': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S17mysql-ndb-mgm': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S10sysklogd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S20hotkey-setup': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S25pulseaudio': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S11klogd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S20postfix': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S10acpid': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S20powernowd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S12dbus': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S19spamassassin': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S20mailman': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S30gdm': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S20saslauthd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S89cron': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S20apport': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S89anacron': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S99laptop-mode': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S19mysql': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S21quotarpc': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S15bind9': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S20apmd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S89atd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S20clamav-daemon': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S99rc.local': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S91apache2': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S99stop-readahead': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S01policykit': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc2.d/S23ntp': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/mail/spamassassin': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/php5/cli/conf.d': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/php5/apache2/conf.d': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/php5/cgi/conf.d': Operation not permitted
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/etc/perl/XML/SAX/ParserDetails.d/XML::LibXML::SAX': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/etc/perl/XML/SAX/ParserDetails.d/XML::LibXML::SAX::Parser': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/etc/perl/XML/SAX/ParserDetails.d/XML::SAX::PurePerl': Invalid argument
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/pango/pangox.aliases': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apparmor.d/force-complain/usr.bin.freshclam': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/apparmor.d/force-complain/usr.sbin.clamd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K11atd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K90sysklogd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K16dhcdbd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K11anacron': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K20clamav-daemon': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K79quotarpc': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K21spamassassin': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K21postgresql-8.3': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K20avahi-daemon': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K01usplash': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K85bind9': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K99laptop-mode': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K20mailman': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K20apport': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K23mysql-ndb-mgm': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K20powernowd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K15pulseaudio': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K89klogd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K20apmd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K99policykit': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/S30killprocs': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K09apache2': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K20rsync': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K74bluetooth': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K50proftpd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K20saslauthd': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K88dbus': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K21mysql': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K23ntp': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K20acpi-support': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K11cron': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K24dovecot': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K39ufw': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K21acpid': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K20nvidia-kernel': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K84ssh': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K01gdm': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/S90single': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K20clamav-freshclam': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K10webmin': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K20postfix': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K20hotkey-setup': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K22mysql-ndb': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K16hal': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/rc1.d/K80cupsys': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xinit/xinput.d/zh_SG': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xinit/xinput.d/zh_HK': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xinit/xinput.d/zh_CN': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xinit/xinput.d/ko_KR': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xinit/xinput.d/ja_JP': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xinit/xinput.d/zh_TW': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xinit/xinput.d/all_ALL': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xinit/xinput.d/th_TH': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/X': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xkb/geometry.dir': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xkb/semantics': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xkb/symbols': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xkb/rules': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xkb/types.dir': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xkb/semantics.dir': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xkb/symbols.dir': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xkb/geometry': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xkb/keycodes.dir': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xkb/keymap.dir': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xkb/compat': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xkb/compat.dir': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xkb/keycodes': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xkb/types': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/xkb/keymap': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/X11/app-defaults/XScreenSaver': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/40-nonlatin.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/10-hinting.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/30-metric-aliases.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/45-latin.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/30-defoma.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/90-ttf-thai-tlwg-synthetic.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/65-nonlatin.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/65-ttf-thai-tlwg.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/65-fonts-persian.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/10-antialias.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/30-urw-aliases.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/80-delicious.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/49-sansserif.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/70-no-bitmaps.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/53-monospace-lcd-filter.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/51-local.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/90-synthetic.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/20-unhint-small-vera.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/90-ttf-arphic-uming-embolden.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/52-languageselector.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/35-ttf-arphic-uming-aliases.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/69-unifont.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/25-ttf-arphic-uming-render.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/50-user.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/41-ttf-arphic-uming.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/64-ttf-arphic-uming.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/20-fix-globaladvance.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/10-no-sub-pixel.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/25-ttf-arphic-uming-bitmaps.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/30-cjk-aliases.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/60-latin.conf': Operation not permitted
cp: cannot create symbolic link `/media/USBDISK/Manualbackup/Documents/etc/fonts/conf.d/10-hinting-medium.conf': Operation not permitted

```

---

### Post by blueridgedog on 2011-09-30
Those are not files, they are symbolic links to files that actually exist elsewhere. 

If you want to copy the source file, the you can use the -L switch when copying.  I don't recommend it as you will not need those files for your data recover.

---

### Post by zer0net on 2011-09-30
oh great, that puts my mind at ease a little bit, because since the morning i've been stressing over the symbolic link error

I'm going to backup the data and then do a clean install of ubuntu 10.04

Thank you blueridgedog, and matt_symes for all the help,

I'll post back with the updates.

---

### Post by blueridgedog on 2011-09-30
Verify the backups first!  Also, with the upgrade in OS version being so big, little if any of the files salvaged from /etc will be of any value to you.  Focus on what is in your home directory.

---

### Post by zer0net on 2011-09-30
ok so i'm trying to copy this one folder which contains emails for all the users and its about 3GB, but when i run the command, i get the following error messages

```


cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1301669952.24286_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1286990863.22729_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1276049183.22608_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1295275863.22762_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1289226923.22829_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1296065908.30732_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1292856257.5888_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1302028330.14182_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1285971488.28883_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1316155375.10192_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1296486655.28751_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1300992529.5639_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1303318647.20046_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1263834892.18369_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1305658241.8524_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1279275608.22117_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1311600770.24639_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1263868233.5458_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1290026983.3291_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1313621978.9319_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1283520246.P8737Q2M310348.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1314294934.26827_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1315334286.20047_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1279127489.26406_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1291041384.17131_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1288576690.10262_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1310141432.4941_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1284385052.13744_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1283520246.P8737Q3M398413.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1285175855.28960_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1275934878.17214_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1271281459.11015_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/purchase/Maildir/cur/1295880739.8089_0.domain.ca:2,S': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/admin/Maildir/cur/1271680825.7149_0.domain.ca:2,': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/admin/Maildir/cur/1238648430.32091_0.domain.ca:2,': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/admin/Maildir/cur/1238302819.2306_0.domain.ca:2,': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/admin/Maildir/cur/1271691912.12081_0.domain.ca:2,': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/admin/Maildir/cur/1238389218.20624_0.domain.ca:2,': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/admin/Maildir/cur/1238734830.4873_0.domain.ca:2,': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/admin/Maildir/cur/1237957208.23372_1.domain.ca:2,': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/admin/Maildir/cur/1271684366.8880_0.domain.ca:2,': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/admin/Maildir/cur/1238475614.7282_0.domain.ca:2,': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/admin/Maildir/cur/1238216416.16078_0.domain.ca:2,': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/admin/Maildir/cur/1238562016.32373_0.domain.ca:2,': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/admin/Maildir/cur/1271684786.9015_0.domain.ca:2,': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/admin/Maildir/cur/1271970519.22679_0.domain.ca:2,': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/admin/Maildir/cur/1238130017.29646_0.domain.ca:2,': Invalid argument
cp: cannot create regular file `/media/USBDISK/Manualbackup/Documents/domain/homes/admin/Maildir/cur/1238043615.11304_0.domain.ca:2,': Invalid argument


```

and after it is finished copying the folder is only 40MB

---

### Post by zer0net on 2011-09-30
*bump*

---

### Post by blueridgedog on 2011-10-02
Perhaps you should try rsync:

```
rsync -av /home/zer0/ /media/USBDISK
```

---

### Post by zer0net on 2011-10-02
Hi, thanx for reply blueridgedog.
I was able to backup some of the data, and then tried to clean install 10.04, but ran into many errors during installation, so after many tries later when it did install, I ran the disk utility, and it showed there were 111 bad sectors on the disk. So the HDD is corrupted, I'm going to pickup a new one tomorrow and then install 10.04 and reconfigure the whole thing again with the help of some of the data that i was able to backup.

Thank you everyone for taking your time to help me out, I really appreciate it.

---

