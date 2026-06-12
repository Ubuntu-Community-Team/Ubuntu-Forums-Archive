---
title: "HELP Error occurred while mounting!"
date: 2011-03-01
forum: General Help
---

### Post by sokekoke on 2011-03-01
When i boot my ubuntu 10.10 i get:
"An error occurred while mounting"
"Press S to skip mounting or M for normal recovery"

If i press "S" or "M" ubuntu mount my ext4 drive as readonly, so i can't change anything. 
If i boot form livecd and mount the filesystem i can edit files.

The last thing i remember doing yesterday was mounting a FTP drive in nautilus, so i'm guessing that's the source of evil. I also ran the command "sudo apt-get build-dep wine" before i shutdown my computer.

If i look at my /etc/fstab it says:
UIID=45058d9d-4ef2-4ccf-b587-0eba53e61d06 / ext4 error=remount -ro 0 1

Help much appreciated, so i can go back to work.

Thanks

Stuff i tried:
UIID=45058d9d-4ef2-4ccf-b587-0eba53e61d06 / ext4 rw 0 1 (still can't mount)

---

### Post by sokekoke on 2011-03-01
bump

---

### Post by TeoBigusGeekus on 2011-03-01
Have you tried fsck-ing your partition from the live cd?

---

### Post by sokekoke on 2011-03-01
> **TeoBigusGeekus said:**
> Have you tried fsck-ing your partition from the live cd?

I have no experience with this, could  you explain what i should try doing? In the meantime i will google for my life!

---

### Post by TeoBigusGeekus on 2011-03-01
Boot up with a live cd, open terminal and
```
sudo fsck /dev/whatever
```
It will check your partition for errors and attempt to fix them.

---

### Post by matt_symes on 2011-03-01
Hi

```
UIID=45058d9d-4ef2-4ccf-b587-0eba53e61d06 / ext4 error=remount -ro 0 1
```

change to (Changed items highlighted in bold)

```
**UUID**=45058d9d-4ef2-4ccf-b587-0eba53e61d06 / ext4 **errors**=**remount-ro** 0 1
```

To run fdisk boot into the livecd, ensure the drive is not mounted and then goto System->Administration->Disk utility. Select the drive and partition and select check file system.

Kind regards

---

### Post by sokekoke on 2011-03-01
It takes a war to reboot from the live cd so please have patience, i will post results as soon as i can!

---

### Post by sokekoke on 2011-03-01
Ok when i check my filesystem it says that it's clean.

I changed the line in fstab and rebooted, but problem prevails.

Bad feeling increasing :p

---

### Post by matt_symes on 2011-03-01
Hi

From the terminal post the whole file

```
cat /etc/fstab
```

also post the results of

```
sudo blkid -c /dev/null
```

Enter your password. You will not see it echoed to the screen.

Kind regards

---

### Post by sokekoke on 2011-03-01
cat /etc/fstab

```
ubuntu@ubuntu:/media/45058d9d-4ef2-4ccf-b587-0eba53e61d06$ cat etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=45058d9d-4ef2-4ccf-b587-0eba53e61d06 /               ext4    errors=remount-ro 0       1

# swap was on /dev/sda3 during installation
UUID=c763222d-188e-4056-8eac-c3209e2c681c none            swap    sw              0       0

UUID=e028cf56-7195-4513-8c29-72356e25a0bd  /media/DATA ext4 defaults 0 2

```

sudo blkid -c /dev/null

```
ubuntu@ubuntu:/media/45058d9d-4ef2-4ccf-b587-0eba53e61d06$  sudo blkid -c /dev/null
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="DATA" UUID="e028cf56-7195-4513-8c29-72356e25a0bd" TYPE="ext4" 
/dev/sda2: UUID="45058d9d-4ef2-4ccf-b587-0eba53e61d06" TYPE="ext4" 
/dev/sda3: UUID="c763222d-188e-4056-8eac-c3209e2c681c" TYPE="swap" 
```

---

### Post by sokekoke on 2011-03-01
> **matt_symes said:**
> Hi

From the terminal post the whole file

```
cat /etc/fstab
```

also post the results of

```
sudo blkid -c /dev/null
```

Enter your password. You will not see it echoed to the screen.

Kind regards

if you need me to post any more commands or anything ill gladly do so, wild guesses are also much appreciated

---

### Post by matt_symes on 2011-03-01
Hi

```
# / was on /dev/sda2 during installation
UUID=45058d9d-4ef2-4ccf-b587-0eba53e61d06 /               ext4    errors=remount-ro 0       1

# swap was on /dev/sda3 during installation
UUID=c763222d-188e-4056-8eac-c3209e2c681c none            swap    sw              0       0

UUID=e028cf56-7195-4513-8c29-72356e25a0bd  /media/DATA ext4 defaults 0 2

... line removed
H7ETJ2GS@ws37
```

```
... line removed
H7ETJ2GS@ws37
```

Is that split over 2 lines. Try commenting them out by puting a **#** in front of each so they become..

```
# ... line removed
# H7ETJ2GS@ws37
```

Apart from that i cannot see much wrong with your fstab. As an example here is mine.

```
matthew@matthew-laptop:/mnt/arch$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sda5 during installation
UUID=3d48429c-7361-4ab8-8689-54407673b141 /               ext4    errors=remount-ro 0       1

# swap was on /dev/sda6 during installation
UUID=b1c6171a-075e-4291-af69-64baf751d10e none            swap    sw              0       0

UUID=6f865ee1-c098-45e2-9c40-faf230218c4b /home/matthew/data ext4 defaults,auto,noatime 0 1
matthew@matthew-laptop:/mnt/arch$ 
```

How did you run the fsck check ? Was it from the command line or from the Disk Utility application ?

Kind regards

---

### Post by sokekoke on 2011-03-01
> **matt_symes said:**
> Hi

```
# / was on /dev/sda2 during installation
UUID=45058d9d-4ef2-4ccf-b587-0eba53e61d06 /               ext4    errors=remount-ro 0       1

# swap was on /dev/sda3 during installation
UUID=c763222d-188e-4056-8eac-c3209e2c681c none            swap    sw              0       0

UUID=e028cf56-7195-4513-8c29-72356e25a0bd  /media/DATA ext4 defaults 0 2

[CODE]
H7ETJ2GS@ws37
```

Is that split over 2 lines. Try commenting them out by puting a **#** in front of each so they become..

```
# 
# H7ETJ2GS@ws37
```

Apart from that i cannot see much wrong with your fstab. As an example here is mine.

```
matthew@matthew-laptop:/mnt/arch$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sda5 during installation
UUID=3d48429c-7361-4ab8-8689-54407673b141 /               ext4    errors=remount-ro 0       1

# swap was on /dev/sda6 during installation
UUID=b1c6171a-075e-4291-af69-64baf751d10e none            swap    sw              0       0

UUID=6f865ee1-c098-45e2-9c40-faf230218c4b /home/matthew/data ext4 defaults,auto,noatime 0 1
matthew@matthew-laptop:/mnt/arch$ 
```

How did you run the fsck check ? Was it from the command line or from the Disk Utility application ?

Kind regards

**THANK YOU for pointing that out!**
H7ETJ2GS@ws37 was a remnant! removed it fixed my problems.. god thank you so much! back to work =)

---

### Post by matt_symes on 2011-03-01
Hi

Don't work too hard ;)

Kind regards

---

