---
title: "unable to Uninstall pysdm-- help"
date: 2012-03-08
forum: General Help
---

### Post by achu91 on 2012-03-08
I am very new to ubuntu. i am having ubuntu11.10 ,as i am using virtual box i installed pysdm from ubuntu resources for automounting harddisk.It was installed correctly and harddisk are automounted after booting up.But on the contrary Virtual box was aborting with error.Then i uninstalled pysdm form resoucess menu.But still  my harddisk automounts upon boot up and VB still aborts with error.Kindly guide me know to come out this problem.

---

### Post by jerome1232 on 2012-03-08
Likely psydm is uninstalled correctly but it made an fstab entry that is automounting your disk which is still there.

What are the results of this command?

```
cat /etc/fstab
```

---

### Post by achu91 on 2012-03-08
thanx for reply 

the below is the ouput

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sdb8 during installation
UUID=a504d1c5-f704-4c83-b064-a258582ca5d1  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sdb7 during installation
UUID=994f7428-666a-4b4c-a729-6fdf6fc6c1eb  none         swap  sw                   0  0  
/dev/sda1                                  /media/sda1  vfat  defaults             0  0  
/dev/sda2                                  /media/sda2  ntfs  defaults             0  0  
/dev/sda3                                  /media/sda3  ntfs  defaults             0  0  
/dev/sda5                                  /media/sda5  ntfs  defaults             0  0  
/dev/sda6                                  /media/sda6  vfat  defaults             0  0

---

### Post by jerome1232 on 2012-03-08
Okay all of those entries at the end (in red), in /media/sdax look like manual entires. The question is which one or ones are causing the problem?


If your unsure, you can always comment them out by puting a "#" symbol in front of them without the quotes and reboot to see if it fixes the issue.

I don't have anyway of knowing which one specifically is causing the issue without more input from you. 

to open fstab for editing use this command
```
gksu gedit
```


This is just me highlighting in red the ones that are manual entries.
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sdb8 during installation
UUID=a504d1c5-f704-4c83-b064-a258582ca5d1 / ext4 errors=remount-ro 0 1
# swap was on /dev/sdb7 during installation
UUID=994f7428-666a-4b4c-a729-6fdf6fc6c1eb none swap sw 0 0
[COLOR="Red"]/dev/sda1 /media/sda1 vfat defaults 0 0
/dev/sda2 /media/sda2 ntfs defaults 0 0
/dev/sda3 /media/sda3 ntfs defaults 0 0
/dev/sda5 /media/sda5 ntfs defaults 0 0
/dev/sda6 /media/sda6 vfat defaults 0 0 [/COLOR]
```

And example of what I mean by commenting out

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sdb8 during installation
UUID=a504d1c5-f704-4c83-b064-a258582ca5d1 / ext4 errors=remount-ro 0 1
# swap was on /dev/sdb7 during installation
UUID=994f7428-666a-4b4c-a729-6fdf6fc6c1eb none swap sw 0 0
[COLOR="Red"]#/dev/sda1 /media/sda1 vfat defaults 0 0
#/dev/sda2 /media/sda2 ntfs defaults 0 0
#/dev/sda3 /media/sda3 ntfs defaults 0 0
#/dev/sda5 /media/sda5 ntfs defaults 0 0
#/dev/sda6 /media/sda6 vfat defaults 0 0 [/COLOR]
```

---

### Post by pavi_elex on 2012-03-09
Use Gparted Partition editor.
It is better solution.

---

### Post by achu91 on 2012-03-09
thanks a lot!!!!!!!!! initially i found it little difficult to open fstab as i didnt its know the file location.finally i found it in /etc. den used gksu gedit fstab,

did the same as u typed in red.Now finally all is fine.and VB is working normally ,by manually mounting the partition.

Once again thanks lot!!!!!!!!!!!!!!!!!

---

### Post by jerome1232 on 2012-03-09
My bad I forgot that, I meant to put gksu gedit /etc/fstab :p

Glad it worked for you

