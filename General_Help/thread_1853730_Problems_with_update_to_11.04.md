---
title: "Problems with update to 11.04"
date: 2011-10-02
forum: General Help
---

### Post by josephellengar on 2011-10-02
So, I typically stay exactly 6 months behind the release schedule, so I am currently updating to 11.04 from 10.10. I am having a few problems.

1) If I use the default kernel, I get a completely blank screen on boot.

2) If I use either one of the old kernels that I have installed (2.6.32-25 or 2.6.32-22) I get one of those screens that appears when you have a bad graphics driver. It's all green with horizontal lines and at the very top of the screen there are red horizontal lines. I am able to use my boot to Windows option.

Any idea what might be causing this? On my current 10.10 system I have a working Nvidia proprietary driver, if that's the problem. I have never been able to use kernel 2.6.32-25 even in 10.10. It never boots entirely so I always use 2.6.35-22-generic.

My system specs are: hp dv7t quad. Intel Core i7-820QM Processor (1.73GHz, 8MB L2 Cache, 1333MHz FSB)
8gb RAM DDR3
1GB Nvidia GeForce GT 230M
160Gb Gen 1 Intel SSD.
Etc. Do you have any idea what the problem might be? Should I bother trying to install from scratch? Is it a driver issue?

---

### Post by wildmanne39 on 2011-10-02
Hi, yes it is most likely an issue with your nvidia driver. use this link to set nomodeset parameters to see if you can boot so you can install your nvidia driver.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thank you

---

### Post by josephellengar on 2011-10-02
> **wildmanne39 said:**
> Hi, yes it is most likely an issue with your nvidia driver. use this link to set nomodeset parameters to see if you can boot so you can install your nvidia driver.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thank you

Thanks. I'll try it and report back tomorrow. Right now I'm going to get my beauty sleep.

---

### Post by josephellengar on 2011-10-03
Okay, I've spent the last few hours arguing with my computer. Here's what I've found out:

If it is the driver, adding the nomodeset parameter to my grub boot does not help. Rather, I reach a blank screen every time and have to do a hard reboot. I only got the weird screen with the colored horizontal lines once today in about twenty boots.

I am able to boot into Recovery Mode with only a CLI, and I am also able to boot into Windows, which I am using now.

My package manager is working, as from recovery mode I was able to add and remove packages with a wired network connection.

I know it's not very much to go on. I also ran the Boot Info Script (results below) and am attaching my grub.d directory, if that is any help to you at all.

Do you have any other ideas what my problem could be?

EDIT: By the way, I was adding "nomodeset" to the end of the line that looks like this in grub: 
```
linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 ro   quiet splash vt.handoff=7
```

Results from boot info script:

