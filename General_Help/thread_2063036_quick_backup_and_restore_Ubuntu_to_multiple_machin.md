---
title: "quick backup and restore Ubuntu to multiple machines"
date: 2012-09-26
forum: General Help
---

### Post by drofzz on 2012-09-26
So i got alot of Lenovo T61 machines, that we often reinstall, as users got root access, they are mostly used to play with (experiment)

i've been doing some stuff to make this easier, as edubuntu takes about 1½ hours to install.

first we bought a Server to serve as a NFS host server, for our backup/restore images 

10.0.0.10:/upload rw
10.0.0.10:/images ro

the uploaded backup/restore images gets moved to images, but does not funktion yet, as we still experiment to get the backup system to work.

i use SystemRescue (er linux live pen, with fsarchive), to boot up on.

does the following to backup:

mkdir /image
mount -o rw,nolock 10.0.0.1:/upload /image
cd /image
mkdir <Type#>
cd <Type#>
dd if=/dev/sda of=mbr.img bs=512 count=1
fsarchiver -v savefs p1.fsa /dev/sda1


now on the next computer i want to restore on, i do the following:

mkdir /image
mount -o ro,nolock 10.0.0.1:/upload /image
cd /image/<Type#>
dd if=mbr.img of=/dev/sda
fsarchiver -v restfs p1.fsa id=0,dest=/dev/sda1
reboot


Now when that is done, and the computer restart, it find the boot all fine.. but when i press it to start ubuntu, it says 
"error: no such partition
 error: no such partition
 error: no such partition"

and i dont come further... did i do anything wrong?

---

### Post by prshah on 2012-09-26
> **drofzz said:**
> 
dd if=/dev/sda of=mbr.img bs=512 count=1


Don;t know about fsarchiver, et al, but you can just use dd as a simple clone/backup tool. In the above example, you are using it to backup MBR and partition table, but you can just as well back up (clone image) the entire drive.

 Boot into a live CD/USB, open the terminal (Dash-Terminal) and

```

#first, turn off active swap partitions
sudo swapoff -a
# ensure any other mounted partitions on your source HDD are unmounted.
#next attach your backup device (ext HDD?) and let it mount
# run the dd command to create a backup image
sudo dd if=/dev/sdX of=/media/backupdevice/dd_image bs=32M 
# when it is done (will take a long time), unmount your ext hdd
sudo umount /media/backupdevice

```

To restore the image, again boot into a live CD/USB, with blank HDD attached. Plug in the ext HDD, and open the terminal```

#first, turn off active swap partitions
sudo swapoff -a
# ensure any other mounted partitions on your target HDD are unmounted.
# run the dd command to restore a backup image
sudo dd of=/dev/sdX if=/media/backupdevice/dd_image bs=32M 
# when it is done (will take a long time), unmount your ext hdd
sudo umount /media/backupdevice
#and reboot
sudo reboot
```
You should be able to boot successfully without any other action required.

If your new (target) HDD is larger than the source HDD, you can resize the partitions using gparted from the live CD/USB.

You cannot use this method (without problems) if the target HDD is smaller than the source HDD.

To check the progress (dd has no progress indicator), open a fresh terminal and issue a USR1 kill signal to the dd process```

#find dd processid
sudo ps -e|grep dd
#issue USR1 signal, replace xxx with dd process id
sudo kill -USR1 xxx

```
 Note that progress report may be delayed a few seconds (delay depends on your "bs" setting in dd).

---

### Post by oldfred on 2012-09-26
If you are booting with grub2, it also has core.img in the sectors from the MBR to the first partition. Your are probably missing core.img. You could reinstall grub2 to reinstall a valid core.img or image entire drive as suggested by prshah.

While mostly about using gpt rather than MBR, it explains why with gpt a  bios_grub partition is required for core.img and where it is in MBR partitioning. 
[https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)

---

