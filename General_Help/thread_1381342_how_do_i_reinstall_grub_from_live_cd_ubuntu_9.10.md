---
title: "how do i reinstall grub from live cd ubuntu 9.10"
date: 2010-01-14
forum: General Help
---

### Post by dodo_dodder on 2010-01-14
hello,
 I had windows XP on my c:\drive. installed ubuntu 9.10 on a 27 gig unallocated space. ubuntu ran fine. Then i boot to win xp and used a partitioning software to take back some other unallocated space. after it rebooted to complete the partitioning processes grub wouldn't load. So i need to re install grub from this ubuntu 9.10 live cd.
i tired the following
grub
(didnt work the first time said i needed to install grub so did : root@ubuntu:~# sudo apt-get install grub )
after grub was installed
grub> find /boot/grub/stage1 

Error 15: File not found



the previous linux partition I can see in the Computer with the boot directory and is called 1000gb hard disk: 27 GB filesystem see screenshot.

HELP![IMG]http://i739.photobucket.com/albums/xx38/dodo_dodder/Screenshot.png[/IMG]

---

### Post by Leppie on 2010-01-14
could you please post the output of the following command:
```
sudo fdisk -l
```

---

### Post by 73ckn797 on 2010-01-14
Look down the page here [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2) until you find
Recover Grub 2 via LiveCD then follow the steps.

---

### Post by dodo_dodder on 2010-01-14
root@ubuntu:~# sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x71f3c0d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       61192   471041865    7  HPFS/NTFS
/dev/sda3           61193      104934   351357615    7  HPFS/NTFS
/dev/sda4          104935      121601   133877677+   f  W95 Ext'd (LBA)
/dev/sda5          104935      110532    44965903+   7  HPFS/NTFS
/dev/sda6          110533      113763    25952976   83  Linux
/dev/sda7          113764      113908     1164681   82  Linux swap / Solaris
/dev/sda8          117106      119307    17679532    7  HPFS/NTFS
/dev/sda9          119308      121601    18426523+   7  HPFS/NTFS
root@ubuntu:~# sudo mount /dev/sda6 /mnt
root@ubuntu:~# sudo mount --bind/dev /mnt/dev
mount: unrecognized option '--bind/dev'
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
root@ubuntu:~# sudo chroot /mnt
root@ubuntu:/# nano /etc/default/grub
root@ubuntu:/# update-grub
grub-probe: error: cannot find a device for /.

root@ubuntu:/# grub-install --recheck/dev/sda
Unrecognized option `--recheck/dev/sda'
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-mkdevicemap=FILE use FILE as grub-mkdevicemap
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specified by
--root-directory, and uses grub-setup to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.
root@ubuntu:/# update-grub
grub-probe: error: cannot find a device for /.

root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu
grub-probe: error: cannot find a device for /.

root@ubuntu:/# $ sudo mount --bind /proc /mnt/proc
$: command not found
root@ubuntu:/# mount --bind /proc /mnt/proc
mount: mount point /mnt/proc does not exist
root@ubuntu:/# mount --bind /proc /mnt/sys
mount: mount point /mnt/sys does not exist


------------------------------------------------------------------------------

is all i tried. terminal is so cool :D

---

### Post by dodo_dodder on 2010-01-14
while you guys are at it, can you tell me if there is a way to install ubuntu_restricted_package while im on the live disc so that it I don't have to re do it everytime i restart? Currently this crisis calls for many restarts, and i am downloading the packages on every restart for music. and I cant get through this without music. 
This is Ubuntu 9.10 - the Karmic Koala.

---

### Post by mechro on 2010-01-14
> **dodo_dodder said:**
> while you guys are at it, can you tell me if there is a way to install ubuntu_restricted_package while im on the live disc so that it I don't have to re do it everytime i restart? Currently this crisis calls for many restarts, and i am downloading the packages on every restart for music. and I cant get through this without music. 
This is Ubuntu 9.10 - the Karmic Koala.

Nope. It's a read only CD.

---

### Post by Leppie on 2010-01-14
> **dodo_dodder said:**
> root@ubuntu:~# sudo fdisk -l
the prompt indicates that you have a root shell. both "root@" and "#" indicate the root shell. the root shell does not require the "sudo" command ;)

install grub2 to the mbr:
```
# mount /dev/sda6 /mnt
# grub-install --recheck --root-directory=/mnt /dev/sda
```

---

### Post by dodo_dodder on 2010-01-14
i was hoping since it had access to the hard drive it could write something. but okay
I just wont restart as long as i can.

---

### Post by dodo_dodder on 2010-01-14
root@ubuntu:/# mount /dev/sda6 /mnt
mount: you must specify the filesystem type


is what i got.

---

### Post by Leppie on 2010-01-14
> **dodo_dodder said:**
> i was hoping since it had access to the hard drive it could write something. but okay
I just wont restart as long as i can.
if you followed the instructions correctly, you would be able to install the restricted package:
```
sudo -i
mount /dev/sda6 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
apt-get install ubuntu-restricted-extras
grub-install --recheck --root-directory=/mnt /dev/sda
exit
```

---

### Post by dodo_dodder on 2010-01-14
"i was hoping since it had access to the hard drive it could write something. but okay
I just wont restart as long as i can." was addressed to mechro for the restricted_packages thing. is it related to the grub problem?
sudo -i
mkdir -p /mnt/temp/boot
mount /dev/sda6 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
apt-get install ubuntu-restricted-extras
grub-install --recheck --root-directory=/mnt /dev/sda
exitI  have already installed the restricted packages, do i need to install them again?

---

### Post by dodo_dodder on 2010-01-14
@leppie

root@ubuntu:/# mkdir -p /mnt/temp/boot
root@ubuntu:/# mount /dev/sda6 /mnt/temp/
mount: you must specify the filesystem type



is what i got

---

### Post by Leppie on 2010-01-14
> **dodo_dodder said:**
> I  have already installed the restricted packages, do i need to install them again?
at what stage did you install the package?
if you did it before chrooting, you will have to do it again.

---

### Post by Leppie on 2010-01-14
> **dodo_dodder said:**
> @leppie

root@ubuntu:/# mkdir -p /mnt/temp/boot
root@ubuntu:/# mount /dev/sda6 /mnt/temp/
mount: you must specify the filesystem type



is what i got
then specify the filesystem type using the "-t" option:
```
mount -t ext4 /dev/sda6 /mnt/temp/
```
unless you used ext3, then amend the command

---

### Post by dodo_dodder on 2010-01-14
do you mean that if i chroot and then reinstall restricted packages, then i dont need to install them again on restart. note that i am booting from a live cd.(unless you guys fix my grub)

---

### Post by dodo_dodder on 2010-01-14
root@ubuntu:/# mount -t ext4 /dev/sda6 /mnt/temp/
mount: special device /dev/sda6 does not exist


:(

---

### Post by Leppie on 2010-01-14
> **dodo_dodder said:**
> do you mean that if i chroot and then reinstall restricted packages, then i dont need to install them again on restart. note that i am booting from a live cd.(unless you guys fix my grub)
well, if you followed and executed the instructions properly and you installed the package after chrooting you should've installed it on your ubuntu system (hence, not the livecd system).

---

### Post by Leppie on 2010-01-14
> **dodo_dodder said:**
> root@ubuntu:/# mount -t ext4 /dev/sda6 /mnt/temp/
mount: special device /dev/sda6 does not exist


:(
did you exit after that last root session, or did you just try to mount /dev/sda6 again?

---

### Post by dodo_dodder on 2010-01-14
i didnt exit the terminal.. and i dont know how to exit the last root session, if they are different things. do i need to exit?

---

### Post by Leppie on 2010-01-14
> **dodo_dodder said:**
> i didnt exit the terminal.. and i dont know how to exit the last root session, if they are different things. do i need to exit?
well, if you did not exit the root session (this could be done by either closing the terminal or issuing the "exit" command), you are still working in your ubuntu system.
i would suggest to close that terminal, so to clear that session, and follow the instructions.

---

### Post by dodo_dodder on 2010-01-14
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount /dev/sda6 /mnt/temp
mount: mount point /mnt/temp does not exist
root@ubuntu:~# mount /dev/sda6 /mnt/temp/
mount: mount point /mnt/temp/ does not exist
root@ubuntu:~# 

on a fresh terminal, previous terminal quit.

---

### Post by Leppie on 2010-01-14
i'm sorry, i left out the mkdir command:
```
sudo -i
mkdir /mnt/temp
mount /dev/sda6 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
apt-get install ubuntu-restricted-extras
grub-install --recheck --root-directory=/mnt /dev/sda
exit
```
if you're still in the root shell, then don't issue the "sudo -i" command.

---

### Post by dodo_dodder on 2010-01-14
What now?

---

### Post by Leppie on 2010-01-14
> **dodo_dodder said:**
> What now?
already did the whole process?
you're fast...

---

### Post by dodo_dodder on 2010-01-14
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount /dev/sda6 /mnt/temp
mount: mount point /mnt/temp does not exist
root@ubuntu:~# mount /dev/sda6 /mnt/temp/
mount: mount point /mnt/temp/ does not exist
root@ubuntu:~# mkdir /mnt/tmp
mkdir: cannot create directory `/mnt/tmp': File exists
root@ubuntu:~# 


now its taunting me.

---

### Post by dodo_dodder on 2010-01-14
> **Leppie said:**
> already did the whole process?
you're fast...
 "what now"  was just an impatient reaction

---

### Post by Leppie on 2010-01-14
ah... lol

---

### Post by Leppie on 2010-01-14
> **dodo_dodder said:**
> ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount /dev/sda6 /mnt/temp
mount: mount point /mnt/temp does not exist
root@ubuntu:~# mount /dev/sda6 /mnt/temp/
mount: mount point /mnt/temp/ does not exist
root@ubuntu:~# mkdir /mnt/tmp
mkdir: cannot create directory `/mnt/tmp': File exists
root@ubuntu:~# 


now its taunting me.
you're mixing up things:
```
mount: mount point /mnt/**_*temp*_**/ does not exist
root@ubuntu:~# mkdir /mnt/***_tmp_***
```
you have the folder /mnt/tmp but are mounting to /mnt/temp

---

### Post by dodo_dodder on 2010-01-14
root@ubuntu:~# mkdir /mnt/tmp
mkdir: cannot create directory `/mnt/tmp': File exists
root@ubuntu:~# mount /dev/sda6 /mnt/temp
mount: mount point /mnt/temp does not exist
root@ubuntu:~# 

it seems tmp dir is not a 'mount point'.

---

### Post by dodo_dodder on 2010-01-14
"you have the folder /mnt/tmp but are mounting to /mnt/temp" can i mount to the tmp folder now? or should i make temp and mout to temp?

---

### Post by Leppie on 2010-01-14
> **dodo_dodder said:**
> root@ubuntu:~# mkdir /mnt/tmp
mkdir: cannot create directory `/mnt/tmp': File exists
root@ubuntu:~# mount /dev/sda6 /mnt/temp
mount: mount point /mnt/temp does not exist
root@ubuntu:~# 

it seems tmp dir is not a 'mount point'.
if you are creating the folder /mnt/tmp (no "e" in tmp) as mount point, then you cannot mount to /mnt/temp (with "e" in temp).

---

### Post by dodo_dodder on 2010-01-14
root@ubuntu:~# mkdir /mnt/temp
root@ubuntu:~# mount /dev/sda6 /mnt/temp
root@ubuntu:~# mount -o bind /proc /mnt/temp/proc
root@ubuntu:~# mount -o bind /dev /mnt/temp/dev
root@ubuntu:~# mount -o bind /dev/pts /mnt/temp/dev/pts
root@ubuntu:~# mount -o bind /sys /mnt/temp/sys
root@ubuntu:~# chroot /mnt/temp
root@ubuntu:/# 


-----------
do i need to install restricted packages? i have it on my original ubuntu installation(on sda6). it takes a long time, slow internet.

---

### Post by dodo_dodder on 2010-01-14
root@ubuntu:~# mount -o bind /proc /mnt/temp/proc
root@ubuntu:~# mount -o bind /dev /mnt/temp/dev
root@ubuntu:~# mount -o bind /dev/pts /mnt/temp/dev/pts
root@ubuntu:~# mount -o bind /sys /mnt/temp/sys
root@ubuntu:~# chroot /mnt/temp
root@ubuntu:/# grub-install --recheck --root-directory=/mnt /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
root@ubuntu:/# 



-----------------
grub is installed with no errors it says.I didn't install the restricted packages(took a chance because grub wasn't likely to be 'restricted'). should i install them now so that if grub doesnt work and i need to come back to the live cd i can play some tunes?

---

### Post by dodo_dodder on 2010-01-14
root@ubuntu:/# apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 125 not upgraded.
root@ubuntu:/# 


---------------------
sweet. I think its done. it says its already installed :D. Is it detecting the restricted packages of the sda 6 installation or the one i am using right now?

---

### Post by rodrigo.toste.gomes on 2010-01-14
Your replies are confusing xD
If you fixed grub, you no longer need the live cd.
Just use the fully installed OS.
In that one, any change you make (like installing restricted extras) is permanent, so you only have to install them once.
So, just enjoy your system!

---

### Post by dodo_dodder on 2010-01-14
"If you fixed grub, you no longer need the live cd.
Just use the fully installed OS."

it doesnt boot into the os or show os selection. just displays grub prompt. grub gnu 1.93. I typed exit and it asked for boot media.

---

### Post by rodrigo.toste.gomes on 2010-01-14
Ok.
Reboot the system through the live CD, and copy exactly the commands that I'm going to put here!
Don't try to write them even, to make sure there are no errors!
Just copy and paste them:

sudo mount /dev/sda6 /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
update-grub
grub-install /dev/sda
exit
sudo umount /mnt/dev
sudo umount /mnt

And then you can reboot the system, and experiment again.
Hopefuly this solves any problems :P
And please put the full output these commands give you here, so we can analyze where it goes wrong.

---

### Post by dodo_dodder on 2010-01-14
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
done
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev
ubuntu@ubuntu:~$ sudo umount /mnt
ubuntu@ubuntu:~$ 


--------------------------------
rebooting. any chance of getting xp installation back? have some unfinished torrents to attend to :P

---

### Post by dodo_dodder on 2010-01-14
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!

??
do i need this command : root@ubuntu:~# mount -o bind /proc /mnt/temp/proc

---

### Post by dodo_dodder on 2010-01-14
should I reboot or is that error okay?

---

### Post by Leppie on 2010-01-15
> **dodo_dodder said:**
> "If you fixed grub, you no longer need the live cd.
Just use the fully installed OS."

it doesnt boot into the os or show os selection. just displays grub prompt. grub gnu 1.93. I typed exit and it asked for boot media.
you're posts are confusing too... :P
do you have grub v 1.93 installed?
you can check the version like this:
```
sudo grub-install -v
```

---

### Post by Leppie on 2010-01-15
> **dodo_dodder said:**
> grep: /proc/mounts: No such file or directory
Cannot find list of partitions!

??
do i need this command : root@ubuntu:~# mount -o bind /proc /mnt/temp/proc
this errore:
```
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
```
is because you didn't mount /proc

---

### Post by Leppie on 2010-01-15
please try the following (all commands :P):
```
sudo -i
mkdir /mnt/temp
mount /dev/sda6 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
apt-get purge grub grub-pc grub-common
apt-get install grub-pc grub-common
exit
```

---

### Post by dodo_dodder on 2010-01-15
i reinstalled ubuntu on sda6. and its dual booting now :)

---

### Post by Leppie on 2010-01-15
good, glad the issue is solved :)

---

