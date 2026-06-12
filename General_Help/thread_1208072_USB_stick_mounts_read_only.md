---
title: "USB stick mounts read only"
date: 2009-07-08
forum: General Help
---

### Post by MacDuff on 2009-07-08
I have a Sandisk Cruiser I am trying to use with Ubuntu 9.04 and it mounts only as Read Only.  It is immediately recognized and mounted at /media/disk but I cannot write to it no matter what I do.

I have tried to chown the drive and chmod but each time I get a message that the drive is read only and I cannot change ownership nor permissions.

It worked with Ubuntu 8.04 and it works with Virtual Windows XP in VirtualBox running on Ubuntu 9.04.   

Any suggestions would be welcome.

---

### Post by munky99999 on 2009-07-08
Does it boot properly?

Simply sounds like presistence isnt working.

Using the built-in usb creator in ubuntu + an iso. You should be able to adjust the "stored in reserved extra space" move it to like max on the bar and it should work.

---

### Post by wojox on 2009-07-08
Are you doing this through the terminal or nautilus?

---

### Post by Jebtrix on 2009-07-08
Post the output from (in terminal):

```

cat /etc/mtab
```

---

### Post by MacDuff on 2009-07-08
Here is the result of cat /etc/mtab


$ cat /etc/mtab
/dev/sda6 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-13-generic/volatile tmpfs rw,mode=755 0 0
none /proc/bus/usb usbfs rw,devgid=46,devmode=664 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
//192.168.0.49/Volume_1 /media/RAID cifs rw,mand 0 0
//192.168.0.49/Volume_2 /media/OnLineBAK cifs rw,mand 0 0
gvfs-fuse-daemon /home/mac/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=mac 0 0
/dev/sdb1 /media/disk vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

---

### Post by synapsys on 2009-07-08
Can you modify it with:

```
sudo nautilus /media/disk
```?

If so, **unmount** it and change ownership of /media/disk.

---

### Post by MacDuff on 2009-07-09
Good Idea but No Joy

When I try your suggestion I get the following:
** (nautilus:3754): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///media/disk

(nautilus:3754): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:3754): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
mac@T-61:~$ 

Mac

---

### Post by MacDuff on 2009-07-10
We can put PAID to this.  The problem appears to be that the SanDisk Cruzer has built-in security that prevents the stick from mounting as read/write on Ubuntu 9.04.  (Oddly it will work perfectly with V. 8.04). 

The solution was to put the stick into a Windows System and re-format the stick to remove the security partition (also removes the data partition).  It now auto-mounts and works as a simple (non secured) USB storage device with read/write privileges.

---

### Post by synapsys on 2009-07-20
The first thing I do when I buy any type of storage media is wipe it. Sorry I was assuming everybody did that. You can implement your own security if you are worried about that. I would use at least 128 bit encryption.

---

### Post by MacDuff on 2009-07-21
Yes that works BUT should not be necessary, at least not if all the dependencies required to work with DOS formated devices are installed.  

It was not necessary with Ubuntu with versions 8.04 and earlier.  Something has changed in later versions which has created complications, not only when using some USB devices but also connecting formerly compatible Network Accessible Storage Devices.

Some people have been able to circumvent the problem with changes to the OS but nothing they have done appears to work on my 9.04 system.

Quel frustration!

---

### Post by synapsys on 2009-07-21
Sounds like it's time to report a bug on launchpad.net eh?

---

### Post by MacDuff on 2009-07-21
> Re: USB stick mounts read only
Sounds like it's time to report a bug on launchpad.net eh? 

Yes but I do not have enough knowledge about the inner workings of Linux to do the type of testing that would produce a good report.

I trust that there are some knowledgeable people watching the forums who, if they confirm it is a problem with the OS rather than just my own stupidity, may add my problem to those reported by others.

This problem with the USB stick would be a major pain if someone wanted to transfer/edit files already on a USB stick using an Ubuntu 9.04 system.  Many would not have the knowledge (nor perhaps the time) to re-format the stick without losing the files on the stick.  these sorts of problem become ever more serious as more and more people, who are not software gurus, are drawn to Ubuntu.  They quickly become disillusioned by a failure of what they consider to be a pretty basic procedure.

In my case a reformat was easy and the problem is solved for now.  

Hopefully future updates to 9.04 will have a patch for the problem.

---

### Post by khughitt on 2009-09-22
Running into same problem after a recent update. I wiped the 4gb usb-stick, and formatted it as ext4. When I mount the usb-stick, however, it shows up as read-only and I cannot copy any files to it. I checked the logs after mounting, and everything appears to be okay:

```

$dmesg | tail

[  898.056017] usb 1-1: new high speed USB device using ehci_hcd and address 4
[  898.193215] usb 1-1: configuration #1 chosen from 1 choice
[  898.221544] Initializing USB Mass Storage driver...
[  898.221664] scsi2 : SCSI emulation for USB Mass Storage devices
[  898.222187] usb-storage: device found at 4
[  898.222191] usb-storage: waiting for device to settle before scanning
[  898.222204] usbcore: registered new interface driver usb-storage
[  898.222253] USB Mass Storage support registered.
[  903.220433] usb-storage: device scan complete
[  903.221426] scsi 2:0:0:0: Direct-Access     PNY      USB 2.0 FD       4096 PQ: 0 ANSI: 0 CCS
[  903.222114] sd 2:0:0:0: Attached scsi generic sg3 type 0
[  903.224159] sd 2:0:0:0: [sdc] 7864320 512-byte logical blocks: (4.02 GB/3.75 GiB)
[  903.224900] sd 2:0:0:0: [sdc] Write Protect is off
[  903.224904] sd 2:0:0:0: [sdc] Mode Sense: 43 00 00 00
[  903.224907] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  903.227770] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  903.227774]  sdc: sdc1
[  903.257269] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  903.257274] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[  903.856215] EXT4-fs (sdc1): barriers enabled
[  903.886250] kjournald2 starting: pid 10174, dev sdc1:8, commit interval 5 seconds
[  903.887824] EXT4-fs (sdc1): internal journal on sdc1:8
[  903.887830] EXT4-fs (sdc1): delayed allocation enabled
[  903.887834] EXT4-fs: file extents enabled
[  903.888176] EXT4-fs: mballoc enabled
[  903.888192] EXT4-fs (sdc1): mounted filesystem with ordered data mode


```

The relevant entry in /etc/mtab also looks okay:

```
/dev/sdc1 /media/Elara ext4 rw,nosuid,nodev,uhelper=devkit 0 0
```

Any help would be greatly appreciated :)

Thanks,

---