```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   157,870,079   157,460,480   7 NTFS / exFAT / HPFS
/dev/sda3         157,870,755   312,576,704   154,705,950   5 Extended
/dev/sda5         157,870,818   262,731,775   104,860,958  83 Linux
/dev/sda6         262,743,138   312,576,704    49,833,567  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   597,457,349   597,457,287   7 NTFS / exFAT / HPFS
/dev/sdb2         597,457,350   625,137,344    27,679,995  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        40389FB8389FAB82                       ntfs       SYSTEM
/dev/sda2        645684D25684A700                       ntfs       OS
/dev/sda5        098c0e33-2ea8-420a-a7c9-2bcdc9011118   ext4       
/dev/sda6        c835dec7-b978-4793-b23d-2f812c6a1f96   ext4       home
/dev/sdb1        74912E3D2459A0BE                       ntfs       
/dev/sdb2        0de4ba0c-7406-4974-a25b-a1d10f68be39   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,discard,commit=600)
/dev/sda6        /home                    ext4       (rw,errors=remount-ro,discard,commit=600)
/dev/sdb1        /home/ross/storage       fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 098c0e33-2ea8-420a-a7c9-2bcdc9011118
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=4
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 098c0e33-2ea8-420a-a7c9-2bcdc9011118
insmod png
if background_image /boot/grub/grub-splash-wide.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=blue/green
  set menu_color_highlight=green/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 098c0e33-2ea8-420a-a7c9-2bcdc9011118
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 098c0e33-2ea8-420a-a7c9-2bcdc9011118
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 098c0e33-2ea8-420a-a7c9-2bcdc9011118
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 098c0e33-2ea8-420a-a7c9-2bcdc9011118
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 098c0e33-2ea8-420a-a7c9-2bcdc9011118
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 098c0e33-2ea8-420a-a7c9-2bcdc9011118
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 40389FB8389FAB82
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 645684D25684A700
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0

# root filesystem
UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 / ext4 errors=remount-ro,discard 0 1

# swap file
UUID=0de4ba0c-7406-4974-a25b-a1d10f68be39 none swap sw 0 0

# home
/dev/sda6 /home ext4 errors=remount-ro,discard 0 1

# storage
/dev/sdb1 /home/ross/storage ntfs-3g auto,exec,user,uid=1000,gid=100,dmask=027,fmask=137,utf8 0 0

# flash drive
/dev/sdc1 /home/ross/flash vfat iocharset=utf8,umask=000,user,noauto,exec 0 0

#tmpfs
tmpfs /tmp tmpfs defaults,noatime 0 0
tmpfs /var/tmp tmpfs defaults,noatime 0 0
tmpfs /usr/src tmpfs defaults,noatime 0 0
tmpfs /var/cache/apt/archives tmpfs defaults,noatime 0 0
tmpfs /var/log tmpfs defaults,noatime 0 0


--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  75.414711952 = 80.975930368   boot/grub/core.img                             1
  79.640564919 = 85.513405440   boot/grub/grub.cfg                             1
  84.442734718 = 90.669696000   boot/initrd.img-2.6.32-25-generic              2
  91.339261055 = 98.074784768   boot/initrd.img-2.6.35-22-generic              2
  91.381318092 = 98.119943168   boot/initrd.img-2.6.38-11-generic              2
  87.532505989 = 93.987312640   boot/vmlinuz-2.6.32-25-generic                 1
  87.344235420 = 93.785158656   boot/vmlinuz-2.6.35-22-generic                 1
  88.931328773 = 95.489287168   boot/vmlinuz-2.6.38-11-generic                 1
  91.381318092 = 98.119943168   initrd.img                                     2
  91.339261055 = 98.074784768   initrd.img.old                                 2
  88.931328773 = 95.489287168   vmlinuz                                        1
  87.344235420 = 93.785158656   vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by wildmanne39 on 2011-10-03
Hi, I looked over your boot information, it looks okay but I am not that good at reading the boot script information.

If you remove quiet splash then add your parameter you will get to see more output of what is going on and what fails.

Do you have two video cards in your computer?
Thank you

---

### Post by pr3zident on 2011-10-04
I have the same problem than i have to install my ubuntu version 10.04 back ... did you ever fix this problem ?

---

### Post by Mr.Enigma on 2011-10-04
wait a while for it to boot up fully (if it is booting up) and hit ctrl+alt+F1 to bring up the command line interface.

If that interface pops up it's a problem with the drivers and you may have to investigate the commands to fix it.

If it doesn't it's a problem with the kernal and your download may have been damaged, try re-downloading the .iso

---

### Post by pr3zident on 2011-10-04
> **Mr.Enigma said:**
> wait a while for it to boot up fully (if it is booting up) and hit ctrl+alt+F1 to bring up the command line interface.

If that interface pops up it's a problem with the drivers and you may have to investigate the commands to fix it.

If it doesn't it's a problem with the kernal and your download may have been damaged, try re-downloading the .iso

I tried i have waited to see if it was my lack of patience, i pressed ctrl alt f1 doesn't work its just a black screen, the sound plays as if it is on but the screen shows nothing, ive tried downloading the iso 100 times usb and live cd nothing seems to work ive to to update my kernel use the old and new kernel i have still not working

---

### Post by wildmanne39 on 2011-10-04
Hi pr3zident, please follow the directions in post 2.
Thank you

---

### Post by pr3zident on 2011-10-04
Ok I'm going to try it now.. thanx

---

### Post by josephellengar on 2011-10-04
> **wildmanne39 said:**
> Hi, I looked over your boot information, it looks okay but I am not that good at reading the boot script information.

If you remove quiet splash then add your parameter you will get to see more output of what is going on and what fails.

Do you have two video cards in your computer?
Thank you

I have one video card.

I removed quiet splash and with the more recent kernels it completely freezes- on the grub splash screen. I didn't even know that was possible. So I can't tell what's going on in the background.

When I go to the old kernels through "previous linux versions" it freezes at an arbitrary spot in the boot and I really don't get any useful messages. Last time I think it froze at 
loading scripts /init/<whatever> done

So it even said done, but it just didn't continue. And it's not a kernel panic, since the caps lock key is not flashing.

Anyway, thanks for the continued help.

---

### Post by philinux on 2011-10-04
In recovery mode do this and post back.

```
apt-cache policy nvidia-current
```

You could try removing it and see if it will then boot up. You can always reinstall it.

```
sudo apt-get remove nvidia-current
```

---

### Post by josephellengar on 2011-10-04
> **philinux said:**
> In recovery mode do this and post back.

```
apt-cache policy nvidia-current
```

You could try removing it and see if it will then boot up. You can always reinstall it.

```
sudo apt-get remove nvidia-current
```

Did both of these. Thanks. The output from the first one is:

```

