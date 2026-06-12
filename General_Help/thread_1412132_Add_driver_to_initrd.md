---
title: "Add driver to initrd"
date: 2010-02-20
forum: General Help
---

### Post by kfleten on 2010-02-20
I have an initrd image (/var/lib/tftpboot/ltsp/i386/initrd.img-2.6.31-19-generic) to wich I want to add a driver. I have the right driver module in /opt/ltsp/i386/lib/modules/2.6.31-19-generic/kernel/drivers/net.

I have extracted the initrd image and copied the right module in to the initrd tree. I have then tried to make a new initrd image using two methods wich both fails:

1.
find . | cpio -o -c | gzip -9 > /var/lib/tftpboot/ltsp/i386/initrd.img-2.6.31-19-generic

This creates the initrd image, but the image causes kernel panic when loading it.

2. 
mkinitramfs -o initrd.img-2.6.31-19-generic 2.6.31-19-generic

This also creates an initrd image, but with no drivers at all. I get the error "find: '/lib/modules/2.6.31-19-generic/kernel/crypto/': No such file or directory" when running the command.

Is there anyone that can give me a clue on how to make the initrd image right ?

---

### Post by falconindy on 2010-02-20
Your first method panics because you're redirecting STDOUT from the pipeline to a file, and not doing anything with the gzipped data.

Your second method works because you haven't told mkinitramfs enough information to create a full image.

What you **should** be doing is the following:

* Put the kernel driver in the proper place (/lib/modules/`uname -r`/kernel/drivers/net/)
* Run `sudo depmod -a` and verify that the module has been added in "/lib/modules/`uname -r`/modules.dep".
* Create a new file in /usr/share/initramfs-tools/modules.d/ with the name of your driver and add the name of the module as well as any dependencies to that file. For example, if you were adding btrfs to your boot image, you'd make a file called btrfs and add:
```
btrfs
zlib-deflate
libcrc32c
crc32c
```
*If you ran depmod successfully, modules.dep will tell you what other modules your new driver is dependent on*

* Regenerate the image with: `update-initramfs -u -k all`

You may need a boot hook as well depending on what exactly the new driver is for.

---

### Post by kfleten on 2010-02-21
Thanks ! That helped me a lot. With the proper drivers in /lib/modules/`uname -r`/kernel/drivers/net/ and following your advices I got the driver in to the initrd. In fact the easy way was to install kernel sources (wich I had not in the first place), wich in turn populated /lib/modules/

I have made a file in /usr/share/initramfs-tools/modules.d/ called "b43". From modules.dep I added to the file:
b43
ssb
mac80211
cfg80211
led-class

Unfortunately there commes no firmware into the new initrd ?
I did *sudo apt-get install b43-fwcutter* and regenerated the image with: *update-initramfs -u -k 2.6.31-19-generic*

How can I get the firmware into the initrd ?

---

### Post by falconindy on 2010-02-21
I'm not familiar with loading firmware on a boot image. What are you doing that you need the firmware this early in userspace and can't wait for udev?

---

### Post by kfleten on 2010-02-22
I'm building a LTSP boot image for wireless :-)

