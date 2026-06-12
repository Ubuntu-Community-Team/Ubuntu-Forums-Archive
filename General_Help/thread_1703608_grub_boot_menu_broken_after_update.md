---
title: "grub boot menu broken after update"
date: 2011-03-09
forum: General Help
---

### Post by hammeraxe on 2011-03-09
I'm running Ubuntu 10.10 and Windows 7 dual boot. I had removed all but one of the Ubuntu kernels and boot options from grub menu to reduce clutter. Today I ran an update (admittedly, I've been suppressing the update manager lately) and after that update I was asked to restart. Now all the entries from the boot menu except for Windows 7 are gone.

I understand I need to boot a live cd/usb and fix the grub config from within? But how do I ensure this does not happen again?

---

### Post by Rubi1200 on 2011-03-09
Hi,
we need to get a better overview of the current state of your setup.

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by hammeraxe on 2011-03-09
ok, there it is. i've got separate partitions for both OSes and another one for data on sda. and sdb is the flash drive im booting this from


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda4 starts at sector 122865120.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   102,402,047   102,400,000   7 HPFS/NTFS
/dev/sda2         102,402,048   120,834,047    18,432,000  83 Linux
/dev/sda3         120,834,048   122,863,615     2,029,568  82 Linux swap / Solaris
/dev/sda4         122,865,120   625,137,344   502,272,225   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1047 MB, 1047789568 bytes
255 heads, 63 sectors/track, 127 cylinders, total 2046464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     2,046,463     2,046,401   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        152D65277880C77D                       ntfs       Win7                          
/dev/sda2        76f703e3-1d37-4124-90fb-755f762100b8   ext4       Ubuntu                        
/dev/sda3        240a38bd-06ec-43e0-9e3c-f9b07b950415   swap       swap                          
/dev/sda4        5040736940735526                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0C1A-1C7F                              vfat       EDG                           
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set default="1"
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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 76f703e3-1d37-4124-90fb-755f762100b8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 76f703e3-1d37-4124-90fb-755f762100b8
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry '2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 76f703e3-1d37-4124-90fb-755f762100b8
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=76f703e3-1d37-4124-90fb-755f762100b8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry '2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 76f703e3-1d37-4124-90fb-755f762100b8
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=76f703e3-1d37-4124-90fb-755f762100b8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 152d65277880c77d
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=76f703e3-1d37-4124-90fb-755f762100b8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=240a38bd-06ec-43e0-9e3c-f9b07b950415 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  57.3GB: boot/grub/core.img
  61.2GB: boot/grub/grub.cfg
  53.5GB: boot/initrd.img-2.6.35-24-generic-pae
  53.9GB: boot/initrd.img-2.6.35-27-generic-pae
  57.2GB: boot/vmlinuz-2.6.35-24-generic-pae
  57.4GB: boot/vmlinuz-2.6.35-27-generic-pae
  53.9GB: initrd.img
  53.5GB: initrd.img.old
  57.4GB: vmlinuz
  57.2GB: vmlinuz.old