nvidia-current:
  Installed: 270.41.06-0ubuntu1
  Candidate: 270.41.06-0ubuntu1
  Version table:
 *** 270.41.06-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ natty/restricted amd64 Packages
        100 /var/lib/dpkg/status

```

Then I uninstalled the driver and tried to boot back up. It still froze on all of the boots, but when I booted with the most recent kernel, when it froze I was able to alt-shift-f1 into a command prompt. I was not able to do that with any of the other kernels.

Most of the kernels boot silently, but on one of them when it froze it gave this error message: 
```

nouveau: couldn't find matching output script table

```

Any more ideas? I've run out of ideas myself.

EDIT: Should I reinstall? I have a separate /home partition, so that *should* save most of my information and customization, correct?

---

### Post by wildmanne39 on 2011-10-04
Hi, in the link with nomodset there is other parameters to try, did you try them all one at a time?
Thank you

---

### Post by josephellengar on 2011-10-04
> **wildmanne39 said:**
> Hi, in the link with nomodset there is other parameters to try, did you try them all one at a time?
Thank you

Now I have. No luck.

---

### Post by wildmanne39 on 2011-10-04
Hi, did you upgrade to 11.04 was this a clean install?

Did you have any trouble when you installed 11.04? 

Did 11.04 ever boot?

Did you try it out on your computer before you installed it?
Thank you

---

### Post by pjd99 on 2011-10-04
I had some issues a few months ago with locking during boot. Ended up blacklisting the nouveau driver, then purging and reinstalling the nvidia driver to get the system working again.

Original post if it's any help: [http://ubuntuforums.org/showthread.php?t=1830622](http://ubuntuforums.org/showthread.php?t=1830622)

---

### Post by josephellengar on 2011-10-04
> **pjd99 said:**
> I had some issues a few months ago with locking during boot. Ended up blacklisting the nouveau driver, then purging and reinstalling the nvidia driver to get the system working again.

Original post if it's any help: [http://ubuntuforums.org/showthread.php?t=1830622](http://ubuntuforums.org/showthread.php?t=1830622)

How would I go about blacklisting nouveau? I can access a command line but cannot access a GUI. Thanks for the link. Sounds a lot like my problem.

---

### Post by josephellengar on 2011-10-04
> **wildmanne39 said:**
> Hi, did you upgrade to 11.04 was this a clean install?

Did you have any trouble when you installed 11.04? 

Did 11.04 ever boot?

Did you try it out on your computer before you installed it?
Thank you

Upgrade. Only boots to CLI. Did use with livecd many times and it always worked.

---

### Post by pjd99 on 2011-10-04
> **josephellengar said:**
> How would I go about blacklisting nouveau? I can access a command line but cannot access a GUI. Thanks for the link. Sounds a lot like my problem.

```

sudo cp /etc/modprobe.d/blacklist.conf /etc/modprobe.d/blacklist.conf.bak
sudo echo -e "\n#In case of nvidia conflict\nblacklist nouveau" >> /etc/modprobe.d/blacklist.conf

```Should put it straight in there for you with a comment, it you ever wonder why its there.

EDIT: Should probably back up original blacklist.conf first.

---

### Post by josephellengar on 2011-10-04
> **pjd99 said:**
> ```

sudo cp /etc/modprobe.d/blacklist.conf /etc/modprobe.d/blacklist.conf.bak
sudo echo -e "\n#In case of nvidia conflict\nblacklist nouveau" >> /etc/modprobe.d/blacklist.conf

