---
title: "Hard drives keep reversing positions"
date: 2012-04-04
forum: General Help
---

### Post by MichaelGld on 2012-04-04
I have two hard disks, named sda and sdb. It appears that the physical drives switch position on every reboot. I discovered this via hddtemp.
```

On 4/3/2012
termmichael@michael-desktop:~$ sudo hddtemp /dev/sda
[sudo] password for michael: 
/dev/sda: WDC WD5000AAKX-001CA0: 34°C
michael@michael-desktop:~$ sudo hddtemp /dev/sdb
/dev/sdb: ST3500630AS: 34°C

On 4/4/2012
michael@michael-desktop:~$ sudo hddtemp /dev/sda
[sudo] password for michael: 
/dev/sda: ST3500630AS: 24°C
michael@michael-desktop:~$ sudo hddtemp /dev/sdb
/dev/sdb: WDC WD5000AAKX-001CA0: 25°C
michael@michael-desktop:~$ 
```Does anyone know why this is happening and how to fix it?

Thanks.

---

### Post by cryptotheslow on 2012-04-04
Why it is happening? Probably slight changes in drive initialisation times between boots causing the order they become ready and detected to reverse.

How to solve? Define the disks by UUID rather than /dev/sdX in your fstab.

If you need a hand with that post back with the output to these two commands:

```
cat /etc/fstab

sudo blkid

```

---

### Post by MichaelGld on 2012-04-04
Thanks for your reply. Yes, I do need help with that. Here is the data you requested.


```
michael@michael-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=1d19060b-2349-4857-b6c1-c550fdda0097 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=1740c274-3369-4498-91e0-6c789f015c8b /boot           ext4    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=0b8f28be-9562-4ccf-aec5-807f4e339925 /home           ext4    defaults,user_xattr        0       2
/dev/sdb5       none            swap    sw              0       0
``````
michael@michael-desktop:~$ sudo blkid
[sudo] password for michael: 
/dev/sda1: UUID="0CEE3E283AC284FF" TYPE="ntfs" 
/dev/sda2: LABEL="New DATA" UUID="449C80469C803488" TYPE="ntfs" 
/dev/sda5: LABEL="New DOWNLOADS" UUID="4266B53A66B52F91" TYPE="ntfs" 
/dev/sdb1: UUID="1740c274-3369-4498-91e0-6c789f015c8b" TYPE="ext4" 
/dev/sdb5: UUID="7702a57b-17e9-41e0-9c14-67a04381fe90" TYPE="swap" 
/dev/sdb6: UUID="1d19060b-2349-4857-b6c1-c550fdda0097" TYPE="ext4" 
/dev/sdb7: UUID="0b8f28be-9562-4ccf-aec5-807f4e339925" TYPE="ext4" 
/dev/sdc1: LABEL="ProDrive" UUID="4ED018EDD018DD51" TYPE="ntfs" 
```I became aware of this because of my use of the hddtemp command to extract the temperature information from the drives, and pulling that data into Conky.

I really appreciate your help!

---

### Post by cryptotheslow on 2012-04-04
Ah - OK, sda is not defined in fstab at all.

Can you post up the output to this as well please:
```

sudo mount -l

```

That's a lowercase L at the end not a number one :D

---

### Post by MichaelGld on 2012-04-04
Okay, sure.

```
michael@michael-desktop:~$ mount -l
/dev/sdb6 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sdb1 on /boot type ext4 (rw,commit=0)
/dev/sdb7 on /home type ext4 (rw,user_xattr,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)
/dev/sdc1 on /media/ProDrive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) [ProDrive]
/dev/sda1 on /media/0CEE3E283AC284FF type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```

---

### Post by flemur13013 on 2012-04-04
I had that happen, and I *think* I made it go away with a disk-order setting in BIOS. 
(I'm not sure this fixed it, or if it just stopped changing).

You might also want to use LABEL or UUID to identify partitions in /etc/fstab (the last line in your fstab - for swap - could use this: make it UUID like the line above). This won't necessarily fix the a/b changing, but your swap should mount regardless of the order, since it won't refer to sda/b ).

---

### Post by cryptotheslow on 2012-04-04
Do "New DATA" and "New DOWNLOADS" also appear in /media when you access those?

Also is the disk that sda1, 2 and 5 sit on permanently installed in the machine or removable (usb etc.) ?

Just asking as typically for a permanently installed drive we would mount the partitions into /mnt rather than /media. Not that it really matters and changing their mount points now is going to mess up any applications you have that are set to access them at their current locations (e.g. media app  indexes).

