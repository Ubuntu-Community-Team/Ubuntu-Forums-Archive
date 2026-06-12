---
title: "force install lucid kermel from livecd without internet"
date: 2011-08-29
forum: General Help
---

### Post by chaceos on 2011-08-29
Ok, I screwed up. 
I would discribe myself as a begginer in ubuntu.
I was running lucid as my only OS in my hp pavillion, and worked like a charm!
Two days before, I was reading some ubuntu documentation that was reassuuring me that ubuntu especsialy synaptic, wouldn't let me delete the current kernel image.
But after a restart I only could boot into memtest, and after some searching I found the obvious: I had no more a linux kernel.
I tried some things.. Nothing worked out, but at least I know what kind of help I need.

Is there a way to force install the livecd kernel to my root partition, and configure grub?
and all theese without an internet connection and with a locked- encrypted home partition?
and could the above workout to a functional system with the previus configuration?

thanks sooo much for your time.

---

### Post by blueridgedog on 2011-08-29
Follow the instructions in post 2, especially the chroot items mentioned in the signature.  

[http://ubuntuforums.org/showthread.php?t=1641599](http://ubuntuforums.org/showthread.php?t=1641599)

In essence, you will boot off of a LiveCD, then attach your current system as the "running" system, from there you will install a new kernel and update grub.

If you get stuck and want issue specific help, post the out put of the following while booted on the LiveCD:

sudo fdisk -al

and 

mount

---

### Post by chaceos on 2011-08-30
Ok thank you very much.
I've seen this thread before but I had the impression that "apt-get" linux image requires internet connection.
I think i've tried it also. Anyway, i' try it again and tell you for sure.
thanks again

---

### Post by chaceos on 2011-08-30
Ok thank you very much.
I've seen this thread before but I had the impression that "apt-get" linux image requires internet connection.
I think i've tried it also. Anyway, i' try it again and tell you for sure.
thanks again

---

### Post by blueridgedog on 2011-08-30
I neglected to mention that you will need to enable the CDROM as a source of packages, then you can use apt with it.  It should be enabled by default, which will require you to determine the kernel that is on the CD.

---

### Post by chaceos on 2011-08-30
I've done all theese mentioned in the links above and it didn't worked.
it was like needed internet connection to work out, but im not sure.
this is everything I did in terminal:
 
I have to add that I did it in a
persistent mode live usb.
but in the non persistent mode itis exactly the same without some lines in the end that states that cannot access /casper......blahblah
but still only find memtest to update grub.



ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00039cf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            9243        9730     3906561    5  Extended
/dev/sda2   *        7420        9243    14647296   83  Linux
/dev/sda3               1        7420    59594752   83  Linux
/dev/sda5            9243        9730     3906560   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4026 MB, 4026531840 bytes
220 heads, 32 sectors/track, 1117 cylinders
Units = cylinders of 7040 * 512 = 3604480 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006de31

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1118     3932143+   b  W95 FAT32
ubuntu@ubuntu:~$ sudo mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i; done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf 
cp: cannot stat `/etc/resolv.conf': No such file or directory
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# sudo apt-get update
sudo: unable to resolve host ubuntu
Err [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid Release.gpg
  Could not resolve 'gr.archive.ubuntu.com'
Err [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-updates Release.gpg
  Could not resolve 'gr.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
  Could not resolve 'ppa.launchpad.net'
Reading package lists... Done
W: Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'gr.archive.ubuntu.com'

W: Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Could not resolve 'gr.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:/# sudo apt-get install linux-image
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-image-2.6.32-32-generic linux-image-generic
Suggested packages:
  fdutils linux-doc-2.6.32 linux-source-2.6.32 linux-tools
The following NEW packages will be installed:
  linux-image linux-image-2.6.32-32-generic linux-image-generic
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 31.7MB of archives.
After this operation, 99.4MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-image-2.6.32-32-generic 2.6.32-32.62
  Could not resolve 'gr.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main linux-image-2.6.32-32-generic 2.6.32-32.62
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main linux-image-generic 2.6.32.32.38
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main linux-image 2.6.32.32.38
  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-32-generic_2.6.32-32.62_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-32-generic_2.6.32-32.62_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.32.32.38_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.32.32.38_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image_2.6.32.32.38_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image_2.6.32.32.38_i386.deb)  Could not resolve 'security.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu
Generating grub.cfg ...
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
done
root@ubuntu:/#

---

### Post by blueridgedog on 2011-08-31
I have some chroot instructions at home and will post them this evening.  After you are chroot'ed to your current install you should be able to open symantec and re-install the kernel.

---

### Post by chaceos on 2011-08-31
Thanks a lot.
By symantec you must mean synaptic right?
If it must use by default the live usb as source for the linux image,
why is it looking in internet adresses and fails to install the image?

---

### Post by dino99 on 2011-08-31
use dpkg to install the kernel deb packages:

use an empty folder where you put the required packages:
- linux-headers...all.deb
- linux-headers...i386.deb (or ...amd.deb for 64 bits)
- linux-image...i386.deb   ( " " " )

then cd /to/that/folder/

sudo dpkg -i *.deb

sudo update-grub

---

### Post by chaceos on 2011-08-31
Also there is another thing:
all theese eforts are because I believe that reinstalling the kernel, my pc will boot as before, and will ask me just the user password so I can have access to my system as before, and to my home directory as before.
Do you know how the newly installed kernel will behave to my encrypted home partition?
if there's a chance that cannot use my encrypted home partition  maybe it is better to wait some time to leave this place i m now and find the 11.04 live cd that has tool for encrypted partitions?

---

### Post by chaceos on 2011-09-02
> **dino99 said:**
> use dpkg to install the kernel deb packages:

use an empty folder where you put the required packages:
- linux-headers...all.deb
- linux-headers...i386.deb (or ...amd.deb for 64 bits)
- linux-image...i386.deb   ( " " " )

then cd /to/that/folder/

sudo dpkg -i *.deb

sudo update-grub

To dino99:
Could you please be more specific. Th folder youn mention must be on my original root, and do this after chrooting or I can do this without chroot and do it from any folder?
And please where am I going to find theese files? Could you write at least the full name and the full path if possible?

Thanks

---

### Post by chaceos on 2011-09-02
> **blueridgedog said:**
> I have some chroot instructions at home and will post them this evening.  After you are chroot'ed to your current install you should be able to open symantec and re-install the kernel.

blueridgedog any news?

---

### Post by blueridgedog on 2011-09-02
I would do the following:

```
blkid
```

< find the partition you installed ubuntu on

```
sudo mount /dev/sdax /mnt
``` 

< where x is partion # containing ubuntu and 'a' assumes this is your first hard drive (if have > 1)

```
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
```

Then copy over the kernel you want to install from the CDROM:

```
sudo mkdir /mnt/tmp/reinstall
```

< where you put this is not inportant

Find the following on your CDROM:
- linux-headers...all.deb
- linux-headers...i386.deb (or ...amd.deb for 64 bits)
- linux-image...i386.deb ( " " " )

cd /to/that/folder/ on the CDROM and copy them to the directory you made, such as

sudo cp /path/to/file/on/CDROM/(list the kernel files) /mnt/tmp/reinstall
<I can't give you an exact command here as I am mot certain what disk you will be using

Then change to the directory where you put the kernel files

```
cd /mnt/tmp/reinstall
``` 

and 

```
sudo dpkg -i *.deb
sudo update-grub
```

---

### Post by chaceos on 2011-09-03
OK. I couldn't find the .deb files in the usb...
but i found an internet connection.
so... I folowed the instructions of the link of your first post (blueridgedog):
[http://ubuntuforums.org/showthread.php?t=1641599](http://ubuntuforums.org/showthread.php?t=1641599)
and everything worked fine.
I chrooted into my original root, reinstalled the kernel, updated grub, and my system is back 
"same" and sound!
No problem with my encrypted home partition, just needed my superuser password.
I don't consider this thread as solved, because the "no internet connection" was crucial for the thread.
But thank you guys very very much anyway.

---

