---
title: "Extra HDD no longer mounts"
date: 2009-08-19
forum: General Help
---

### Post by PlayLoud on 2009-08-19
Hi all,

I am having a problem...

I have been using this computer (Ubuntu 64-bit) as a dedicated folding@home/fileserver machine. Today, I was trying to access the file server (via SAMBA), and I could not connect. So, I go to the computer, and I see that my file server drive (a 1TB Western Digital internal HDD) is not mounted.

I do not know exactly when this happened. It is POSSIBLE it happened on my last reboot, as I did not check to see if the drive was mounted. However, rebooting again does not seem to fix the problem.

When I try to mount the drive, I get an error.

[IMG]http://img.photobucket.com/albums/1003/playloud/One%20Time%20Use/ext4nomount.jpg[/IMG]


Here is my fstab> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc         defaults                    0  0  
# / was on /dev/sda5 during installation
UUID=d1d559e5-a8dc-40db-8e2b-68c14366341b  /                ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda6 during installation
UUID=c48d40df-4fd2-4cbf-867d-a36fa62ad023  none             swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0    udf,iso9660  user,noauto,exec,utf8       0  0  
**/dev/sdb1                                  /media/ext4Tera  ext4         users,user,owner            0  0**  The system has been sitting untouched for a while. It just runs folding@home, and SAMBA. Now and then I will check on it and download any updates that may be available, but that's about it.

The drive is a Western Digital Caviar Green WD10EADS 1TB 32MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive. It is ext4 formatted, and has been pretty flawless up to this point.

Does anybody have any thoughts on what may be going on? I have hundreds of Gigs of stuff on that drive, and would really not like to lose it. I am afraid I do not know a whole lot about Linux. I pretty much learned how to get folding@home running, and how to set up SAMBA, as that is all I really need it for.

Thank you in advance,
PlayLoud

---

### Post by jwaffolter on 2009-08-19
Can you tell me what kernel version your running on?
the kernel version can be found in the System Monitor application under System->Administration

---

### Post by PlayLoud on 2009-08-20
Kernel Linux 2.6.28-15-generic

I tried booting under older versions of 2.6.28, but no dice. I tried to whatever was the default kernel that came with Ubuntu 9.04 (might have been 2.6.28-11, but I would have to go back into GRUB to find that for sure).

---

### Post by jwaffolter on 2009-08-20
Open a terminal; under Applications->Accessories   and type
sudo mount /dev/sdb1

and post the error message

---

### Post by PlayLoud on 2009-08-20
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
           missing codepage or helper program, or other error
                  In some cases useful info is found in syslog - try
                  dmesg | tail  or so

---

### Post by jwaffolter on 2009-08-20
There's one possible cause of this, and it isn't pretty. It depends on how long you were running the 2.6.28-11 kernel.
The 28-11 kernel has been know to cause filesystem corruption on 64-bit systems [link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691")
Most likely your personal data is still intact

Try running the following in the terminal

sudo fsck.ext4 -v /dev/sdb1
this should give up more info

---

### Post by PlayLoud on 2009-08-20
> 
jim@The-QuadFather:~$ sudo fsck.ext4 -v /dev/sdb1
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext4: Group descriptors look bad... trying backup blocks...
Group descriptor 0 checksum is invalid.  Fix<y>? 
I said yes, but it just kept asking me for each checksum. I stopped saying yes at about 400, and canceled. It looks like it goes to 7452 checksums.

**EDIT:** Also, I don't think I was on the old kernel very long. In fact, IIRC, I reformatted the main drive a while back, and I would have updated to the latest kernel immediately after installation.

---

### Post by jwaffolter on 2009-08-20
adding -y to the command will auto answer

this is about as far as my knowledge goes, if your lucky fsck will fix the problem and and you can try remounting the drive

---

### Post by PlayLoud on 2009-08-20
I thank you for your help.

I just held in the enter button to all 7452 checksums, and when it finished, I got this message...

> 
ext4 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes


I don't really know where to go from here.

---

### Post by PlayLoud on 2009-08-20
Anybody else have any thoughts?

---

### Post by PlayLoud on 2009-08-23
Going to try one last time before I reformat, and lose my data.

Anybody have any thoughts on this?

---

### Post by PlayLoud on 2009-08-26
Ha!

I was able to repair the file system with Gparted!

Though, now there is a lost&found folder on the drive, which it says I don't have permission to access. I don't know if that is causing me storage space, and I don't know if any of my files have been corrupted.

As a lot of the data is video, is there any way to check for file damage, other than playing all the videos?

---

### Post by MartinEve on 2009-08-26
You should be able to get into the lost+found folder via the terminal and sudo:

```

sudo ls /path/to/mount/lost+found/

```

Alternatively, launch your file browser with sudo permissions.

---

### Post by PlayLoud on 2009-08-26
Thanks MartinEve. I'll give that a try.

---

### Post by PlayLoud on 2009-08-27
Hmm. The folder was empty. I don't know why it was created if there was nothing in it =)

---

### Post by scouser73 on 2009-08-27
Here is a tutorial on mounting an external hard drive: [[COLOR="Red"]**Mount External Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/").

---