```Should put it straight in there for you with a comment, it you ever wonder why its there.

EDIT: Should probably back up original blacklist.conf first.

Didn't work. Latest kernel still freezes on Grub splash screen; other two kernels give me the horizontal colored lines. I'm really mystified. I've had problems before on upgrades, but never this bad.

EDIT: But thank you very much for your continued help.

---

### Post by pjd99 on 2011-10-04
TBH, I never marked the linked thread as solved, as I couldn't figure out what actually caused it to start working again.

Basically, when I lost mine, I did:
```

sudo apt-get purge nvidia-common nvidia-current
sudo apt-get install linux-image-2.6.38-11-generic linux-headers-2.6.38-11-generic
export CC=/usr/bin/gcc-4.5
sudo apt-get install nvidia-common nvidia-current

```(the CC thing was because I'd linked gcc-4.4 to /usr/bin/gcc)

Other times, to reconfigure xorg (to change to nvidia, nv or nouveau):
```

sudo dpkg-reconfigure xserver-xorg
or
sudo dpkg-reconfigure xserver-xorg -phigh

```Can't remember what the -phigh does anymore. I don't even know if this does much anymore, nvidia-settings seems to take over in X.

---

### Post by wildmanne39 on 2011-10-04
Hi, there has been a lot of trouble when upgrading to 11.04, it has been best to do a clean install.

I am wondering if everything got installed?

You might try this:
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)
Thank you

---

### Post by josephellengar on 2011-10-04
Thanks to both of you. I'll try this and report back tomorrow.

EDIT: And @pjd999: I left the blacklist nouveau in. Should I remove that before trying the code that you give above?

@wildmanne39: I've been thinking that I might have to do a clean install, but I'd like to debug more first, as it would take a lot to completely replace my settings, etc, in my current installation.

---

### Post by josephellengar on 2011-10-04
I don't know if this will help or not, but I thought that I'd mention I tried a `startx` and got a log with a whole lot of output. It's probably stuff that we already know, but I thought I'd post it in case anybody could figure out what it means. The only thing that jumps out at me is, again, the problems with the nvidia drivers.

```


[   126.247] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[   126.254] X Protocol Version 11, Revision 0
[   126.258] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[   126.264] Current Operating System: Linux ross-laptop 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64
[   126.277] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 ro quiet splash vt.handoff=7
[   126.296] Build Date: 11 August 2011  03:43:05PM
[   126.307] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[   126.332] Current version of pixman: 0.20.2
[   126.346] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   126.378] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   126.432] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct  4 22:39:08 2011
[   126.455] (==) Using config file: "/etc/X11/xorg.conf"
[   126.476] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   126.497] (==) No Layout section.  Using the first Screen section.
[   126.498] (**) |-->Screen "Default Screen" (0)
[   126.498] (**) |   |-->Monitor "<default monitor>"
[   126.498] (==) No device specified for screen "Default Screen".
	Using the first device section listed.