```

---

### Post by Rubi1200 on 2011-03-10
Odd, because the script results don't seem to indicate a problem. At least not that I can see immediately.

I think the easiest thing to do is simply run a GRUB install from the LiveCD/USB:

```
sudo mount /dev/sda2 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
```Run 

```
sudo update-grub
```back in Ubuntu to pick up the Windows install.

Let me know how it works out please.

While on the LiveCD/USB it is also worthwhile getting rid of this file from sda1: > /grldr

---

### Post by hammeraxe on 2011-03-10
Unfortunately that didn't help. I can still only see the Windows 7 entry in the boot menu :/

---

### Post by YesWeCan on 2011-03-10
> **hammeraxe said:**
> I'm running Ubuntu 10.10 and Windows 7 dual boot. I had removed all but one of the Ubuntu kernels and boot options from grub menu to reduce clutter.
Interesting symptoms. How exactly did you remove the entries?

---

### Post by hammeraxe on 2011-03-10
I wish I could remember, but clearly it was the wrong way :D

Grub2 is a complete puzzle to me. I think I might have edited the files in /etc/grub.d/

---

### Post by YesWeCan on 2011-03-10
Grub is a little complicated.
You may need to reinstall Grub from scratch.

Try manually booting into your Ubuntu from the Grub menu.
See: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) in the section called "Using CLI to Boot"

```
set root=(hd0,2)
linux /vmlinuz root=/dev/sda2 ro
initrd /initrd.img
boot
```

If the only problem is Grub2 then this should get you booted. Once booted you probably want to reinstall Grub2 afresh.
sudo apt-get install grub-pc (I think)


PS: CLI = Command Line Interface

---

### Post by Rubi1200 on 2011-03-10
It might be easiest to purge and reinstall GRUB from the LiveCD/USB:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by hammeraxe on 2011-03-10
YesWeCan's advice worked nicely. update-grub found two kernels and Windows 7 installation. But when I reboot, the boot menu only shows recovery modes for the two kernels. They boot perfectly well after I hit "proceed with normal boot". How exactly are you supposed to change the menu entries in grub2?

---

### Post by YesWeCan on 2011-03-10
Getting there...
Would you post the output of 'ls /boot' ?

and also /boot/grub/grub.cfg

---

### Post by hammeraxe on 2011-03-10
There we go


ls /boot
```
abi-2.6.35-27-generic-pae         memtest86+_multiboot.bin
config-2.6.35-27-generic-pae      System.map-2.6.35-27-generic-pae
grub                              vmcoreinfo-2.6.35-27-generic-pae
initrd.img-2.6.35-27-generic-pae  vmlinuz-2.6.35-27-generic-pae
memtest86+.bin
```



/boot/grub/grub.cfg
```
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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 76f703e3-1d37-4124-90fb-755f762100b8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 76f703e3-1d37-4124-90fb-755f762100b8
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry '2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 76f703e3-1d37-4124-90fb-755f762100b8
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=76f703e3-1d37-4124-90fb-755f762100b8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 76f703e3-1d37-4124-90fb-755f762100b8
	echo	'Loading Linux 2.6.35-27-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=76f703e3-1d37-4124-90fb-755f762100b8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 152d65277880c77d
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
```

---

### Post by YesWeCan on 2011-03-10
The grub.cfg seems to have a mistake in it. The line in red below probably should not be there at all.
Try deleting it and rebooting.
Then if it is now ok, do update-grub again and see whether the line returns. If so, it is probably an error in /etc/grub.d somewhere.

```
### BEGIN /etc/grub.d/10_linux ###
[COLOR="Red"]menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os {[/COLOR]
menuentry '2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 76f703e3-1d37-4124-90fb-755f762100b8
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=76f703e3-1d37-4124-90fb-755f762100b8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
```

---

### Post by hammeraxe on 2011-03-10
yeah, you're absolutely right. Deleting the line returned all the boot options to the menu, but update-grub brought the line back

---

### Post by YesWeCan on 2011-03-10
Have a look in /etc/grub.d/10_linux

I am not quite sure how Grub works at this level. I think the update-grub runs this file to generate the linux boot entries in grub.cfg. Obviously it is making a mess of doing this.

I would have thought that reinstalling grub would have replaced this file with a fresh, good one. Maybe it didn't.

Here is my 10_linux file...perhaps you can compare:
```
#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
bindir=${exec_prefix}/bin
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib

export TEXTDOMAIN=grub
export TEXTDOMAINDIR=@LOCALEDIR@

CLASS="--class gnu-linux --class gnu --class os"

if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
  OS=GNU/Linux
else
  OS="${GRUB_DISTRIBUTOR}"
  CLASS="--class $(echo ${GRUB_DISTRIBUTOR} | tr '[A-Z]' '[a-z]' | cut -d' ' -f1) ${CLASS}"
fi

# loop-AES arranges things so that /dev/loop/X can be our root device, but
# the initrds that Linux uses don't like that.
case ${GRUB_DEVICE} in
  /dev/loop/*|/dev/loop[0-9])
    GRUB_DEVICE=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
    # We can't cope with devices loop-mounted from files here.
    case ${GRUB_DEVICE} in
      /dev/*) ;;
      *) exit 0 ;;
    esac
  ;;
esac

if [ "x${GRUB_DEVICE_UUID}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] \
    || ! test -e "/dev/disk/by-uuid/${GRUB_DEVICE_UUID}" \
    || [ "`grub-probe -t abstraction --device ${GRUB_DEVICE} | sed -e 's,.*\(lvm\).*,\1,'`" = "lvm"  ] ; then
  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
else
  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
fi

# add crashkernel option if we have the required tools
if [ -x "/usr/bin/makedumpfile" ] && [ -x "/sbin/kexec" ]; then
    GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA crashkernel=384M-2G:64M,2G-:128M"
fi

linux_entry ()
{
  os="$1"
  version="$2"
  recovery="$3"
  args="$4"
  if ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s, with Linux %s")"
  fi
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
  cat << EOF
	recordfail
EOF
  save_default_entry | sed -e "s/^/\t/"

  if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
	  cat << EOF
	set gfxpayload=$GRUB_GFXPAYLOAD_LINUX
EOF
  fi

  if [ -z "${prepare_boot_cache}" ]; then
    prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
  fi
  printf '%s\n' "${prepare_boot_cache}"
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
	echo	'$(printf "$(gettext_quoted "Loading Linux %s ...")" ${version})'
EOF
  fi
  cat << EOF
	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
	echo	'$(gettext_quoted "Loading initial ramdisk ...")'
EOF
  fi
  if test -n "${initrd}" ; then
    cat << EOF
	initrd	${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

blacklisted_kernel() {
  local r=""
  case "${1}" in
    *-ec2) r="linux-ec2";; # LP: #671097
  esac
  [ -n "${r}" ] && { echo "Skipping linux image [$r]: ${1}" >&2; return 0; }
  return 1;
}

list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
        if grub_file_is_not_garbage "$i" &&
           ! blacklisted_kernel "$i"; then
          echo -n "$i ";
        fi
      done`
prepare_boot_cache=

while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"

  initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" \
	   "initrd-${version}" "initrd.img-${alt_version}" \
	   "initrd-${alt_version}.img" "initrd-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done
  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  else
    # "UUID=" magic is parsed by initrds.  Since there's no initrd, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

  linux_entry "${OS}" "${version}" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}" "${version}" true \
	"single ${GRUB_CMDLINE_LINUX}"
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
done
```

---

### Post by hammeraxe on 2011-03-10
The files were quite different so I decided to try and reinstall grub again, but this time purging all the settings as well. Now everything works perfectly.

(I used this guide btw [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099))

---

