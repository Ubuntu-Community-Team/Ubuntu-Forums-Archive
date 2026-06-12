---
title: "Grub2 doesn't list Fedora, even though upgrade-grub &quot;finds&quot; it."
date: 2010-01-21
forum: General Help
---

### Post by joeblurton on 2010-01-21
Hey guys, I've got a little problem with GRUB 2, and hope you can help!

In general I love Ubuntu Karmic, and think it's the most polished Gnome distro out there, but since installing it on my laptop alongside Fedora I haven't been able to boot into the latter.

I know that I could fix it by adding an entry into the 40_custom file, but wonder if there's a simpler fix.

The command > sudo update-grub actually finds and lists the Fedora Constantine kernel, but it still doesn't appear in the bootloader menu. Before I delve around and break something, does this mean that there's a line commented out in one of the config files?

I'm not going to slag off Grub 2 because I can see that it has clear benefits, especially for power users, and I don't mind change if it brings clear benefits. So long, /boot/grub/menu.lst, and thanks for all the fish!

---

### Post by joeblurton on 2010-01-21
I suppose I'm just interested to see why Grub doesn't seem to show the alternate OSs, rather than specifically looking for a solution. I can fix it, but if I'm right and there's an easier way, that'll be handy as a way of getting to know Grub 2.

---

### Post by Leppie on 2010-01-21
was this a clean install or an upgrade? if it's an upgrade, you probably still are using grub legacy. even if this was a clean install, you could have ended up with grub legacy booting your system.
you can check the version like this:
```
sudo grub-install -v
```
grub2 is v.1.97
if you do have grub2 installed, install it to the mbr like this:
```
sudo grub-install --recheck /dev/sda
```

if you want to be sure you don't have grub legacy on your system anymore, remove the packages and re-install grub2 like this:
```
sudo apt-get purge grub grub-pc grub-common
sudo apt-get install grub-pc grub-common
```

---

### Post by Leppie on 2010-01-21
> **joeblurton said:**
> I suppose I'm just interested to see why Grub doesn't seem to show the alternate OSs, rather than specifically looking for a solution. I can fix it, but if I'm right and there's an easier way, that'll be handy as a way of getting to know Grub 2.
if you want to analyse what exactly is going on with your system, [download and run meierfra's script]("http://http://sourceforge.net/projects/bootinfoscript/"). the generated RESULTS.txt will give you plenty of information, if you need help analysing the output, post the file.

---

### Post by joeblurton on 2010-01-21
Leppie, thanks for this. Here's the full output of RESULTS.txt:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /grub.
 => No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 12 (Constantine) 
                       Kernel on an ()
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90549054

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    33,792,062    33,792,000  83 Linux
/dev/sda2    *     33,792,063    34,201,662       409,600  83 Linux
/dev/sda3          34,201,663    56,307,131    22,105,469  8e Linux LVM
/dev/sda4          56,307,825    58,589,054     2,281,230   5 Extended
/dev/sda5          56,323,890    58,589,054     2,265,165  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 5027 MB, 5027097600 bytes
240 heads, 63 sectors/track, 649 cylinders, total 9818550 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b84ee

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     9,812,879     9,812,817  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="Fedora-12-i686-L" UUID="a24a9425-72f5-4a98-9e3a-b78e72437522" TYPE="ext4" 
/dev/sda2: UUID="d9a2edb0-cfd2-443b-8f13-ae94fc193acc" TYPE="ext2" 
/dev/sda3: UUID="a8b38af8-3a52-4761-beca-8a835d64e58c" TYPE="ext4" 
/dev/sda5: UUID="f7d2c28b-a4a9-452d-ac90-b231d7791b30" TYPE="swap" 
/dev/sdb1: UUID="38bd2a78-004f-4724-b0d9-82d1256b8b5e" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda2 on /boot type ext2 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/joe/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=joe)


=============================== sda1/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Wed Dec  9 19:46:49 2009
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=a24a9425-72f5-4a98-9e3a-b78e72437522 /                       ext4    defaults        1 1
UUID=e4fa5faf-7bde-4c83-aea7-5be7ba658db7 /boot                   ext4    defaults        1 2
UUID=f7d2c28b-a4a9-452d-ac90-b231d7791b30 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