---

### Post by achu91 on 2012-03-09
As i understood if an entry is made fstab for sda as per the syntax  ,it should auto mount.Den in my case although the sda was auto mounted using pysdm previously by making an entry in fstab , y the VB(virtual box) didnt work?. Is it possible to automount the sda den run VB?.

---

### Post by jerome1232 on 2012-03-09
I'd have to see the error Virtual Box gave you, uncomment the lines in fstab then run mount (shown below) to mount everything in fstab, run Virtual Box and grab a screen shot of the error. (I was under the impression you had Ubuntu in a virtual machine and it was throwing errors when you booted it because you were mounting nonexistent partitions or something)

```
sudo mount -a
```

Also knowing what your partition setup looks like would be nice, as well as where things are currently mounted

```
sudo fdisk -l
mount
```

---

### Post by achu91 on 2012-03-09
i have removed all commented lines in the fstab as told by you.rebooted and followed the instruction given by you (mount,fdisk.. etc..) and oepned VB.but it aborted with error and i have attached the screenshot.
the terminal output is shown below.

[COLOR="Red"]
suja@suja-Inspiron-1525:~$ sudo mount -a
suja@suja-Inspiron-1525:~$ sudo fdisk -l[/COLOR]

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x68000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      128519       64228+  de  Dell Utility
/dev/sda2          129024    21100543    10485760    7  HPFS/NTFS/exFAT
/dev/sda3   *    21100544   104986623    41943040    7  HPFS/NTFS/exFAT
/dev/sda4       104988670   312578047   103794689    f  W95 Ext'd (LBA)
/dev/sda5       104988672   236584951    65798140    7  HPFS/NTFS/exFAT
/dev/sda6       307335168   312578047     2621440   dd  Unknown
/dev/sda7       236584960   252209151     7812096   82  Linux swap / Solaris
/dev/sda8       252211200   307322879    27555840   83  Linux

Partition table entries are not in disk order
[COLOR="red"]suja@suja-Inspiron-1525:~$ mount[/COLOR]
/dev/sda8 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /media/sda1 type vfat (rw)
/dev/sda2 on /media/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /media/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /media/sda6 type vfat (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/suja/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=suja)
suja@suja-Inspiron-1525:~$ 

one for thing as we have made all sda entries in fstab only 2 nos of sda are auto mounted i.e sda5 and sda3
(in the screen shot it can been that only 2 sda are listed in the left side menu)

---

### Post by jerome1232 on 2012-03-09
Taking a stab in the semi dark, I think when you setup that virtual machine, you put the vdi file(the virtual hard drive) on one of your windows partitions, when you installed psydm that windows partition was set to mount somewhere else, and therefore virtualbox couldn't find your vdi file.

Really all we need to do then is figure out which partition you put your vdi file, and tell virtualbox where to find it now. To get that last bit of info, I need you to re-comment your fstab so that virtualbox would work, test virtualbox to see if it works, if it does work repost the contents of mount if you need my help

```
mount | grep DATAPART
```

Look for the /dev/sdxx part, once your know it's dev path, look at your fstab to see where it's going to be mounted, uncomment fstab and reboot. Open vbox, click on your virtual machine, click settings, click storage, click the hard disk file in the right hand pane, click the icon that looks like hard drive platters and select "Choose a virtual hard disk file", browse to the new mountpoint and select your virtual hard disk file.


If you have questions feel free to ask and post a screenshot/or terminal output that your unsure of.

---

### Post by achu91 on 2012-03-10
i tried the below mentioned command which was suggested by you
mount | grep DATAPART
 but didnt yeild any the result.Then i simply modified my fstab line on experimental basis 
which was /dev/sda5                                  /media/sda5  ntfs  defaults             0  0  
to
/dev/sda5                                  /media/DATAPART1  ntfs  defaults             0  0  

but to my surprise the vb started working after a reboot without any errors.

I still don't know the technicality on how it worked.
Thanks very very much in guiding me to solving my issue.

---

