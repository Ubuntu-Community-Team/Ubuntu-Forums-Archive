---
title: "Got a partitioned hard drive i cant save stuff to"
date: 2010-05-24
forum: General Help
---

### Post by polardude1983 on 2010-05-24
I have a partition on a different hard drive that I cannot copy any files to it just wont let me. any help?

its
Partition /dev/sdb2
file system: ext3
Mount Point: blank
Label: extra hard drive
Size: 216Gb
UUID: 4918d811-79f5-4355-98e2-cca5ab1174ae

GParted:

If i right click all i get is unmount, manage flags, and information

Here is what i get from information

Warning:
Unable to find mount point
Unable to read the contents of this file system!
Because of this some operations may be unavailable.

---

### Post by rob-ward on 2010-05-24
I think you need to add it to fstab in order for it to work, you will need a line like this(just add it to the end of the file):


```
/dev/sdb2    /mnt/mydrive   ext3   defaults   0  0 
```

where 
```
/mnt/mydrive
```


is the place you want the files to be accessible at(you will need to create this directory first using this command

```
sudo mkdir /mnt/mydrive
```



In order to edit fstab you need to run this command

```
sudo gedit /etc/fstab
```

Once you have created the directory and al;tered fstab you need to run this command

```
sudo mount -a
```

it is also a good idea to make a copy of fstab before you edit it just incase, to do that you use the following command:

```
cp /etc/fstab ~/fstab_backup
```

Hope that helps

---

### Post by polardude1983 on 2010-05-24
Im guessing i dont type /mnt/mydrive

cuase that didnt work

do i do it as /mnt/sdb2? or /mnt/extra hard drive?

cause i tried /mnt/sdb2 and I get no such file or directory. Yes im a newb

---

### Post by polardude1983 on 2010-05-24
[IMG]http://i46.tinypic.com/2w3os9f.png[/IMG]

Ok so it seems i have made progress but i still cant paste anything into this partition :(

---

### Post by rob-ward on 2010-05-25
can you paste the output of the following commands

```
mount
```

```
cat /etc/fstab
```

```
cd /mnt/ ; ls -lh
```

---

### Post by polardude1983 on 2010-05-26
```

christoph@christoph-desktop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb2 on /mnt/mydrive type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/christoph/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=christoph)
/dev/sdb1 on /media/Backup__ type ext3 (rw,nosuid,nodev,uhelper=udisks)
christoph@christoph-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6876c9c2-22b4-42ee-9eff-0a2f61a305af /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=726999da-9ea3-48d1-acd0-9cfc0e40fae5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb2    /mnt/mydrive   ext3   defaults   0  0
christoph@christoph-desktop:~$ cd /mnt/ ; ls -lh
total 8.0K
drwxr-xr-x 2 root root 4.0K 2009-12-02 02:33 g
drwxr-xr-x 3 root root 4.0K 2010-04-18 08:23 mydrive
christoph@christoph-desktop:/mnt$ 


```

---

### Post by polardude1983 on 2010-05-27
bump for help

---

### Post by wilee-nilee on 2010-05-27
> **polardude1983 said:**
> bump for help

Post the outputs of post 5.

---

### Post by confused57 on 2010-05-27
> **polardude1983 said:**
> bump for help

Have you tried:
```
sudo chown -R username:username /mnt/mydrive
```

Substitute username for your ubuntu username.
You'll probably have to reboot for the changes to take effect.

This might work, if I'm reading your problem correctly.

---

### Post by dcstar on 2010-05-27
> **polardude1983 said:**
> I have a partition on a different hard drive that I cannot copy any files to it just wont let me. any help?
........

Next time just install the **pysdm** package and use that to set up the drive mounting.

---

### Post by polardude1983 on 2010-05-27
> **confused57 said:**
> Have you tried:
```
sudo chown -R username:username /mnt/mydrive
```

Substitute username for your ubuntu username.
You'll probably have to reboot for the changes to take effect.

This might work, if I'm reading your problem correctly.

It doesnt work i put in my username and it says

```
christoph@christoph-desktop:~$ sudo chown -R username:christoph /mnt/mydrive
chown: invalid user: `username:christoph'
christoph@christoph-desktop:~$ 


```

---

### Post by confused57 on 2010-05-27
Try this:
```
sudo chown -R christoph:christoph /mnt/mydrive
```

I should have given you an example.

---