============================= sda2/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set a8b38af8-3a52-4761-beca-8a835d64e58c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d9a2edb0-cfd2-443b-8f13-ae94fc193acc
	linux	/vmlinuz-2.6.31-17-generic root=UUID=a8b38af8-3a52-4761-beca-8a835d64e58c ro   quiet splash
	initrd	/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d9a2edb0-cfd2-443b-8f13-ae94fc193acc
	linux	/vmlinuz-2.6.31-17-generic root=UUID=a8b38af8-3a52-4761-beca-8a835d64e58c ro single 
	initrd	/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d9a2edb0-cfd2-443b-8f13-ae94fc193acc
	linux	/vmlinuz-2.6.31-14-generic root=UUID=a8b38af8-3a52-4761-beca-8a835d64e58c ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d9a2edb0-cfd2-443b-8f13-ae94fc193acc
	linux	/vmlinuz-2.6.31-14-generic root=UUID=a8b38af8-3a52-4761-beca-8a835d64e58c ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda2: Location of files loaded by Grub: ===================


  17.3GB: grub/core.img
  17.3GB: grub/grub.cfg
  17.3GB: initrd.img-2.6.31-14-generic
  17.3GB: initrd.img-2.6.31-17-generic
  17.3GB: vmlinuz-2.6.31-14-generic
  17.3GB: vmlinuz-2.6.31-17-generic

=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set a8b38af8-3a52-4761-beca-8a835d64e58c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d9a2edb0-cfd2-443b-8f13-ae94fc193acc
	linux	/vmlinuz-2.6.31-17-generic root=UUID=a8b38af8-3a52-4761-beca-8a835d64e58c ro   quiet splash
	initrd	/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d9a2edb0-cfd2-443b-8f13-ae94fc193acc
	linux	/vmlinuz-2.6.31-17-generic root=UUID=a8b38af8-3a52-4761-beca-8a835d64e58c ro single 
	initrd	/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d9a2edb0-cfd2-443b-8f13-ae94fc193acc
	linux	/vmlinuz-2.6.31-14-generic root=UUID=a8b38af8-3a52-4761-beca-8a835d64e58c ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d9a2edb0-cfd2-443b-8f13-ae94fc193acc
	linux	/vmlinuz-2.6.31-14-generic root=UUID=a8b38af8-3a52-4761-beca-8a835d64e58c ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=a8b38af8-3a52-4761-beca-8a835d64e58c /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=d9a2edb0-cfd2-443b-8f13-ae94fc193acc /boot           ext2    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=f7d2c28b-a4a9-452d-ac90-b231d7791b30 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  17.5GB: boot/grub/core.img
  17.5GB: boot/grub/grub.cfg
  17.5GB: boot/initrd.img-2.6.31-14-generic
  17.5GB: boot/initrd.img-2.6.31-17-generic
  17.5GB: boot/vmlinuz-2.6.31-14-generic
  17.5GB: boot/vmlinuz-2.6.31-17-generic
  17.5GB: initrd.img
  17.5GB: initrd.img.old
  17.5GB: vmlinuz
  17.5GB: vmlinuz.old

================================ sdb1/menu.lst: ================================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,1)
#          kernel /vmlinuz-version ro root=/dev/sda1
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=6
splashimage=(hd0,1)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.31.9-174.fc12.i686)
	root (hd0,1)
	kernel /vmlinuz-2.6.31.9-174.fc12.i686 ro root=UUID=a24a9425-72f5-4a98-9e3a-b78e72437522 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=uk rhgb quiet
	initrd /initramfs-2.6.31.9-174.fc12.i686.img
title Fedora (2.6.31.6-166.fc12.i686)
	root (hd0,1)
	kernel /vmlinuz-2.6.31.6-166.fc12.i686 ro root=UUID=a24a9425-72f5-4a98-9e3a-b78e72437522 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=uk rhgb quiet
	initrd /initramfs-2.6.31.6-166.fc12.i686.img
title Fedora (2.6.31.6-162.fc12.i686)
	root (hd0,1)
	kernel /vmlinuz-2.6.31.6-162.fc12.i686 ro root=UUID=a24a9425-72f5-4a98-9e3a-b78e72437522 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=uk rhgb quiet
	initrd /initramfs-2.6.31.6-162.fc12.i686.img
title Chrunchbang
	root (hd0,2)
	chainloader +1

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: menu.lst
```

Looks like quite a mess to me. The system's gone through a few changes of late, and Karmic is a new install ontop of #! 9.04.

So I'm definitely using GRUB 2, and as I mentioned, even though the cli output of update-grub looks like this:

```
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /memtest86+.bin
Found Fedora release 12 (Constantine) on /dev/sda1
done