[   126.498] (**) |   |-->Device "Default Device"
[   126.498] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[   126.498] (==) Automatically adding devices
[   126.498] (==) Automatically enabling devices
[   126.498] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   126.498] 	Entry deleted from font path.
[   126.498] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   126.498] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   126.498] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   126.498] (II) Loader magic: 0x7e17e0
[   126.498] (II) Module ABI versions:
[   126.498] 	X.Org ANSI C Emulation: 0.4
[   126.498] 	X.Org Video Driver: 10.0
[   126.498] 	X.Org XInput driver : 12.3
[   126.498] 	X.Org Server Extension : 5.0
[   126.499] (--) PCI:*(0:1:0:0) 10de:0a28:103c:363c rev 162, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00007000/128, BIOS @ 0x????????/524288
[   126.499] (II) Open ACPI successful (/var/run/acpid.socket)
[   126.499] (II) "extmod" will be loaded by default.
[   126.499] (II) "dbe" will be loaded by default.
[   126.499] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[   126.499] (II) "record" will be loaded by default.
[   126.499] (II) "dri" will be loaded by default.
[   126.499] (II) "dri2" will be loaded by default.
[   126.499] (II) LoadModule: "glx"
[   126.499] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   126.499] (II) Module glx: vendor="X.Org Foundation"
[   126.499] 	compiled for 1.10.1, module version = 1.0.0
[   126.499] 	ABI class: X.Org Server Extension, version 5.0
[   126.499] (==) AIGLX enabled
[   126.499] (II) Loading extension GLX
[   126.499] (II) LoadModule: "extmod"
[   126.499] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   126.499] (II) Module extmod: vendor="X.Org Foundation"
[   126.499] 	compiled for 1.10.1, module version = 1.0.0
[   126.499] 	Module class: X.Org Server Extension
[   126.499] 	ABI class: X.Org Server Extension, version 5.0
[   126.499] (II) Loading extension MIT-SCREEN-SAVER
[   126.499] (II) Loading extension XFree86-VidModeExtension
[   126.499] (II) Loading extension XFree86-DGA
[   126.499] (II) Loading extension DPMS
[   126.499] (II) Loading extension XVideo
[   126.499] (II) Loading extension XVideo-MotionCompensation
[   126.499] (II) Loading extension X-Resource
[   126.499] (II) LoadModule: "dbe"
[   126.499] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   126.500] (II) Module dbe: vendor="X.Org Foundation"
[   126.500] 	compiled for 1.10.1, module version = 1.0.0
[   126.500] 	Module class: X.Org Server Extension
[   126.500] 	ABI class: X.Org Server Extension, version 5.0
[   126.500] (II) Loading extension DOUBLE-BUFFER
[   126.500] (II) LoadModule: "record"
[   126.500] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   126.500] (II) Module record: vendor="X.Org Foundation"
[   126.500] 	compiled for 1.10.1, module version = 1.13.0
[   126.500] 	Module class: X.Org Server Extension
[   126.500] 	ABI class: X.Org Server Extension, version 5.0
[   126.500] (II) Loading extension RECORD
[   126.500] (II) LoadModule: "dri"
[   126.500] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   126.500] (II) Module dri: vendor="X.Org Foundation"
[   126.500] 	compiled for 1.10.1, module version = 1.0.0
[   126.500] 	ABI class: X.Org Server Extension, version 5.0
[   126.500] (II) Loading extension XFree86-DRI
[   126.500] (II) LoadModule: "dri2"
[   126.500] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   126.500] (II) Module dri2: vendor="X.Org Foundation"
[   126.500] 	compiled for 1.10.1, module version = 1.2.0
[   126.500] 	ABI class: X.Org Server Extension, version 5.0
[   126.500] (II) Loading extension DRI2
[   126.500] (II) LoadModule: "nvidia"
[   126.501] (WW) Warning, couldn't open module nvidia
[   126.501] (II) UnloadModule: "nvidia"
[   126.501] (II) Unloading nvidia
[   126.501] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   126.523] (EE) No drivers available.
[   126.546] 
Fatal server error:
[   126.592] no screens found
[   126.616] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[   126.715] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   126.768] 

```

---

### Post by pjd99 on 2011-10-04
You can leave it blacklisted unless you want to try that driver. From memory, my problem was that nouveau was being loaded and then nvidia was trying to load, causing a conflict. There's a possibility that it was due to my gcc version, but I never proved it.


I could still boot using the nv driver, with very bad performance (2D desktop taking 2 seconds to minimise a window). Can you get to X at all using a recovery session?

---

### Post by pjd99 on 2011-10-04
Looks like the nvidia module isn't present.

Do you get an error if you try to insert the module yourself:
```

sudo modprobe -i nvidia

```
then try startx.

Can you post the output of /var/log/Xorg.0.log as well. It looks like the driver isn't there...

---

### Post by josephellengar on 2011-10-04
> **pjd99 said:**
> Looks like the nvidia module isn't present.

Do you get an error if you try to insert the module yourself:
```

sudo modprobe -i nvidia

```
then try startx.

Can you post the output of /var/log/Xorg.0.log as well. It looks like the driver isn't there...

I think I removed the driver earlier on yours or somebody else's recommendation. Given this information, how should I adapt the steps that you gave me above? Should I reinstall the driver before I start that? Would you mind giving me a list of things that I should try, in order? That would be extremely helpful.

Thank you very much either way.

This is going to be my last post tonight. I'm gonna go to bed.

---

### Post by pjd99 on 2011-10-05
> **josephellengar said:**
> I think I removed the driver earlier on yours or somebody else's recommendation. Given this information, how should I adapt the steps that you gave me above? Should I reinstall the driver before I start that? Would you mind giving me a list of things that I should try, in order? That would be extremely helpful.

Thank you very much either way.

This is going to be my last post tonight. I'm gonna go to bed.
I'd say try:
```

