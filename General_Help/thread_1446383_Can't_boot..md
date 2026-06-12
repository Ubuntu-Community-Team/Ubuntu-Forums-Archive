---
title: "Can't boot."
date: 2010-04-04
forum: General Help
---

### Post by EMABrad on 2010-04-04
I'm running Karmic.  I installed pysdm, changed options (that I can't remember) with it, and, upon reboot, got:

```
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
init: Failed to spawn mountall-shell main process: unable to execute: Permission denied
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
init: Failed to spawn mountall post-stop process: unable to execute: Permission denied
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
init: Failed to spawn networking main process: unable to execute: Permission denied
init: Failed to spawn udev-finish main process: unable to execute: Permission denied
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
udevd-work[828]: exec of program '/sbin/modprobe' failed

udevd-work[829]: exec of program '/lib/udev/path_id' failed

udevd-work[830]: exec of program '/lib/udev/path_id' failed

```

Upon ctrl-alt-delete at this screen, I receive:

```
init: Failed to spawn control-alt-delete main process: unable to execute: Permission denied
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
```

Yes, I've tried to boot in Recovery Mode.  It does the same thing.

I've uninstalled pysdm with a LiveCD session.  I would love to find out I can fix it without having to reinstall Ubuntu.  I need this computer.  Halp?

---

### Post by EMABrad on 2010-04-04
And here's my fstab file:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                 0  0  
# / was on /dev/sda5 during installation
UUID=d18b5390-a027-450d-aeed-fccc2eceaf27  /              ext4         users                    0  1  
# swap was on /dev/sda6 during installation
UUID=af492c66-71e5-44b5-a95b-57102369af1c  none           swap         sw                       0  0  


```

---

### Post by gzarkadas on 2010-04-04
Try this changes for a start:

```
##-<file system>------------------------------<mount pt>--<type>-------<options>-----------------------------<dump>--<pass>
proc                                          /proc       proc         defaults                              0       0  
# / was on /dev/sda5 during installation
UUID=d18b5390-a027-450d-aeed-fccc2eceaf27     /           ext4         defaults,relatime,errors=remount-ro   0       1  
# swap was on /dev/sda6 during installation
UUID=af492c66-71e5-44b5-a95b-57102369af1c     none        swap         sw                                    0       0

```Do you have other partitions? I see from the comments that you use the extended partition. If you did make other partitions during the initial installation you may have still mount points that are missing.

You can run gparted from the live CD to see what your partitions are (be careful not to do actions with it!).

---

### Post by EMABrad on 2010-04-04
Changed fstab as you prescribed.  It now works.

You are now my god.

---

### Post by ghandon.2110 on 2010-04-20
hi
here's my fstab file:

```
UUID=36afd928-3c7c-4d15-8b5d-34879e1a03fa swap swap sw 0 0
UUID=E1E277AF28DF2513 /media/My File ntfs-3g users 0 0
UUID=FEF6DF5C1B3E7436 /media/software ntfs-3g users 0 0
UUID=061f99af-64e7-43fc-9151-50dac67a8965 / ext4 users 0 1
 
```i am beginner and cannot fix problem
plez help me
tanks

---

### Post by gzarkadas on 2010-04-20
You need to state what exactly your problem is to get relevant help :).

Assuming that it is the same as the thread's title, then you should change the [COLOR=Red]`**users**'[COLOR=Black] in last[/COLOR] [/COLOR]line to [COLOR=Red]`**defaults,relatime,errors=remount-ro**'[/COLOR].

The problem is that the `users' option (which is an option to the `mount' program; type `man mount' in your terminal to read about the mount options) implies also the `nodev', `noexec' and `nosuid' options which are all inappropriate for a setup with a single / mount point (the bottom line is: you cannot execute anything nor have any devices in such a case).

I also see no proc entry in your fstab (the line:

```
 proc                                          /proc       proc         defaults
```in my previous reply in this thread). After you fix the boot problem check that your  /proc filesystem functions and if not add this line also to your fstab.

---

### Post by ghandon.2110 on 2010-04-21
hi and tanks for your answer
Changed fstab .  It now works.
i can boot 
but this error appear when i try to mount software partion
```
unable to mount software
error mounting : mount exited with exit code 1 : helper failed with :
[mntent]:line2 in /etc/fstab is bad
mount : only root can mount /dev/sda5 on /media/software

```

---