```

- there is no option for Fedora at boot. So I'm puzzled by what's missing!

---

### Post by meierfra. on 2010-01-21
It seems the Fedora kernels are missing. But to get a better picture, could you install "lvm2" via:

```
sudo apt-get install lvm2
```

and then run the boot info script again.  (without the lvm2 package the boot info script is not able to read LVM partitions)

Post the new RESULTS.txt (although it might be called RESULTS1.txt)


Edit: Something is funny. Do you already have lvm2 installed?

---

### Post by joeblurton on 2010-01-21
Hey meierfra, thanks. And that's a clever little script!

Here's the new output after installing lvm2: [Edit: It didn't seem to be installed according to apt.]

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /grub.
 => No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 12 (Constantine) 
                       Kernel on an ()
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90549054

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    33,792,062    33,792,000  83 Linux
/dev/sda2    *     33,792,063    34,201,662       409,600  83 Linux
/dev/sda3          34,201,663    56,307,131    22,105,469  8e Linux LVM
/dev/sda4          56,307,825    58,589,054     2,281,230   5 Extended
/dev/sda5          56,323,890    58,589,054     2,265,165  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 5027 MB, 5027097600 bytes
240 heads, 63 sectors/track, 649 cylinders, total 9818550 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b84ee

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     9,812,879     9,812,817  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="Fedora-12-i686-L" UUID="a24a9425-72f5-4a98-9e3a-b78e72437522" TYPE="ext4" 
/dev/sda2: UUID="d9a2edb0-cfd2-443b-8f13-ae94fc193acc" TYPE="ext2" 
/dev/sda3: UUID="a8b38af8-3a52-4761-beca-8a835d64e58c" TYPE="ext4" 
/dev/sda5: UUID="f7d2c28b-a4a9-452d-ac90-b231d7791b30" TYPE="swap" 
/dev/sdb1: UUID="38bd2a78-004f-4724-b0d9-82d1256b8b5e" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda2 on /boot type ext2 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/joe/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=joe)


=============================== sda1/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Wed Dec  9 19:46:49 2009
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=a24a9425-72f5-4a98-9e3a-b78e72437522 /                       ext4    defaults        1 1
UUID=e4fa5faf-7bde-4c83-aea7-5be7ba658db7 /boot                   ext4    defaults        1 2
UUID=f7d2c28b-a4a9-452d-ac90-b231d7791b30 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

============================= sda2/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set a8b38af8-3a52-4761-beca-8a835d64e58c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d9a2edb0-cfd2-443b-8f13-ae94fc193acc
	linux	/vmlinuz-2.6.31-17-generic root=UUID=a8b38af8-3a52-4761-beca-8a835d64e58c ro   quiet splash
	initrd	/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d9a2edb0-cfd2-443b-8f13-ae94fc193acc
	linux	/vmlinuz-2.6.31-17-generic root=UUID=a8b38af8-3a52-4761-beca-8a835d64e58c ro single 
	initrd	/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d9a2edb0-cfd2-443b-8f13-ae94fc193acc
	linux	/vmlinuz-2.6.31-14-generic root=UUID=a8b38af8-3a52-4761-beca-8a835d64e58c ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d9a2edb0-cfd2-443b-8f13-ae94fc193acc
	linux	/vmlinuz-2.6.31-14-generic root=UUID=a8b38af8-3a52-4761-beca-8a835d64e58c ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda2: Location of files loaded by Grub: ===================


  17.3GB: grub/core.img
  17.3GB: grub/grub.cfg
  17.3GB: initrd.img-2.6.31-14-generic
  17.3GB: initrd.img-2.6.31-17-generic
  17.3GB: vmlinuz-2.6.31-14-generic
  17.3GB: vmlinuz-2.6.31-17-generic

=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set a8b38af8-3a52-4761-beca-8a835d64e58c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d9a2edb0-cfd2-443b-8f13-ae94fc193acc
	linux	/vmlinuz-2.6.31-17-generic root=UUID=a8b38af8-3a52-4761-beca-8a835d64e58c ro   quiet splash
	initrd	/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d9a2edb0-cfd2-443b-8f13-ae94fc193acc
	linux	/vmlinuz-2.6.31-17-generic root=UUID=a8b38af8-3a52-4761-beca-8a835d64e58c ro single 
	initrd	/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d9a2edb0-cfd2-443b-8f13-ae94fc193acc
	linux	/vmlinuz-2.6.31-14-generic root=UUID=a8b38af8-3a52-4761-beca-8a835d64e58c ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d9a2edb0-cfd2-443b-8f13-ae94fc193acc
	linux	/vmlinuz-2.6.31-14-generic root=UUID=a8b38af8-3a52-4761-beca-8a835d64e58c ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=a8b38af8-3a52-4761-beca-8a835d64e58c /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=d9a2edb0-cfd2-443b-8f13-ae94fc193acc /boot           ext2    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=f7d2c28b-a4a9-452d-ac90-b231d7791b30 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  17.5GB: boot/grub/core.img
  17.5GB: boot/grub/grub.cfg
  17.5GB: boot/initrd.img-2.6.31-14-generic
  17.5GB: boot/initrd.img-2.6.31-17-generic
  17.5GB: boot/vmlinuz-2.6.31-14-generic
  17.5GB: boot/vmlinuz-2.6.31-17-generic
  17.5GB: initrd.img
  17.5GB: initrd.img.old
  17.5GB: vmlinuz
  17.5GB: vmlinuz.old

================================ sdb1/menu.lst: ================================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,1)
#          kernel /vmlinuz-version ro root=/dev/sda1
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=6
splashimage=(hd0,1)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.31.9-174.fc12.i686)
	root (hd0,1)
	kernel /vmlinuz-2.6.31.9-174.fc12.i686 ro root=UUID=a24a9425-72f5-4a98-9e3a-b78e72437522 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=uk rhgb quiet
	initrd /initramfs-2.6.31.9-174.fc12.i686.img
title Fedora (2.6.31.6-166.fc12.i686)
	root (hd0,1)
	kernel /vmlinuz-2.6.31.6-166.fc12.i686 ro root=UUID=a24a9425-72f5-4a98-9e3a-b78e72437522 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=uk rhgb quiet
	initrd /initramfs-2.6.31.6-166.fc12.i686.img
title Fedora (2.6.31.6-162.fc12.i686)
	root (hd0,1)
	kernel /vmlinuz-2.6.31.6-162.fc12.i686 ro root=UUID=a24a9425-72f5-4a98-9e3a-b78e72437522 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=uk rhgb quiet
	initrd /initramfs-2.6.31.6-162.fc12.i686.img
title Chrunchbang
	root (hd0,2)
	chainloader +1

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: menu.lst
```