I have tried to follow [http://www.lug-kr.de/wiki/ThinClientLokalBooten](http://www.lug-kr.de/wiki/ThinClientLokalBooten) and other helpfull links on the Internet. 

With your help -and what I have read other places - I yesterday managed to bulid the image. This was done by:
*sudo chroot /opt/ltsp/i386/*
*mount /proc -t proc /proc* 
*apt-get install b43-fwcutter*
and finally adding "b43" to the end of /etc/initramfs-tools/modules (In LTSP chroot). Then I built the initrd with
*update-initramfs -u -k 2.6.31-19-generic *

This gave me the message that firmware was not present in 
/lib/firmware/2.6.31-19-generic/FW13/ 
so I copied the files extracted from the *apt-get install b43-fwcutter* command, and pasted it into /lib/firmware/2.6.31-19-generic/FW13/ 
Then I built the initrd again - now with success (I think) - since there was no errors this time. But I'm not shure: when I unpack the initrd to have a look, the FW13 folder is empty ?

If the initrd image is Ok, then my last step will be tweaking scripts to connect to the wireless network. [http://www.lug-kr.de/wiki/ThinClientLokalBooten](http://www.lug-kr.de/wiki/ThinClientLokalBooten) mentions (like you did) that I might need a "boot hook" ? What does a "boot hook" do ?

---

### Post by falconindy on 2010-02-22
Glad to hear you've had some success on your own. I'm not really sure where to go with the lack of error message.

These are boot hooks:
[img]http://www.shoeandfootcare.com/pics/TN_104-083-00_boot_hook_2.jpg[/img]

Okay, okay. I'm fibbing slightly. A boot hook is simply a script contained in the initrd that runs in order to assist in creation (mounting) of the root filesystem. It usually accompanies some extra software that wouldn't normally be found on a boot image. For example, I used to have a boot hook that ran "btrfsctl -a" in order to scan discovered devices for btrfs filesystems. It was a necessary evil before I was able to mount the FS as root.

In your case... well, I'm not incredibly familiar with the concept of a network mounted root (I only know the general idea behind it). Being wireless, you're going to have some extra hurdles to overcome. Sounds like fun!

---

### Post by TheeMahn2003 on 2010-12-21
I too have been messing with rebuilding the livefs kernel for Ultimate Edition 2.6.1 & have had success.  I went from 10.04.1's 2.6.32-17-generic to 2.6.32-27-generic, also saving 100's of MB of space. I hope I can shed some light.  **Note**: there are some fairly heavy commands used below, please use caution:
```
#Do not screw around root up
#sudo passwd
su

#grab required tools
apt-get install squashfs-tools lzma lzma-source

#initiate build
modprobe squashfs
#remove old if nec.
rm -R edit
rm -R extract-cd
rm -R mnt
rm -R squashfs

#prepare
mkdir edit
mkdir extract-cd
mkdir mnt
mkdir squashfs

#mount & extract
mount -o loop ultimate-edition-2.6-x64.iso mnt
rsync --exclude=/casper/filesystem.squashfs -a mnt/ extract-cd
mount -t squashfs -o loop mnt/casper/filesystem.squashfs squashfs
cp -a squashfs/* edit/

#setup networking for chroot environment
cp /etc/resolv.conf edit/etc
cp /etc/hosts edit/etc

#sources list? (optional)
cp edit/etc/apt/sources.list edit/etc/apt/sources.bak
cp /etc/apt/sources.list edit/etc/apt

#optional extra sources...
cp /etc/apt/sources.list.d/* edit/etc/apt/sources.list.d/

#Mount proc etc. as su
#sudo passwd
#su
umount /home/theemahn/wip/squashfs/
umount /home/theemahn/wip/mnt/
mount --bind /dev/ edit/dev
#mount --bind / edit <<- unnecessary
chroot edit
mount -t devpts none /dev/pts
mount -t proc none /proc
mount -t sysfs none /sys
cd tmp/
apt-get update

#
# The Section of your concern, I typically use it for plymouth splashes #
# In this case a new Kernel, custom plymouth splash also comes along ;) #
#

###########################################################################
#Special commands needed to build new kernel to obtain Plymouth from chroot#
###########################################################################

#Assume super user role - not necessary as done earlier
#su
#unnecessary as done above
#chroot edit
#mount -t devpts none /dev/pts
#mount -t proc none /proc
#mount -t sysfs none /sys
#plymouth-set-default-theme -R Ultimate_Edition_2.6 <<-history, done differently see below

#The above plymouth commands are now depreciated, below setting 250 will make it take over any other known o/s
#customizations
#update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/Ultimate_Edition_2.6/Ultimate_Edition_2.6.plymouth 250
#update-alternatives --config default.plymouth  #use this command if you wish to change
#change plymouth to another theme always execute the following after the fact.
#update-initramfs -u

#CAUTION:
#Purge all old kernels - This is pretty heavy (please pay close attention to output on the console)
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs -p sudo apt-get -y purge

#Grab headers and source for remaining single kernel
apt-get install build-essential linux-headers-`uname -r` linux-image-`uname -r`

#update initramfs
update-initramfs -u -k all

depmod -a 

#this can be used if you wish to install additional drivers as falconindy has said above firmware I believe in your case to be located in cd /lib/modules/`uname -r`/kernel/drivers/firmware/ 

# Adding Additional drivers Example (as provided by falconindy now hard coded in my wip file):
# =================================
# * Put the kernel driver in the proper place (/lib/modules/`uname -r`/kernel/drivers/net/)
# * Run `sudo depmod -a` and verify that the module has been added in "/lib/modules/`uname -r`/modules.dep".
# * Create a new file in /usr/share/initramfs-tools/modules.d/ with the name of your driver and add the name of the module as well as any dependencies to that file. For example, if you were adding btrfs to your boot image, you'd make a # file called btrfs and add:
# Code:
#
#  btrfs
#  zlib-deflate
#  libcrc32c
#  crc32c

#If you ran depmod successfully, modules.dep will tell you what other modules your new driver is dependent on

# * Regenerate the image with: `update-initramfs -u -k all`

# You may need a boot hook as well depending on what exactly the new driver is for.

#Build Initrd.lz
mkinitramfs -o /tmp/initrd.lz `uname -r`

#copy vmlinuz
cp /boot/vmlinuz-`uname -r` /tmp/vmlinuz

#Scrap source and headers (optional)?
#apt-get --remove --purge linux-headers-`uname -r` linux-image-`uname -r`

#unmount
umount -f /proc/sys/fs/binfmt_misc
umount /proc
umount /sys
umount /dev/pts
exit
umount /home/theemahn/wip/edit/dev

#Transfer to disk to build
mv edit/tmp/initrd.lz extract-cd/casper/
mv edit/tmp/vmlinuz extract-cd/casper/

## PROCEED TO BUILD SECTION ##

```

It's not often I post over here.  I hope you appreciate it, and thanks for the tidbit of info falconindy.

TheeMahn,

---

### Post by sabinsathian on 2011-12-22
I found similar problem while creating initramfs with 3.1.5 kernel:
root@SabinS:/boot# mkinitramfs -o initramfs-3.1.5 3.1.5
find: `/lib/modules/3.1.5/kernel/crypto/': No such file or directory

Found it easier to solve this by just making a couple of unharmful options under Cryptographic API as 'M' module build.
This created a folder for crypto under modules and a few modules depending on the options selected.

---