---

### Post by cryptotheslow on 2012-04-04
Actually I think I have gone off on the wrong tangent here - mounting the partitions by UUID using fstab isn't going to alter the assignment of the physical devices to /dev/sda or sdb, that will still depend what order they initialise in. More thought required here by me :(

---

### Post by 23dornot23d on 2012-04-04
I have this - because I have different boot menus on each drive ..... and

on cold boot .... a   b 

on warm boot ..... b   a

It actually works to my advantage as after a cold boot - to change to the other 
drive I just warm reboot/restart and doing it this way as a warm boot automatically
goes to the other system on the other drive ......

.... usually with two USB HDs attached  though ..... and using a Acer Motherboard ..... 
not sure if its Linux or the BIOS that somehow swaps the order though.

I have no internal drive at all on this laptop though ..... just runs from 2 external
USB drives 

laptop Acer Aspire 7730

( It is consistent and does the same thing everytime though ..... and the USB hard drives never get detatched ..........)

---

### Post by MichaelGld on 2012-04-04
> **cryptotheslow said:**
> Do "New DATA" and "New DOWNLOADS" also appear in /media when you access those?

Also is the disk that sda1, 2 and 5 sit on permanently installed in the machine or removable (usb etc.) ?

Just asking as typically for a permanently installed drive we would mount the partitions into /mnt rather than /media. Not that it really matters and changing their mount points now is going to mess up any applications you have that are set to access them at their current locations (e.g. media app  indexes).

Yes,  both "New DATA" and "New DOWNLOADS" appear in /media when I access them. 

Both sda and sdb are 'permanently' installed. They are both connected to SATA connectors on the motherboard.  I recently did a fresh install of Natty on one of the drives. Windows 7 Ultimate is installed on the other drive.  I *really* don't want to mess up my applications.

Thanks.

---

### Post by redmk2 on 2012-04-04
> **cryptotheslow said:**
> Actually I think I have gone off on the wrong tangent here - mounting the partitions by UUID using fstab isn't going to alter the assignment of the physical devices to /dev/sda or sdb, that will still depend what order they initialise in. More thought required here by me :(

The /dev/sd<whatever> is assigned when the devices are enumerated (upon bootup).  This can change.  The UUID or label will not change upon boot or reboot.

Consider ```
sda1 = UUID 123456789 = label = boot
or 
sda2 = UUID 123456789 = label = boot
```

These are the same partition but the kernel has assigned a different /dev name.

If you mount this partition by either UUID or label you will be fine, but if you mount it by /dev name you could get the wrong partition mounted at the wrong place.

---

### Post by redmk2 on 2012-04-04
> **MichaelGld said:**
> Both sda and sdb are 'permanently' installed. 

Be careful here.  The names sda and sdb can change.  :-)

Edit:  What would happen if you added a USB stick and it was given the name /dev/sda1 ?

---

### Post by MichaelGld on 2012-04-04
> **flemur13013 said:**
> I had that happen, and I *think* I made it go away with a disk-order setting in BIOS. 
(I'm not sure this fixed it, or if it just stopped changing).

You might also want to use LABEL or UUID to identify partitions in /etc/fstab (the last line in your fstab - for swap - could use this: make it UUID like the line above). This won't necessarily fix the a/b changing, but your swap should mount regardless of the order, since it won't refer to sda/b ).

I already have set the Linux drive as first in the boot order in the BIOS; that's where GRUB is installed.

I don't have a problem with the swap (or any other) partition mounting, it's just the sda/sdb assignment.

Thanks for the reply.

---

### Post by jerome1232 on 2012-04-04
In short, your not going to fix it. The /dev assignments dance around with some bios's. If it really bugs you refer to the drives by file system label or uuid.

---

### Post by ridetheteapot on 2012-04-04
hey bro, if you haven't got it yet I suggest skimming through this guide : [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

You can assign device names to hardware with udev rules -- it has nothing to do with label or uuid. Those are automagiclly created udev rules BTW, ie. /dev/disk/* are udev links (see built in persistant naming in above guide).

After you've got the jist check out the section 'udevinfo'.

---

### Post by cryptotheslow on 2012-04-04
@ridetheteapot - is it possible to use udev rules to reassign or fix /dev/* assignments during boot? Just thinking it may not be sane if the / filesystem is already mounted.

Genuine question I don't know the answer to. :)

---

### Post by ridetheteapot on 2012-04-04
yea, if by before boot you mean after grub/lilo.

This really should do it for you. I had the same type problem awhile back.

---