sudo apt-get purge nvidia-common nvidia-current
sudo apt-get install linux-image-2.6.38-11-generic linux-headers-2.6.38-11-generic
sudo apt-get install nvidia-common nvidia-current

```If no errors are thrown during the installation, try either:
sudo service gdm restart
startx
sudo reboot

---

### Post by josephellengar on 2011-10-05
Okay, I went through this thread today and did literally everything that has been recommended, to no avail. My latest output, after purging and reinstalling the kernel and drivers are below. Also, modprobe -i gives me a "driver not found" error.

I am *positive* that the driver is installed.

```

[    48.645] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    48.705] X Protocol Version 11, Revision 0
[    48.724] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    48.744] Current Operating System: Linux ross-laptop 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64
[    48.786] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 ro single
[    48.828] Build Date: 11 August 2011  03:43:05PM
[    48.850] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[    48.895] Current version of pixman: 0.20.2
[    48.917] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    48.962] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    49.034] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct  5 16:32:01 2011
[    49.059] (==) Using config file: "/etc/X11/xorg.conf"
[    49.084] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    49.110] (==) No Layout section.  Using the first Screen section.
[    49.110] (**) |-->Screen "Default Screen" (0)
[    49.110] (**) |   |-->Monitor "<default monitor>"
[    49.110] (==) No device specified for screen "Default Screen".
	Using the first device section listed.
[    49.110] (**) |   |-->Device "Default Device"
[    49.110] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[    49.110] (==) Automatically adding devices
[    49.110] (==) Automatically enabling devices
[    49.114] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    49.114] 	Entry deleted from font path.
[    49.118] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    49.118] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    49.118] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    49.118] (II) Loader magic: 0x7e17e0
[    49.119] (II) Module ABI versions:
[    49.119] 	X.Org ANSI C Emulation: 0.4
[    49.119] 	X.Org Video Driver: 10.0
[    49.119] 	X.Org XInput driver : 12.3
[    49.119] 	X.Org Server Extension : 5.0
[    49.120] (--) PCI:*(0:1:0:0) 10de:0a28:103c:363c rev 162, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00007000/128, BIOS @ 0x????????/524288
[    49.120] (II) Open ACPI successful (/var/run/acpid.socket)
[    49.120] (II) "extmod" will be loaded by default.
[    49.120] (II) "dbe" will be loaded by default.
[    49.120] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    49.120] (II) "record" will be loaded by default.
[    49.120] (II) "dri" will be loaded by default.
[    49.120] (II) "dri2" will be loaded by default.
[    49.120] (II) LoadModule: "glx"
[    49.120] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    49.125] (II) Module glx: vendor="NVIDIA Corporation"
[    49.125] 	compiled for 4.0.2, module version = 1.0.0
[    49.125] 	Module class: X.Org Server Extension
[    49.125] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
[    49.125] (II) Loading extension GLX
[    49.125] (II) LoadModule: "extmod"
[    49.126] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    49.126] (II) Module extmod: vendor="X.Org Foundation"
[    49.126] 	compiled for 1.10.1, module version = 1.0.0
[    49.126] 	Module class: X.Org Server Extension
[    49.126] 	ABI class: X.Org Server Extension, version 5.0
[    49.126] (II) Loading extension MIT-SCREEN-SAVER
[    49.126] (II) Loading extension XFree86-VidModeExtension
[    49.126] (II) Loading extension XFree86-DGA
[    49.126] (II) Loading extension DPMS
[    49.126] (II) Loading extension XVideo
[    49.126] (II) Loading extension XVideo-MotionCompensation
[    49.126] (II) Loading extension X-Resource
[    49.126] (II) LoadModule: "dbe"
[    49.126] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    49.126] (II) Module dbe: vendor="X.Org Foundation"
[    49.126] 	compiled for 1.10.1, module version = 1.0.0
[    49.126] 	Module class: X.Org Server Extension
[    49.126] 	ABI class: X.Org Server Extension, version 5.0
[    49.126] (II) Loading extension DOUBLE-BUFFER
[    49.126] (II) LoadModule: "record"
[    49.126] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    49.126] (II) Module record: vendor="X.Org Foundation"
[    49.126] 	compiled for 1.10.1, module version = 1.13.0
[    49.126] 	Module class: X.Org Server Extension
[    49.126] 	ABI class: X.Org Server Extension, version 5.0
[    49.126] (II) Loading extension RECORD
[    49.126] (II) LoadModule: "dri"
[    49.127] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    49.127] (II) Module dri: vendor="X.Org Foundation"
[    49.127] 	compiled for 1.10.1, module version = 1.0.0
[    49.127] 	ABI class: X.Org Server Extension, version 5.0
[    49.127] (II) Loading extension XFree86-DRI
[    49.127] (II) LoadModule: "dri2"
[    49.127] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    49.127] (II) Module dri2: vendor="X.Org Foundation"
[    49.127] 	compiled for 1.10.1, module version = 1.2.0
[    49.127] 	ABI class: X.Org Server Extension, version 5.0
[    49.127] (II) Loading extension DRI2
[    49.127] (II) LoadModule: "nvidia"
[    49.127] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    49.127] (II) Module nvidia: vendor="NVIDIA Corporation"
[    49.127] 	compiled for 4.0.2, module version = 1.0.0
[    49.127] 	Module class: X.Org Video Driver
[    49.154] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    49.181] (EE) NVIDIA:     system's kernel log for additional error messages.
[    49.208] (II) UnloadModule: "nvidia"
[    49.208] (II) Unloading nvidia
[    49.208] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    49.235] (EE) No drivers available.
[    49.261] 
Fatal server error:
[    49.313] no screens found
[    49.339] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    49.446] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    49.501] 

