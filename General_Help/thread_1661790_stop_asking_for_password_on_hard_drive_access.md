---
title: "stop asking for password on hard drive access"
date: 2011-01-07
forum: General Help
---

### Post by surfmonkee on 2011-01-07
as much as i love ubuntu i am finding my desktop machine attached to the tv set a nightmare.

it has ubuntu studio installed and everytime i want to access the movie drive ( which in XP used to be the d: drive) it asks me for a password to access the drive.

as much as i like the idea of security this is one step too far for this machine.

how can i stop it doing this please?

---

### Post by nomko on 2011-01-07
it sound slike a problem i had.
Check this link:
[http://ubuntuforums.org/showthread.php?t=1336092&highlight=nomko](http://ubuntuforums.org/showthread.php?t=1336092&highlight=nomko)
 
Maybe its helpfull to you.

---

### Post by surfmonkee on 2011-01-07
thanks for the reply, thats exactly my problem but from reading the thread, its way over my head and i wouldnt have a clue how to do any of that stuff, so thanks for the help, i will live with passwords.

---

### Post by nomko on 2011-01-07
> **surfmonkee said:**
> thanks for the reply, thats exactly my problem but from reading the thread, its way over my head and i wouldnt have a clue how to do any of that stuff, so thanks for the help, i will live with passwords.
 
even i didn't know what to do, but just reading it a couple of times made it much easier to understand. It's not that difficult.

---

### Post by sisco311 on 2011-01-07
> **surfmonkee said:**
> thanks for the reply, thats exactly my problem but from reading the thread, its way over my head and i wouldnt have a clue how to do any of that stuff, so thanks for the help, i will live with passwords.


Check out:
[thread=283131]How to fstab[/thread]

If you need more help, open a terminal (Applications -> Accessories -> Terminal) and post the output of:
```
mount
```
and
```
sudo blkid
```

---

### Post by surfmonkee on 2011-01-07
thanks for the extra information, thats helpful. i shall read and digest.

on my way out of the door right now, but i will be back later with results if i need further help.

many thanks

---

### Post by surfmonkee on 2011-01-07
**output from mount=**

mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mike/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mike)
/dev/sdb1 on /media/MIKE type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


**output from sudo blkid=**

/dev/sda1: UUID="17cbcaaa-6987-4410-ba45-621c53287645" TYPE="ext4" 
/dev/sda5: UUID="f69a362e-6d19-406b-9ffa-9b7ffb94cdd3" TYPE="swap" 
/dev/sdb1: LABEL="MIKE" UUID="DAF5-E454" TYPE="vfat"


i am looking to mount a 160gb drive full of media content, so i dont have to password each time i want to play a file.

thanks

---

### Post by sisco311 on 2011-01-07
First unmount the partition, either via the GUI or from the CLI:
```
sudo umount /dev/sdb1
```

Backup the fstab file:
```
sudo cp /etc/fstab /etc/fstab.backup
```

Open it for editing:
```
gksu gedit /etc/fstab
```

Copy and paste the following line at the end of the file:
```

UUID=DAF5-E454    /media/MIKE    vfat    defaults,dmask=002,fmask=113,uid=1000,gid=1000    0    0
```

Save the file and exit.

Create the mount point:
```
sudo mkdir -p /media/MIKE
```

Mount the partitions listed in fstab:
```
sudo mount -a
```

---

### Post by surfmonkee on 2011-01-07
i have made a mistake.  until i rebooted i didnt realise that 'mike' was still connected.  'mike' is a usb stick so it tried to mount that on the reboot, i pressed 's' to skip it and continued to boot.

so now i need help to remove the 'mike' from mounting every time

here is the revised output without the stupid usb stick.

im sorry to waste ur time.... i should check these things more carefully and you thought 'mike' was the device i needed mounted at boot up.  sorry about that, i need to mount my extra 160 gb ide drive full of content at boot up.  thanks a million.

when i go to computer the drive is not showing at all, however last night i was playing content from it after selecting it and entering my password.  how strange it is not listed this morning.  if i go to vlc and try to play last nights content i get this

File reading failed:
VLC could not open the file "/media/New Volume/movies/movietitle.avi".
Your input can't be opened:
VLC is unable to open the MRL 'file:///media/New%20Volume/movies/movietitle.avi'. Check the log for details.


**output from mount**

/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mike/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mike)


**output from sudo blkid**

/dev/sda1: UUID="17cbcaaa-6987-4410-ba45-621c53287645" TYPE="ext4" 
/dev/sda5: UUID="f69a362e-6d19-406b-9ffa-9b7ffb94cdd3" TYPE="swap" 
mike@unknown000ae6611e24:~$

---

### Post by surfmonkee on 2011-01-07
dont you just hate loose wires

got the drive back and here is a revised mount sudo blkid

can we get rid of the mike mount at startup and get new volume to mount at boot please:
[B]
mount output [/B]
mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mike/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mike)

**sudo blkid**

/dev/sda1: UUID="17cbcaaa-6987-4410-ba45-621c53287645" TYPE="ext4" 
/dev/sda5: UUID="f69a362e-6d19-406b-9ffa-9b7ffb94cdd3" TYPE="swap" 
/dev/sdb1: LABEL="New Volume" UUID="4AF09C81F09C7543" TYPE="ntfs"

---

### Post by sisco311 on 2011-01-07
Oh, okay.

Edit the fstab file and replace the line you added with:
```
UUID=4AF09C81F09C7543    /media/**name**    ntfs    defaults,dmask=002,fmask=113,uid=1000,gid=1000    0    0
```

Create the mount point:
```
sudo mkdir /media/**name**
```

And mount the partition:
```
sudo mount -a
```

---

