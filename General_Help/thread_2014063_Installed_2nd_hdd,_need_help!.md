---
title: "Installed 2nd hdd, need help!"
date: 2012-07-01
forum: General Help
---

### Post by matt_mccarron on 2012-07-01
Hello, 2nd (brand new) hdd installed, partitioned and formatted with gparted.  It appears as "1TB file system" in the home folder, left hand pane.  

In properties of this drive, permissions tab says:  "you are not the owner, so you cannot change these permissions," and in the sharing tab it has an error, the gist of it saying:  "Ask the administrator to add the line "usershare owner only = false" 
    to the [global] section of the smb.conf to allow this."

I am very new.  I tried to hit ctrl alt F2 or whatever, but this is a little intimidating.

Can anyone walk me through this?  

I need to auto mount the drive at boot and have the ability to move files from my existing drive to it and download files directly to it.

This answer in Ask Ubuntu here:  [http://askubuntu.com/questions/150028/you-are-not-the-owner-message-when-trying-to-access-folder](http://askubuntu.com/questions/150028/you-are-not-the-owner-message-when-trying-to-access-folder)

is too vague and confusing.   HOW do I change permissions from this procedure?

thanks in advance for your help:guitar:

---

### Post by oldfred on 2012-07-01
Is this a networked drive? I do not understand why a local drive needs changes to Samba for local use only.

What format is partition? That determines how you mount it in fstab. 
If not a Linux partition you can only set permissions & ownership in the fstab or mount commands.
 If Linux format you have the detail capability to set permissions and ownership on everything.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by matt_mccarron on 2012-07-01
No, not a networked drive.  Just had a brand new hdd laying around and the desktop could use it for extra storage.
I think I formatted it ext3 with gparted, for linux only...

When I click on it, the 1tbfilesystem as it appears in the home folder pane, there is a "lost and found" icon that is inaccessible and files/folders are not able to be dropped onto the drive.

I'm not sure if I've mounted it, I just need some step-by-step instructions of what to do after the partition/format that I've done with gparted.

Using the mount and fstab commands are beyond my scope of knowledge.

---

### Post by oldfred on 2012-07-01
When you click on it and see the lost & found it is mounted, but you do not have permission.

After clicking on it. Post these using terminal & copy & paste back.

```
mount

sudo fdisk -lu

sudo blkid -c /dev/null -o list
```

---

### Post by sleash78 on 2012-07-01
type man chown in the terminal then read and it will tell you how do stuff with it.

---

### Post by matt_mccarron on 2012-07-02
oldfred:

(thank you for your time, by the way)

here ya go:

god@Music4God:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/god/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=god)
/dev/sdb1 on /media/1a46b172-ce71-4d16-aaf9-6386a0b38063 type ext3 (rw,nosuid,nodev,uhelper=udisks)
god@Music4God:~$ sudo fdisk -lu
[sudo] password for god: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e9293

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   484728831   242363392   83  Linux
/dev/sda2       484730878   488396799     1832961    5  Extended
/dev/sda5       484730880   488396799     1832960   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00081abb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953523711   976760832   83  Linux
god@Music4God:~$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              5264af11-1429-45fc-88b0-5e82a19550c2
/dev/sda5  swap             <swap>         49186259-6be5-4e25-82c5-fd7d99549463
/dev/sdb1  ext3             /media/1a46b172-ce71-4d16-aaf9-6386a0b38063 1a46b172-ce71-4d16-aaf9-6386a0b38063

---

### Post by oldfred on 2012-07-02
A choice, you can mount it in /media which is the usual default and then you will see it in the left panel of Naulitus. Or you can mount it in /mnt and not see it in the left panel but can separately link folders from the mount into /home so you see each folder in /home.

You have to give it a name. In Windows it would only be d:, but in Linux you can give it a descriptive name. I will use data but it can be anything that is not a system name somewhere else.

If already mounted, unmount it first as it cannot be mounted twice.

sudo mkdir /media/data
sudo mount /dev/sdb1 /media/data
#where sdb1 needs to be your drive, partition
sudo chmod 775 /media/data
sudo chown $USER:$USER /media/data

Some recommend this as a better chmod:
sudo chmod -R a+rwX,o-w /media/data
All directories will be 775.
All files will be 664 except those that were set as executable to begin with.


But you may want to permanently mount every time you reboot, so you do not have to mount each time. Permissions should stay.

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

#fstab entry For ext3:
```
UUID=1a46b172-ce71-4d16-aaf9-6386a0b38063      /media/data ext3 relatime 0 2
```

With a very large partition like that I would use ext4 so fsck would run faster. Or create more than one partition, but that gets into data management and only you know how you will use the space.

---

### Post by matt_mccarron on 2012-07-02
thanks much!!!

---