```

---

### Post by pr3zident on 2011-10-05
> **josephellengar said:**
> Okay, I went through this thread today and did literally everything that has been recommended, to no avail. My latest output, after purging and reinstalling the kernel and drivers are below. Also, modprobe -i gives me a "driver not found" error.

I am *positive* that the driver is installed.

```

[    48.645] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    48.705] X Protocol Version 11, Revision 0
[    48.724] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    48.744] Current Operating System: Linux ross-laptop 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64
[    48.786] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 ro single
[    48.828] Build Date: 11 August 2011  03:43:05PM
[    48.850] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[    48.895] Current version of pixman: 0.20.2
[    48.917] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    48.962] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    49.034] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct  5 16:32:01 2011
[    49.059] (==) Using config file: "/etc/X11/xorg.conf"
[    49.084] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    49.110] (==) No Layout section.  Using the first Screen section.
[    49.110] (**) |-->Screen "Default Screen" (0)
[    49.110] (**) |   |-->Monitor "<default monitor>"
[    49.110] (==) No device specified for screen "Default Screen".
	Using the first device section listed.
[    49.110] (**) |   |-->Device "Default Device"
[    49.110] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[    49.110] (==) Automatically adding devices
[    49.110] (==) Automatically enabling devices
[    49.114] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    49.114] 	Entry deleted from font path.
[    49.118] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    49.118] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    49.118] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    49.118] (II) Loader magic: 0x7e17e0
[    49.119] (II) Module ABI versions:
[    49.119] 	X.Org ANSI C Emulation: 0.4
[    49.119] 	X.Org Video Driver: 10.0
[    49.119] 	X.Org XInput driver : 12.3
[    49.119] 	X.Org Server Extension : 5.0
[    49.120] (--) PCI:*(0:1:0:0) 10de:0a28:103c:363c rev 162, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00007000/128, BIOS @ 0x????????/524288
[    49.120] (II) Open ACPI successful (/var/run/acpid.socket)
[    49.120] (II) "extmod" will be loaded by default.
[    49.120] (II) "dbe" will be loaded by default.
[    49.120] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    49.120] (II) "record" will be loaded by default.
[    49.120] (II) "dri" will be loaded by default.
[    49.120] (II) "dri2" will be loaded by default.
[    49.120] (II) LoadModule: "glx"
[    49.120] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    49.125] (II) Module glx: vendor="NVIDIA Corporation"
[    49.125] 	compiled for 4.0.2, module version = 1.0.0
[    49.125] 	Module class: X.Org Server Extension
[    49.125] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
[    49.125] (II) Loading extension GLX
[    49.125] (II) LoadModule: "extmod"
[    49.126] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    49.126] (II) Module extmod: vendor="X.Org Foundation"
[    49.126] 	compiled for 1.10.1, module version = 1.0.0
[    49.126] 	Module class: X.Org Server Extension
[    49.126] 	ABI class: X.Org Server Extension, version 5.0
[    49.126] (II) Loading extension MIT-SCREEN-SAVER
[    49.126] (II) Loading extension XFree86-VidModeExtension
[    49.126] (II) Loading extension XFree86-DGA
[    49.126] (II) Loading extension DPMS
[    49.126] (II) Loading extension XVideo
[    49.126] (II) Loading extension XVideo-MotionCompensation
[    49.126] (II) Loading extension X-Resource
[    49.126] (II) LoadModule: "dbe"
[    49.126] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    49.126] (II) Module dbe: vendor="X.Org Foundation"
[    49.126] 	compiled for 1.10.1, module version = 1.0.0
[    49.126] 	Module class: X.Org Server Extension
[    49.126] 	ABI class: X.Org Server Extension, version 5.0
[    49.126] (II) Loading extension DOUBLE-BUFFER
[    49.126] (II) LoadModule: "record"
[    49.126] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    49.126] (II) Module record: vendor="X.Org Foundation"
[    49.126] 	compiled for 1.10.1, module version = 1.13.0
[    49.126] 	Module class: X.Org Server Extension
[    49.126] 	ABI class: X.Org Server Extension, version 5.0
[    49.126] (II) Loading extension RECORD
[    49.126] (II) LoadModule: "dri"
[    49.127] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    49.127] (II) Module dri: vendor="X.Org Foundation"
[    49.127] 	compiled for 1.10.1, module version = 1.0.0
[    49.127] 	ABI class: X.Org Server Extension, version 5.0
[    49.127] (II) Loading extension XFree86-DRI
[    49.127] (II) LoadModule: "dri2"
[    49.127] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    49.127] (II) Module dri2: vendor="X.Org Foundation"
[    49.127] 	compiled for 1.10.1, module version = 1.2.0
[    49.127] 	ABI class: X.Org Server Extension, version 5.0
[    49.127] (II) Loading extension DRI2
[    49.127] (II) LoadModule: "nvidia"
[    49.127] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    49.127] (II) Module nvidia: vendor="NVIDIA Corporation"
[    49.127] 	compiled for 4.0.2, module version = 1.0.0
[    49.127] 	Module class: X.Org Video Driver
[    49.154] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    49.181] (EE) NVIDIA:     system's kernel log for additional error messages.
[    49.208] (II) UnloadModule: "nvidia"
[    49.208] (II) Unloading nvidia
[    49.208] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    49.235] (EE) No drivers available.
[    49.261] 
Fatal server error:
[    49.313] no screens found
[    49.339] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    49.446] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    49.501] 

