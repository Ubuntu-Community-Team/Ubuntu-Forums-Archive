---
title: "Cannot mount a ext4 partition"
date: 2009-07-16
forum: General Help
---

### Post by myk02k on 2009-07-16
I'm trying to mount a second partition formatted to ext4.  I currently run Jaunty on a ext3 formatted disc.  This is as far as I can get...

sudo mount -t ext4 /dev/sdb1 /mnt/test
mount: unknown filesystem type 'ext4'

Any advice?

---

### Post by itsjareds on 2009-07-16
Try using this:

```
sudo mount -t ext4dev /dev/sdb1 /mnt/test
```

Since ext4 is still in development, it has the dev suffix. This might have changed because I got the information from a thread from Dec 2008.

Read more: [http://ubuntuforums.org/showthread.php?p=6311252]("http://ubuntuforums.org/showthread.php?p=6311252")

---

### Post by myk02k on 2009-07-16
sudo mount -t ext4dev /dev/sdb1 /mnt/test

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I'm reading elsewhere that I need to update the Linux kernel, which I have 2.6.27-11-generic.  It sucks to be a newb; now I'm trying to figure out how to update.

---

### Post by myk02k on 2009-07-16
Updating linux-image-generic-2.6.27-11 to linux-image-generic-2.6.28-14 by checking the ubuntu-proposed option in Synaptic Package Manager.  Lets see how this goes...

---

### Post by itsjareds on 2009-07-16
I'm not sure, I think I was able to install Jaunty as an ext4 filesystem under your kernel. Either way, it doesn't hurt to update your kernel.

Here's some info I found from [another thread]("http://ubuntuforums.org/showthread.php?t=1152565"):
[QUOTE=lensman3]See if you can find a file called "ext4.ko", it lives in a directory under /lib.  Use the following command

find /lib -name "ext4.ko"

Then as root do "modprobe ext4". 

That should mount the ext4 driver.  Then you should be  able to do a normal mount of the partition.  Modprobe needs a sudo in front of it.  If you do a "/sbin/lsmod | grep ext4", the command will tell you if the module is already loaded.  Also look through "dmesg | more" to see if there is an error message about ext4.  Also after the modprobe above look at dmesg to see if module loaded correctly.

If the module ext4 doesn't exist on your machine, then you will have to compile a new kernel after you enable that module.[/QUOTE]

---

### Post by myk02k on 2009-07-16
Failures have occurred during the kernel update.

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.28-14-generic          
 *  nvidia (180.44)...                                                          nvidia (180.44): Installing module.
  Kernel headers for 2.6.28-14-generic are not installed.  Cannot install this module.
  Try installing linux-headers-2.6.28-14-generic or equivalent.
                                                                         [fail]
 *  vboxdrv (2.1.4)...                                                          vboxdrv (2.1.4): Installing module.
  Kernel headers for 2.6.28-14-generic are not installed.  Cannot install this module.
  Try installing linux-headers-2.6.28-14-generic or equivalent.
                                                                         [fail]
 *  vboxnetflt (2.1.4)...                                                       vboxnetflt (2.1.4): Installing module.
  Kernel headers for 2.6.28-14-generic are not installed.  Cannot install this module.
  Try installing linux-headers-2.6.28-14-generic or equivalent.
                                                                         [fail]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-image-generic (2.6.28.14.18) ...





:-\ 
Someone please tell me wtf just happened...

---

### Post by myk02k on 2009-07-16
Well now my laptop lost the use of compiz as the nvidia drivers have failed post-update and I'm sure VirtualBox has something wrong with it...

Oh yea, it still refuses to mount the ext4 partition.  I tried to fix one problem and created a whole mess...

---

### Post by jerome1232 on 2009-07-16
If you leave out the -t it will automatically determine the filesystem type, so try leaving out -t altogether.

---

### Post by myk02k on 2009-07-16
Seems like it's mounting now, thx.  Now I need to figure out how to get it to mount at startup...and fix whatever went wrong with the NVIDIA drivers...and fix whatever went wrong with VBOX...

---

### Post by myk02k on 2009-07-16
currently trying this to resolve the situation...

sudo apt-get install linux-headers-2.6.28-14-generic.

I'm hoping it's just an unmet dependency.

---

### Post by itsjareds on 2009-07-16
As far as getting the partition to mount on startup, you first need to get the UUID of the partition:

```
sudo blkid /dev/sdb1
```

This should return a string, then do sudo gedit /etc/fstab and enter this line at the end:

```
UUID=XXXXX-XXXXX-XXX /media/test ext4  defaults 0 2
```

---

### Post by myk02k on 2009-07-16
Thanks, everything is good to go now.

Jaunty could not mount the ext4 partition because it required me to update the linux kernel to 2.6.28.  I did this by enabling ubuntu-proposed updates through Synaptic Package Manager.

I ran into an error with NVIDIA and Virtual Box because linux-headers needed to be updated and was an unmet dependency after updating the kernel.

---

### Post by itsjareds on 2009-07-16
Alright, sounds good. Glad things are working.

Just for reference, did you mount with ext4 or ext4dev?

---

### Post by myk02k on 2009-07-16
ext4 works perfectly fine, although I can't seem to get /etc/fstab configured properly for my ext4 or NTFS partition.  Here's my fstab...

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=8d243bd0-d726-4327-b77c-4569bbb74588 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=d48393e1-579e-4647-a12e-cea5f7840b48 none swap sw 0 0
UUID=1884d5fa-69e0-4b13-9002-1bef37829e45 /media/Secondary\ Disk ext4  defaults 0 2
/dev/sda3 /media/Windows ntfs-3g defaults 0 0
/dev/scd0 /media/cdrom0 auto user,noauto,exec,utf8 0 0

---

### Post by itsjareds on 2009-07-16
Try this for your Windows partition:
```
/dev/sda3 /media/Windows ntfs-3g defaults,locale=en_US.utf8 0 0
```

Make sure that /media/Windows is already a folder, if not:
```
sudo mkdir /media/Windows
```

Then try this for your ext4 partition:
```
UUID=1884d5fa-69e0-4b13-9002-1bef37829e45 "/media/Secondary Disk" ext4 defaults 0 2
```

Make sure that you put quotes around Secondary Disk because it has a space in it. As with the Windows folder, make sure you have this folder as well:
```
sudo mkdir "/media/Secondary Disk"
```

---

### Post by JobeJahova on 2009-10-17
The ext4 encrypted filesystem uses encryption. Try installing the encryption support for "crypto_LUKS". These packages in synaptics should do it: **cryptsetup** , **cryptmount** , **gdecrypt**

I had the same problem trying to mount my ext4 Fedora home partition.

---

