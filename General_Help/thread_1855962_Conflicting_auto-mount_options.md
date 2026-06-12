---
title: "Conflicting auto-mount options"
date: 2011-10-07
forum: General Help
---

### Post by Lenlen on 2011-10-07
One of the first things I did when I switched over to Ubuntu was to make my second hard drive mount during startup.  To this end, I did some searching and followed instructions which made the hard drive mount in /media/Storage instead of the standard sdb1.  That worked for a little while, but then I found that the hard drive would only mount sometimes during startup and I started looking for another way.  I learned of pysdm, and that works great.

Here's the problem.  Remember how I said that sometimes the hard drive would be assigned to /media/Storage instead of /media/sdb1?  Well, when it is assigned to /media/Storage, I get a mount error during startup, asking me to skip mounting or perform a manual recovery.

I've been trying to find the method I used to assign the drive to /media/Storage so I can reverse it, but I can't find it for the life of me.  For the time being, I've commented out the line in fstab that mounts the drive to sdb1 so I don't get the error during boot, but anything else would be guesswork which is not something I'd do as root.

---

### Post by TeoBigusGeekus on 2011-10-07
Can you post us your fstab file as well as the output of
```
mount
``` 
and 
```
sudo blkid
```
?
(Have the drive mounted please while issuing these commands)

---

### Post by Lenlen on 2011-10-07
> len@len-PC:~$ mount
/dev/sdb2 on / type ext4 (rw,errors=remount-ro,commit=0)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/len/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=len)
/dev/sda1 on /media/Storage type ext4 (rw,nosuid,nodev,uhelper=udisks)> len@len-PC:~$ sudo blkid
[sudo] password for len: 
/dev/sda1: LABEL="Storage" UUID="ee93c98b-84ad-4fca-89ed-8e150139bfdc" TYPE="ext4" 
/dev/sdb2: UUID="6238cae8-da1f-4711-bffb-50298eaac918" TYPE="ext4" 
/dev/sdb3: UUID="40629ae6-86ed-4583-9e9c-59d275579bab" TYPE="swap" Am I reading this right?  It looks like it's saying there's just one hard drive, but three partitions (the one Ubuntu is installed on, swap, and Storage).

Edit:
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda2 during installation
UUID=6238cae8-da1f-4711-bffb-50298eaac918  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda3 during installation
UUID=40629ae6-86ed-4583-9e9c-59d275579bab  none         swap  sw                   0  0  

#/dev/sdb1                                  /media/sdb1  ext4  defaults             0  0  

---

### Post by drs305 on 2011-10-07
Was this what you were using in fstab:```

UUID=ee93c98b-84ad-4fca-89ed-8e150139bfdc /mnt/Storage ext4 defaults 0 1
``` 

You can add the line above to fstab and then check it to see if it mounts sdb1 correctly:
```

sudo umount /dev/sda1
sudo mount -a
```
If you get no feedback from the second command it mounted properly. You could then try rebooting to see what happens and report what the specific boot message is if it fails to mount properly.

---

### Post by Lenlen on 2011-10-07
Ok, I added the line sudo umount /dev/sda1 to fstab.  Doing sudo mount -a returns this:
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: mount point umount does not exist
```Rebooting gives me "An error occurred while mounting umount" and one for /media/sdb1.

---

### Post by drs305 on 2011-10-07
> **Lenlen said:**
> Ok, I added the line sudo umount /dev/sda1 to fstab.  Doing sudo mount -a returns this:
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: mount point umount does not exist
```Rebooting gives me "An error occurred while mounting umount" and one for /media/sdb1.

The two commands weren't to be added to fstab. Those commands are to be run in a terminal after you add the originally cited line to fstab.

The first unmounts sda1 if it was mounted. The second attempts to mount it via the settings now saved in fstab. If it mounts without any problems there will be no output from the command. If there is a problem mounting the partition, you should see an error in the terminal.

So please remove any lines you added to fstab except the "UUID=...." line, which is the line in fstab that will mount your Storage partition. Save the file, then try the commands.

If you prefer using a Label, which is more informative, rather than the UUID, use this instead (use one or the other, but not both). See later where I changed /media to /mnt:
> LABEL=Storage /mnt/Storage ext4 defaults 0 1

There are advantages to using "/mnt" vs "/media", so in fstab I'm going to make a change to what you may have. > Change /media/Storage to /mnt/Storage, then ensure the folder exists, and make sure you are the owner.

```
sudo mkdir /mnt/Storage
sudo chown $USER: /mnt/Storage
```

---

### Post by Lenlen on 2011-10-07
Ah sorry, I misunderstood your previous post.

Anyway, your instructions worked perfectly.  No errors, and the drive is mounted on startup.  Thanks for the help!

---

### Post by drs305 on 2011-10-07
:-)

I reread what I posted and revised it to avoid any misinterpretation. Anyway, glad it's now working. 

If you don't have any other mounting issues, would you please mark the thread SOLVED via the 'Thread Tools' link at the top right of the original post?  It's reversible... should that become necessary.

Happy Ubuntu-ing !

---

### Post by drs305 on 2011-10-07
:-)

I reread what I posted and revised it to avoid any misinterpretation. Anyway, glad it's now working. 


Edit: See you've now done this. vvv
If you don't have any other mounting issues, would you please mark the thread SOLVED via the 'Thread Tools' link at the top right of the original post?  It's reversible... should that become necessary.

Happy Ubuntu-ing !

---