```

going through the same problem :(

---

### Post by wildmanne39 on 2011-10-05
Hi, I am sorry I am out of ideas.

---

### Post by pjd99 on 2011-10-05
> **wildmanne39 said:**
> Hi, I am sorry I am out of ideas.
So am I, and I think my advice will only keep running**** josephellengar in circles.

Before I go, here are a few threads with similar issues (nVidia and 2.6.38-11):
[http://ubuntuforums.org/showthread.php?t=1804394](http://ubuntuforums.org/showthread.php?t=1804394)
[http://ubuntuforums.org/showthread.php?t=1831892](http://ubuntuforums.org/showthread.php?t=1831892)

---

### Post by wildmanne39 on 2011-10-05
Hi, do you have two video cards, on an optimus card?

If so then have a look at this link.
[http://ubuntuforums.org/showthread.php?p=11277247#post11277247](http://ubuntuforums.org/showthread.php?p=11277247#post11277247)
post 26.
Thank you

---

### Post by josephellengar on 2011-10-06
Hi. I have one more question for anyone who is still observing this thread. I restored my backup, so now I have a working 10.10 release again. Is there anything that I can do before I upgrade that would make the upgrade more likely to work? For example, removing or installing some drivers, changing kernels around, or the like?

---

### Post by wildmanne39 on 2011-10-06
Hi, no not that I know of, I recommend doing a clean install, upgrades are more likely to fail, 11.04 has had a lot of problem when upgrading.
Thank you

---

### Post by josephellengar on 2011-10-06
> **wildmanne39 said:**
> Hi, no not that I know of, I recommend doing a clean install, upgrades are more likely to fail, 11.04 has had a lot of problem when upgrading.
Thank you

When 12.04 is released (I think it will be an LTS release) will I be able to upgrade directly from 10.10 to 12.04?

---

### Post by wildmanne39 on 2011-10-06
Hi, no I believe you have to upgrade to 11.04 first.

You can upgrade LTS versions of ubuntu right to another LTS version though.
Thank you

---