Out of interest, what are we looking for here?

---

### Post by meierfra. on 2010-01-21
Well, the output is the same since you actually do not have an LVM partition. I just got confused since "/dev/sda3" is mislabeled in the partition table:

> dev/sda3          34,201,663    56,307,131    22,105,469  8e Linux LVM

But actually it is a regular ext4 partition:

> dev/sda3: UUID="a8b38af8-3a52-4761-beca-8a835d64e58c" TYPE="ext4" 

Luckily the boot info script is smarter than I'm and processed  the partition correctly.

> Out of interest, what are we looking for here? 
For the Fedora kernel, a file like "kernel /vmlinuz-2.6.31.6-166.fc12.i686".  The boot info script did not find any such file. 

The Fedora fstab might explain what happened:

> UUID=e4fa5faf-7bde-4c83-aea7-5be7ba658db7 /boot                   ext4    defaults    

You used to have a Fedora boot partition with UUID=e4fa5faf-7bde-4c83-aea7-5be7ba658db7. But it does not exists any more.

 
You probably could  edit your Fedora fstab and  remove the  line for the boot partition,  chroot into the Fedora partition and reinstall the kernels.  But I really don't know enough about Fedora to help you with that.

---

### Post by joeblurton on 2010-01-21
Yes, I see now. I've always tried to have a seperate boot partition, and assumed that it was okay to overwrite this with any new install, replacing one grub setup with another. Since F12 uses Grub Legacy, that's actually a problem. So what happened is that installing Grub 2 on sda2 removed the Fedora kernel images? Yes, I can see vmlinuz and initrd.img files there (Ubuntu's). D'oh!

I'll look into rescuing Fedora tomorrow, and see if I can get back in.

Thanks for all the help. I'll post again with an update if I succeed.

It just goes to show, users really are a computer's worst enemy! </learning the hard way>!

---

### Post by meierfra. on 2010-01-21
> So what happened is that installing Grub 2 on sda2 removed the Fedora kernel images? 
Since the UUID of /dev/sda2 changed, /dev/sda2 must have been formated during the Ubuntu installation. 

> I'll look into rescuing Fedora tomorrow,
Good luck.

---

### Post by jcoles on 2010-07-09
Thanks Leppie,

I also had both GRUB and GRUB 2 present, with the old (v0.97) GRUB doing the boot but the new GRUB, (v1.98 ) being used when I called update-grub. It's quite confusing when update-grub doesn't change the boot menu. 

Your instructions for removing the old GRUB and replacing it with the new one fixed the problem for me.

---

