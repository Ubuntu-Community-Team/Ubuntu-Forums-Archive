---
title: "unable to unmount microsd of gsm via usb cable"
date: 2012-07-03
forum: General Help
---

### Post by harun3d on 2012-07-03
I have an error for unmounting my android gsm which is connected with usb  cable.  I have no problem with usb stick.  The link to my gsm in the  bookmarks of file explorer stays on. ubuntu says: ```
unable to  unmount 
/sbin/umount.udisks: no device for /media/H: No such device
```  I  did all what is mentioned in [another thread]("http://ubuntuforums.org/showthread.php?p=9346350") where someone had this problem for usb stick, so not for gsm.  He had root problems.  I don't have it.  The solutions of that thread didn't help.
He shows an unknown character instead of the name of my microsd card in  gsm. instead of harun, he says "h..." with a rectangle and  0 0 0 C in  this rectangle.  The rectangle is as big as one normal letter. see  picture.  I think this happened after I had made a bootable usb stick.

---

### Post by matt_symes on 2012-07-03
Hi

Do you have a corrupted label on the gsm device ?

With the device plugged in type (from the terminal)

```
sudo blkid 
```

Enter your password. It will not be echoed to the screen.

Post the results back here.

Have you tried to change the label if it is corrupted ?

Also, have you tried to unmount it manually ?

You can find the mount point from the command

```
mount
```

and then 

```
sudo umount <mount_point>
```

Post back if you need direction on this.

Kind regards

---

### Post by harun3d on 2012-07-06
Thanks for your response.  I would answer earlier if ubuntuforums could send me a mail about replies on my threads but probably this is not possible for those who have less than 50 posts.  

Probably the label of micro sd is corrupted.  But I didn't change the name, not intentionally.
```
hc@hc-laptop:~$ sudo blkid
/dev/sda1: LABEL="WinRE" UUID="48EC....(hidden by me)" TYPE="ntfs" 
/dev/sda2: LABEL="Vista" UUID="189C3....(hidden by me)" TYPE="ntfs" 
/dev/sda3: LABEL="Data" UUID="426235....(hidden by me)" TYPE="ntfs" 
/dev/sda5: UUID="283ff747-a7....(hidden by me)" TYPE="ext4" 
/dev/sda6: UUID="7f0e1b58-bcc....(hidden by me)" TYPE="swap" 
/dev/sdb: LABEL="H^LM-@kU^M-@b^A&#65533;M-b" UUID="5CB7-1501" TYPE="vfat" 
``` I have hidden ID's of other disks to protect against hacking. We don't talk about that disks.

I didn't try to change the label of my microsd because I only can do that in windows not in ubuntu.  And Windows Vista is slow. 

Unmounting via gsm screen is possible but  ubuntu does not see that microsd is unmounted probably because he cannot understand the label.  

If I can change the label (in ubuntu), it would be probably solved.
```


hc@hc-laptop:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/hc/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hc)
/dev/sdb on /media/H
                     type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
hc@hc-laptop:~$ sudo umount <mount_point>
bash: syntax error near unexpected token `newline'
```Not unmounted with these codes.

---

### Post by matt_symes on 2012-07-06
Hi

> /dev/sdb: LABEL="H^LM-@kU^M-@b^A&#65533;M-b" UUID="5CB7-1501" TYPE="vfat"

That does not look right at all.

Have you tried changing the label using gparted ?

You could also try to use mkfs.vfat

```
sudo mkfs.vfat -n "label_name" /dev/sdb
```

The only thing that is worrying me is the device is not partitioned. 

This may not be a problem  though, as i have never used a gsm device under Ubuntu so i am not sure of their format.

I'm sure if anybody else knows for certain then they will contribute to this thread.

Kind regards

---

### Post by harun3d on 2012-07-09
The problem is solved.  As far as I can remember (did the tricks 3 days ago), the solution was:
Ctrl+Alt+T ```
sudo blkid
```look what the name of your media is: e.g. /dev/sdc
```
sudo ntfslabel /dev/sdc yourLabelName
```Rebooting ubuntu necessary

---

### Post by matt_symes on 2012-07-09
Hi

I'm glad you got it fixed :) Thanks for posting back what you did to fix it.

I did not realise the command ntfslabel could change the label on a FAT32 partition which is why i suggested setting the label using mkfs.vfat. I have learnt some thing useful. Thanks :)

Just to cover all the bases in this post for other users who may come across this thread...

From post #3

> 
hc@hc-laptop:~$ sudo umount **<mount_point> **
bash: syntax error near unexpected token `newline'The text <mount_point> needs to be exchanged for the mount point of the device. Let me give you an example.

Below sda10 is mounted at mount point /home/matthew/storage.

```

matthew@matthew-Aspire-7540 ~ % mount | grep sda10 
/dev/sda10 on /home/matthew/storage type ext4 (rw)
matthew@matthew-Aspire-7540 ~ % 
```so to unmount it i could type

```
sudo umount /home/matthew/storage
```

I could have also used the device name 

```
sudo umount /dev/sda10
```

Kind regards

---