### Post by gzarkadas on 2010-04-21
You can try to append the `ro' (read-only) flag as stated in  this forum [thread]("http://ubuntuforums.org/showthread.php?t=1886"); it may be old but can help.

Check also that you have the fuse package installed. Also, it may not even be necessary to add those ntfs lines in your fstab; if I remember well I could mount from my user account any volumes present in the computer from an out-of -the-box Ubuntu install (from the `Places' menu) - but it is a long time I don't have ntfs volumes ... :)

If you need write access and it is not readily supported, look here for a way to [mount ntfs with read/write access]("http://www.linuxconfig.org/How_to_mount_partition_with_ntfs_file_system_and_read_write_access"). 

In any case, it is better to first comment out the lines in your fstab and try to manually mount the volumes by issuing `mnt' commands from a terminal window (with sudo of course). When you can succesfully mount the volumes with the options you want you can copy them to fstab and append a `,users' to them.

---

### Post by Daryth on 2010-04-29
[QUOTE=
```
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
init: Failed to spawn mountall-shell main process: unable to execute: Permission denied
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
init: Failed to spawn mountall post-stop process: unable to execute: Permission denied
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
init: Failed to spawn networking main process: unable to execute: Permission denied
init: Failed to spawn udev-finish main process: unable to execute: Permission denied
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
udevd-work[828]: exec of program '/sbin/modprobe' failed

udevd-work[829]: exec of program '/lib/udev/path_id' failed

udevd-work[830]: exec of program '/lib/udev/path_id' failed

```Upon ctrl-alt-delete at this screen, I receive:

```
init: Failed to spawn control-alt-delete main process: unable to execute: Permission denied
init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied
```Yes, I've tried to boot in Recovery Mode.  It does the same thing.
?[/QUOTE]

I am getting the same error, I am also totally baffled as to how to retrieve my fstab file to post here...
 I do have windows 7 running on the same machine though, but it cannot see my linux drive.

---

### Post by gzarkadas on 2010-04-30
> **Daryth said:**
> I am getting the same error, I am also totally baffled as to how to retrieve my fstab file to post here...
 I do have windows 7 running on the same machine though, but it cannot see my linux drive.

Use your ubuntu install cd to boot (select the run without modify option). Then mount your hdd ubuntu partition (from Places|Computer...), navigate to the etc folder and copy fstab to a usb stick. Then post it here.

You will use the same procedure to edit it for fixing (for example: `sudo gedit /media/<your partition>/etc/fstab').

---

### Post by Daryth on 2010-04-30
So I have a few Fstab files, 

> **fstab.pre-nets-config]

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device said:**
> 

[Quote=fstab.bak]
**I am really tempted to just rename this fstab and see if it works**

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc                           proc         defaults                     0  0  
# Entry for /dev/sdf5 :
UUID=cec555db-dfaf-41c8-b22d-c494730dbf5c  /                               ext4         users,user,owner             0  1  
# Entry for /dev/sdf6 :
UUID=52a740d8-caef-443a-8ddd-d184d726f1db  none                            swap         sw                           0  0  
/dev/scd0                                  /media/cdrom0                   udf,iso9660  user,noauto,exec,utf8        0  0  
/dev/sdd1                                  /media/sdd1                     ntfs-3g      users,user,owner             0  0  
/dev/sde1                                  /media/sde1                     ntfs-3g      users,user,owner             0  0  
/dev/sdf1                                  /media/sdf1                     ntfs-3g      users,user,owner             0  0  
/dev/sdc1                                  /media/sdc1                     ntfs-3g      users,user,owner             0  0  
/dev/sdb5                                  /media/sdb5                     ntfs-3g      users,user,owner             0  0  
/dev/sda1                                  /media/Old\040Media\040Storage  ntfs-3g      defaults,locale=en_CA.UTF-8  0  0  

[Quote=fstab]

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc                           proc         defaults                     0  0  
# Entry for /dev/sdf5 :
UUID=cec555db-dfaf-41c8-b22d-c494730dbf5c  /                               ext4         users,user,owner             0  1  
# Entry for /dev/sdf6 :
UUID=52a740d8-caef-443a-8ddd-d184d726f1db  none                            swap         users,sw,user,owner          0  0  
/dev/scd0                                  /media/cdrom0                   udf,iso9660  user,noauto,exec,utf8        0  0  
/dev/sdd1                                  /media/sdd1                     ntfs-3g      users,user,owner             0  0  
/dev/sde1                                  /media/sde1                     ntfs-3g      users,user,owner             0  0  
/dev/sdf1                                  /media/sdf1                     ntfs-3g      users,user,owner             0  0  
/dev/sdc1                                  /media/sdc1                     ntfs-3g      users,user,owner             0  0  
/dev/sdb5                                  /media/sdb5                     ntfs-3g      users,user,owner             0  0  
/dev/sda1                                  /media/Old\040Media\040Storage  ntfs-3g      defaults,locale=en_CA.UTF-8  0  0  
[/Quote]


~Daryth

---

### Post by gzarkadas on 2010-05-01
Change this entry in the last (/etc/fstab) file:

```

# Entry for /dev/sdf5 :
UUID=cec555db-dfaf-41c8-b22d-c494730dbf5c  /  ext4  **[COLOR=Red]users,user,owner[/COLOR]**  0  1  

```as follows (the bold are mine in both):

```

# Entry for /dev/sdf5 :
 UUID=cec555db-dfaf-41c8-b22d-c494730dbf5c  /  ext4  [COLOR=Black]**defaults,relatime,errors=remount-ro**[/COLOR]  0  1  
 
```The reasoning is the same as in the #6 post in this thread.

---

### Post by Daryth on 2010-05-01
I actually figured that out late last night, then ran the upgrade to 10.4 which took forever, and nuetralized my USB drives, so I formatted and reinstalled anyway :(

I really appreciate the help finding the file though, as without that I would still be staring at those error messages with no clue what they meant.

~Daryth

---

### Post by dekips on 2010-05-14
UGH! I just rebooted my server after 45 days, after doing upgrades of course. Now, it comes up with the same init: job_process.c:529: Unhandled error from job_process_spawn: Permission denied error... It is ubuntu 9.10 server install, I have checked /etc/fstab:
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=54656a38-a62c-4737-b783-8aeae34f7054 /               ext4    defaults,relatime,errors=remount-ro  0       1
# swap was on /dev/sda5 during installation
UUID=53369302-4295-410a-8eed-c105effad575 none            swap    sw  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I also have tried aptitde reinstall ubuntu-minimal, as well as upstart and initscripts.. All provide no resolve. How else can I get this box booted back? It is in a VMWare ESXi environment and all the other VM's are running and playing nicely.

HELP!:(

---

### Post by gzarkadas on 2010-05-15
Your /etc/fstab looks ok.  The only thing that you should check is whether the UUID contained there matches the UUID passed to the kernel command line. You can do this either by executing from the command prompt (assuming that after the error you are thrown to a console) this command
```
cat /proc/cmdline
```to show the parameters passed to the kernel, or by opening your grub boot configuration files and inspecting the value there. For grub is the file `/boot/grub/menu/lst' ; for grub2 you'll have to find out from this [link]("https://help.ubuntu.com/community/Grub2").

I have no experience with VMWare, but if it requires you to install some tools for the specific VM to function you can try to reinstall them.

It may also be the case that the hard drive is failing; you can try to perform a filesystem check and repair from your live CD, if it is possible with your configuration. 

Another suggestion posted in this [forum thread]("http://ubuntuforums.org/showthread.php?t=1335242") is to run update-grub. This may be helpful if you did in these 45 days install a new kernel of in any other ways touched your boot sequence.

If none of these work, then try to post here more information about the failing boot process. Grab a copy from your following logs
```
/var/log/syslog
/var/log/dmesg
/var/log/kern.log

```strip all info before the last boot and post them here. The easiest way is to open /var/log from nautilus after you have booted with the live CD, copy the files to a removable media, open them with gedit and trim all lines before the last boot; then post them.

---

### Post by geminizin on 2010-05-19
What's wrong with my fstab here?

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=b809a8dd-ee5c-424b-89e8-1434bb3d543b / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=37456e7e-b3c4-4d3b-aa28-f0ca9178531c /home ext3 relatime 0 2
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda2 /media/C ntfs umask=222,utf8 0 0

I'm on Ubuntu 8.0.4 Hardy Heron. I can't boot. It just freezes at the logo screen.

---

### Post by gzarkadas on 2010-05-19
The fstab looks ok. First try to add this option (in bold)
```

# Entry for /dev/sda5 :
UUID=37456e7e-b3c4-4d3b-aa28-f0ca9178531c /home ext3 relatime**,errors=remount-ro** 0 2

```in order to see if there is some filesystem error that prevents you from mounting /home.

Then try to perform a filesystem check to ensure your filesystems and hdds are ok; afterwards if the problem persists, search the logs to find out where in the boot process your system stalls. See the latest of my previous posts in this thread for details (exclude the VM-specific texts).

---

