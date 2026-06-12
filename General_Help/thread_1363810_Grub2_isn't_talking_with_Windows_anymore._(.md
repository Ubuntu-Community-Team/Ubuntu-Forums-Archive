---
title: "Grub2 isn't talking with Windows anymore. :("
date: 2009-12-24
forum: General Help
---

### Post by Sugi on 2009-12-24
I can't get grub2 to talk with my Windows XP partition.  I only have options to run ubuntu kernel 2.6.28-16 server, kernel 2.6.28-14 server, and memtest.  No Windows.

I have tried updating my grub2 and updating my grub.
(sudo update-grub2) (sudo update-grub).

I have also tried making a 11_windows and still no go.
It said something about too  many entries for Windows Xp.
[http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/)

I have also looked over some other pages, but nothing has helped.  I must be overlooking something here.  Can someone help me out?

fdisk
>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2079    16699536    7  HPFS/NTFS
/dev/sda2            2080        3648    12602992+   5  Extended
/dev/sda5            2080        3576    12024621   83  Linux
/dev/sda6            3577        3648      578308+  82  Linux swap / Solaris

Some links that should help, but I still can't get my grub2 up and working correctly.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[http://ubuntuforums.org/showthread.php?t=1296301](http://ubuntuforums.org/showthread.php?t=1296301)

Spec:
Ubuntu 9.10 32 bit
Need Grub2 entry for Windows XP
Grub2

Thanks for reading,
Sugi

---

### Post by Sugi on 2009-12-24
bumpy bump

---

### Post by Sugi on 2009-12-25
bump

---

### Post by Leppie on 2009-12-25
could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.TXT?
this may shed some light on the nature of your issue.

---

### Post by Sugi on 2009-12-25
lieqie, Yep, I still have that file, I'll post the information within at the end of this post.  Please scroll down.

Leppie
```
~$ sh boot_info_script042.sh 
Please use "sudo" or become "root" to run this script.
~$ sudo sh boot_info_script042.sh 
[sudo] password for : 
~$ ./boot_info_script042.sh 
bash: ./boot_info_script042.sh: Permission denied
~$ sudo ./boot_info_script042.sh 
sudo: ./boot_info_script042.sh: command not found

```
Can I not run sh scripts anymore. :(  What am I missing here?


/etc/grub.d/30_os-prober
```
#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
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
libdir=${exec_prefix}/lib

. ${libdir}/grub/grub-mkconfig_lib

found_other_os=

adjust_timeout () {
  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${GRUB_HIDDEN_TIMEOUT}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
	verbose=
      else
	verbose=" --verbose"
      fi

      if [ "x${GRUB_HIDDEN_TIMEOUT}" = "x0" ] ; then
	cat <<EOF
if [ \${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
      else
	cat << EOF
if [ \${timeout} != -1 ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then
  adjust_timeout
  exit 0
fi

if [ -z "`which os-prober 2> /dev/null`" -o -z "`which linux-boot-prober 2> /dev/null`" ] ; then
  # missing os-prober and/or linux-boot-prober
  adjust_timeout
  exit 0
fi

OSPROBED="`os-prober | tr ' ' '^' | paste -s -d ' '`"
if [ -z "${OSPROBED}" ] ; then
  # empty os-prober output, nothing doing
  adjust_timeout
  exit 0
fi

for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

  echo "Found ${LONGNAME} on ${DEVICE}" >&2
  found_other_os=1

  case ${BOOT} in
    chain)

      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"

      case ${LONGNAME} in
	Windows\ Vista*|Windows\ 7*)
	;;
	*)
	  cat << EOF
	drivemap -s (hd0) \${root}
EOF
	;;
      esac

      cat <<EOF
	chainloader +1
}
EOF
    ;;
    linux)
      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"

      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"

        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

         if [ "${LROOT}" != "${LBOOT}" ]; then
           LKERNEL="${LKERNEL#/boot}"
           LINITRD="${LINITRD#/boot}"
         fi

        cat << EOF
menuentry "${LLABEL} (on ${DEVICE})" {
EOF
	save_default_entry | sed -e "s/^/\t/"
	prepare_grub_to_access_device ${LBOOT} | sed -e "s/^/\t/"
	cat <<  EOF
	linux ${LKERNEL} ${LPARAMS}
EOF
        if [ -n "${LINITRD}" ] ; then
          cat << EOF
	initrd ${LINITRD}
EOF
        fi
        cat << EOF
}
EOF
      done
    ;;
    macosx)
      OSXUUID="`grub-probe --target=fs_uuid --device ${DEVICE} 2> /dev/null`"
        cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
EOF
	save_default_entry | sed -e "s/^/\t/"
	prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
	cat << EOF
        insmod vbe
        do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             do_resume=1
           fi
        fi
        if [ \$do_resume == 0 ]; then
           xnu_uuid ${OSXUUID} uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=\${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devtree.txt ]; then
              xnu_devtree /Extra/devtree.txt
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
EOF
    ;;
    hurd|*)
      echo "  ${LONGNAME} is not yet supported by grub-mkconfig." >&2
    ;;
  esac
done

adjust_timeout
```

Thanks guys and sorry for the slow reply,
Sugi

---

### Post by Leppie on 2009-12-25
i think you forgot to make it executable:
```
$sudo chmod +x boot_info_script042.sh
```

---

### Post by Sugi on 2009-12-25
Ha, good point.
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90909090

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    33,399,134    33,399,072   7 HPFS/NTFS
/dev/sda2          33,399,135    58,605,119    25,205,985   5 Extended
/dev/sda5          33,399,198    57,448,439    24,049,242  83 Linux
/dev/sda6          57,448,503    58,605,119     1,156,617  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda5: UUID="826a5efd-551a-43d5-bf86-56afdcb23151" TYPE="ext4" 
/dev/sda6: UUID="13c3e472-1799-4441-afaa-4d68f18ff0f1" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/user/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=user)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 826a5efd-551a-43d5-bf86-56afdcb23151
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 826a5efd-551a-43d5-bf86-56afdcb23151
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=826a5efd-551a-43d5-bf86-56afdcb23151 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 826a5efd-551a-43d5-bf86-56afdcb23151
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=826a5efd-551a-43d5-bf86-56afdcb23151 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 826a5efd-551a-43d5-bf86-56afdcb23151
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=826a5efd-551a-43d5-bf86-56afdcb23151 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 826a5efd-551a-43d5-bf86-56afdcb23151
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=826a5efd-551a-43d5-bf86-56afdcb23151 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=826a5efd-551a-43d5-bf86-56afdcb23151 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=13c3e472-1799-4441-afaa-4d68f18ff0f1 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  17.1GB: boot/grub/grub.cfg
  17.1GB: boot/initrd.img-2.6.31-14-generic
  17.1GB: boot/initrd.img-2.6.31-16-generic
  17.1GB: boot/vmlinuz-2.6.31-14-generic
  17.1GB: boot/vmlinuz-2.6.31-16-generic
  17.1GB: initrd.img
  17.1GB: initrd.img.old
  17.1GB: vmlinuz
  17.1GB: vmlinuz.old
```

Sugi

---

### Post by Sugi on 2009-12-25
bump

---

### Post by Leppie on 2009-12-25
i think you have some filesystem issue (at least, it's not being recognized):
> sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

check your xp partition for errors, then run update-grub again.

---

### Post by Leppie on 2009-12-25
you could try testdisk:
```
$sudo apt-get install testdisk
```

but i'd suggest you make a backup of the partition first (if you have important files on the xp partition).

---

### Post by Sugi on 2009-12-27
Well, I am clueless as what to do.  I can't get into the partition from ubuntu or a livecd.  I can't backup anything, which isn't too bad, but there is some files I would like to keep.

```
sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

I haven't ran testdrive yet, becasue I can't backup anything.

Sugi

---

### Post by ranch hand on 2009-12-27
Do you have the install disk for your MS?

If so I would try running the recovery part of it.  I do not use MS at all so I am of little help there.  However, I do know that you can restore the boot system to MS.   You could try that and see if it boots.

Restoring grub2 is done with these directions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

ignoring the edit files part as you do not need it.

If MS boots with its bootloader in the MBR, I would put the menu entry for it in your /etc/grub.d/40_custom file after restoring grub2 to the MBR.

---

### Post by Sugi on 2009-12-30
I did the restore feature which it kinda did the job.  It also installed the windows version of MBR.  I backed up everything and I am going to reinstall everything including the OSs.

Thanks everyone for the help,
Sugi

---

### Post by ranch hand on 2009-12-30
I would try to find the problem before reinstalling.

If redoing the MS boot to mbr worked and then reinstalling grub2 worked but neither worked up to snuff, then I would be doing some serious looking at my hard drive for a start.  It would not hurt to have someone run a test or two on your power unit either.

---

### Post by Sugi on 2009-12-31
I have tried to install the MS MBR and the grub2 MBR, and neither of them can see one another.  I haven't reformatted, installed or touch any of the partitions.  If you prefer I can do some hardware test.  What applications do you have in mind?

Sugi

---

### Post by Leppie on 2009-12-31
there's disk images on the net containing disk tools and other hardware tools. one of those disks is hiren's boot cd.
try one and run some tests.

in the end, did you check the windows file system?

---

### Post by Sugi on 2010-01-01
If I install MS MBR, the windows partition works no problem.  Then if I install grub2, I can't see the windows partition, but I can see the linux partition.  I don't think it's a hardware issue, just some kind of weird software issue at this point.

Sugi

---

### Post by ranch hand on 2010-01-01
Then try making a MS entry for your Win JerryLewis Pro and put it in your /etc/grub.d/40_custom file.

It needs to be in this form;
```

echo "Adding PhatDebian on sda7" >&2 
cat << EOF
menuentry "PhatDebian on sda7" {
        set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 so quiet splash
        initrd /initrd.img
}
EOF

```Copy/paste that in there and then put your menu entry in place of the three lines between the { and the } leaving said brackets exactly where they are now.  It does not matter how many lines your entry is.  It is for MS, I haven't got a clue as to how long it is.

Above your menu entry there are 2 places with text beginning and ending with ".  You can replace that with any label that strikes your fancy.

Save the file.

Run;
```

sudo update-grub

```
This should do it.

EDIT

Have you, after booting to your Ubuntu, run from terminal there "sudo update-grub"?  There are a lot of times that when installing grub it will miss an MS OS and if you run the "sudo update-grub" command again, from your Ubuntu, it will pick it up.

---

### Post by falkaholic on 2010-01-04
I am having a similar problem. Windows only boots to a blinking cursor. 

I dd'ed my XP partition from my old set up. Not sure what is going on here but I am out of ideas. 


```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub.
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63. According to the info in the boot 
                       sector, sda5 has 102398246 sectors, but according to 
                       the info from fdisk, it has 195318207 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00072651

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     5,863,724     5,863,662  83 Linux
/dev/sda2           5,863,725 1,953,520,064 1,947,656,340   5 Extended
/dev/sda5           5,863,788   201,181,994   195,318,207   7 HPFS/NTFS
/dev/sda6         201,182,058   357,430,184   156,248,127  83 Linux
/dev/sda7         357,430,248   363,293,909     5,863,662  82 Linux swap / Solaris
/dev/sda8         363,293,973 1,953,520,064 1,590,226,092  83 Linux


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="ba4e773b-39e8-4d01-a1e1-6bef228818cc" TYPE="ext4" 
sda5: UUID="2844F72544F6F482" TYPE="ntfs" 
sda6: UUID="7be8778a-be0b-47df-8039-72810f3caf88" TYPE="ext4" 
sda7: UUID="7f94ff10-173a-466f-a94b-60d57455e957" TYPE="swap" 
sda8: UUID="1ad6f344-2b57-459b-b959-9f68c8533f5f" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda1 on /boot type ext4 (rw)
/dev/sda8 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/thecaptain4/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=thecaptain4)
/dev/sda5 on /media/2844F72544F6F482 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


============================= sda1/grub/grub.cfg: =============================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 7be8778a-be0b-47df-8039-72810f3caf88
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
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-16-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro  splash  quiet splash
	initrd	/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-16-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro single  splash
	initrd	/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-15-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro  splash  quiet splash
	initrd	/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-15-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro single  splash
	initrd	/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-14-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro  splash  quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-14-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro single  splash
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
menuentry "Windows NT/2000/XP (on /dev/sda5)" {
	insmod ntfs
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 2844f72544f6f482
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows xxxp" {
set root=(hd0,5)
chainloader +1
}

### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-14-generic
    .0GB: initrd.img-2.6.31-15-generic
    .0GB: initrd.img-2.6.31-16-generic
    .0GB: vmlinuz-2.6.31-14-generic
    .0GB: vmlinuz-2.6.31-15-generic
    .0GB: vmlinuz-2.6.31-16-generic

================================ sda5/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 7be8778a-be0b-47df-8039-72810f3caf88
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
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-16-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro  splash  quiet splash
	initrd	/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-16-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro single  splash
	initrd	/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-15-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro  splash  quiet splash
	initrd	/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-15-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro single  splash
	initrd	/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-14-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro  splash  quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-14-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro single  splash
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
menuentry "Windows NT/2000/XP (on /dev/sda5)" {
	insmod ntfs
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 2844f72544f6f482
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows xxxp" {
set root=(hd0,5)
chainloader +1
}

### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=7be8778a-be0b-47df-8039-72810f3caf88 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=ba4e773b-39e8-4d01-a1e1-6bef228818cc /boot           ext4    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=1ad6f344-2b57-459b-b959-9f68c8533f5f /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=7f94ff10-173a-466f-a94b-60d57455e957 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 103.0GB: boot/grub/core.img
 103.0GB: boot/grub/grub.cfg
 103.0GB: boot/initrd.img-2.6.31-14-generic
 103.0GB: boot/initrd.img-2.6.31-15-generic
 103.0GB: boot/initrd.img-2.6.31-16-generic
 103.0GB: boot/vmlinuz-2.6.31-14-generic
 103.0GB: boot/vmlinuz-2.6.31-15-generic
 103.0GB: boot/vmlinuz-2.6.31-16-generic
 103.0GB: initrd.img
 103.0GB: initrd.img.old
 103.0GB: vmlinuz
 103.0GB: vmlinuz.old
```

---

### Post by SecretCode on 2010-01-04
I'm pretty sure XP has problems booting from a logical partition. Can you repartition your disk and make space for a primary partition? (You'd only need to move a few hundred GB around ... :shock: )

---

### Post by falkaholic on 2010-01-04
> **SecretCode said:**
> I'm pretty sure XP has problems booting from a logical partition. Can you repartition your disk and make space for a primary partition? (You'd only need to move a few hundred GB around ... :shock: )

Correct me if I am wrong, but doenst GRUB 'trick' windows into thinking it's a primary partition?

I know about the complications of Windows and extended partitions; installing XP on extended doesnt work, thats why I dd'ed it. 

Win7 doesn't seem to like that partition either, not sure why (could be other hardware issues). 

This is a 1TB drive and I don't really have a place to back it up and I just did a reinstall and don't want to do it again :cool:

If I could move that one partition out of that extended block I would, but I don't that I can. Correct me if I am wrong.

---

### Post by meierfra. on 2010-01-04
> I'm pretty sure XP has problems booting from a logical partition.

Not really. It just needs to be configured right.

> According to the info in the boot sector, sda5 starts 
                       at sector 63. According to the info in the boot 
                       sector, sda5 has 102398246 sectors, but according to 
                       the info from fdisk, it has 195318207 sectors.
The numbers in the Boot parameter block of your XP partition are messed up.  To fix it, open a terminal in Ubuntu. Then

```
sudo apt-get install testdisk
sudo testdisk /dev/sda
```
Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows XP partition and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk.


You also need to update  the "boot.ini" file.

```
sudo mount /dev/sda5 /mnt
sudo nano /mnt/boot/ini
```

Edit the file so that it looks like


```
timeout=30

default=multi(0)disk(0)rdisk([COLOR="Red"]0[/COLOR])partition([COLOR="Red"]2[/COLOR])\WINDOWS

[operating systems]

multi(0)disk(0)rdisk([COLOR="Red"]0[/COLOR])partition([COLOR="Red"]2[/COLOR])\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin

```

Follow the instruction on the bottom of the terminal to save  the file. "^" means the "ctrl" key. ("nano" handles "dos"-style line breaks very well, so don't use a different editor)

Reboot and hope for the best.

---

### Post by falkaholic on 2010-01-04
meierfra you are a gentleman and a scholar!

that worked.

just now windows bluescreens on startup, but I bet that is some other issue.

thanks again!

---

### Post by meierfra. on 2010-01-04
> just now windows bluescreens on startup,

I was worried about that. Windows XP stores the "disk signature" of the hard drive in its registry. So if  you clone it to a different drive it gets confused.


Try this: Boot from your  Windows XP CD and press "R" to get to the repair console.
(Edit:  This won't work with the XP CD, Instead use one of the many  CD's  with regedit. For example: [UBCD,]("http://ubcd.sourceforge.net/") [Vista]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"), [Windows 7 ]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/"))
Type 
```
 regedit 
```
to open the Registry Editor.

Select "HKey_Local_Maschine" in the left panel.
Select  "Load Hive" in the "File" menu.

In the Pop Up Box, navigate to the  \Window\System32\config folder in your Windows Partition. 
Select the file "SYSTEM" and click open. 
In the new box type "MyHive" and hit enter.
Click on the "+"  signs next the "HKey_Local_Maschine"". 
You should now have an entry  named "MyHive in the left panel.
Click on  the "+" sign next to "MyHive".
RightClick "MountedDevices"  and choose "Delete".
Select   "MyHive". 
Select "Unload Hive" in the "File" menu.

Reboot.  XP should automatically regenerate the "mounted device" registry.

---

### Post by SecretCode on 2010-01-04
nm!

---

### Post by falkaholic on 2010-01-05
Wow, how do you know all this? I searched the interwebs high and low. You must have super powers. 

I wonder why this doesnt happen with everyday imaging?

Anyway, the repair console doesn't see that partition. My guess is because its extended. I think I am outta luck...

---

### Post by meierfra. on 2010-01-05
You should be able to edit the registry with [ UBCD]("http://ubcd.sourceforge.net/"), but it might be better to   convert your Windows partition to a primary partition:

Boot into a Ubuntu and download the attach file PT.txt to your desktop. Rewrite the partition table with
```

cd ~/Desktop
sudo sfdisk --no-reread -f /dev/sda -O PT.save < PT.txt
```
For emergency purposes, save the file PT.save somewhere outside your hard drives (flash drive, online storage,...)

Reboot into Ubuntu and run:

```
sudo update-grub
```

Reboot again and see whether you can boot into XP. Probably not, but your Windows CD should now detect your XP.

---

### Post by falkaholic on 2010-01-06
Wow, are you some sort of high-power super mutant, never even considered for mass production? Thats some serious partition-fu!

It worked. Couldn't rescue my windows install but I was able to reinstall (put win7 on) since it is now a primary partition.

Couple issues:
1. After reinstalling grub, ubuntu stopped during boot and made me run a manual fsck which fixed 7 errors. Dont think that is a big deal.

2. there bigger deal is that  Windows Setup, fdisk, and Palimpsest see the partition table (kinda), but Gparted sees my HD as 1TB chunk. All my files and partitions are accessible, but the PT isn't work. I [see]("http://ubuntuforums.org/showthread.php?t=1192598") there is ways to fix this. I am not sure, I think I am still out of my league with this stuff. Look a the PT here, I have a million bypte partition all of a sudden!

```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub.
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00072651

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     5,863,724     5,863,662  83 Linux
/dev/sda2    *      5,863,788   201,181,994   195,318,207   7 HPFS/NTFS
/dev/sda3         201,182,995 1,953,520,064 1,752,337,070   5 Extended
Invalid MBR Signature found
Empty Partition
/dev/sda5         201,182,995 1,791,348,498 1,590,165,504   0 Empty
/dev/sda4         201,182,058   357,430,184   156,248,127  83 Linux

/dev/sda3 overlaps with /dev/sda4
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda3
/dev/sda5 overlaps with /dev/sda4

blkid -c /dev/null: ____________________________________________________________

sda1: UUID="ba4e773b-39e8-4d01-a1e1-6bef228818cc" TYPE="ext4" 
sda2: UUID="0AB443C0B443ACCF" TYPE="ntfs" 
sda5: UUID="7f94ff10-173a-466f-a94b-60d57455e957" TYPE="swap" 
sda4: UUID="7be8778a-be0b-47df-8039-72810f3caf88" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda1 on /boot type ext4 (rw)
/dev/sda6 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/thecaptain4/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=thecaptain4)


============================= sda1/grub/grub.cfg: =============================

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
set root=(hd0,4)
search --no-floppy --fs-uuid --set 7be8778a-be0b-47df-8039-72810f3caf88
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
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-16-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro  splash  quiet splash
	initrd	/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-16-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro single  splash
	initrd	/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-15-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro  splash  quiet splash
	initrd	/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-15-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro single  splash
	initrd	/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-14-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro  splash  quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-14-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro single  splash
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
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 2844f72544f6f482
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows xxxp" {
set root=(hd0,5)
chainloader +1
}

### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-14-generic
    .0GB: initrd.img-2.6.31-15-generic
    .0GB: initrd.img-2.6.31-16-generic
    .0GB: vmlinuz-2.6.31-14-generic
    .0GB: vmlinuz-2.6.31-15-generic
    .0GB: vmlinuz-2.6.31-16-generic

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root=(hd0,4)
search --no-floppy --fs-uuid --set 7be8778a-be0b-47df-8039-72810f3caf88
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
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-16-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro  splash  quiet splash
	initrd	/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-16-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro single  splash
	initrd	/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-15-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro  splash  quiet splash
	initrd	/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-15-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro single  splash
	initrd	/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-14-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro  splash  quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ba4e773b-39e8-4d01-a1e1-6bef228818cc
	linux	/vmlinuz-2.6.31-14-generic root=UUID=7be8778a-be0b-47df-8039-72810f3caf88 ro single  splash
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
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 2844f72544f6f482
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows xxxp" {
set root=(hd0,5)
chainloader +1
}

### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=7be8778a-be0b-47df-8039-72810f3caf88 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=ba4e773b-39e8-4d01-a1e1-6bef228818cc /boot           ext4    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=1ad6f344-2b57-459b-b959-9f68c8533f5f /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=7f94ff10-173a-466f-a94b-60d57455e957 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


 103.0GB: boot/grub/core.img
 103.0GB: boot/grub/grub.cfg
 103.0GB: boot/initrd.img-2.6.31-14-generic
 103.0GB: boot/initrd.img-2.6.31-15-generic
 103.0GB: boot/initrd.img-2.6.31-16-generic
 103.0GB: boot/vmlinuz-2.6.31-14-generic
 103.0GB: boot/vmlinuz-2.6.31-15-generic
 103.0GB: boot/vmlinuz-2.6.31-16-generic
 103.0GB: initrd.img
 103.0GB: initrd.img.old
 103.0GB: vmlinuz
 103.0GB: vmlinuz.old

```

---

### Post by meierfra. on 2010-01-06
> 1. After reinstalling grub, ubuntu stopped during boot and made me run a manual fsck which fixed 7 errors. Dont think that is a big deal.

2. there bigger deal is that Windows Setup, fdisk, and Palimpsest see the partition table (kinda), but Gparted sees my HD as 1TB chunk.


I'm deeply sorry. Both of those problems have been caused by a mistake in the file PT.txt, I had prepared for you.  Hopefully fsck took care of the first problem. For the second problem, download the attached file PT.txt and repeat the procedure from my previous post.  (I triple checked the file)

---

### Post by falkaholic on 2010-01-07
No need to be sorry, but I do have to critisize you triple checking skills. There was a syntax error in the lastest PT ("size- 0" not "size= 0") :P

Looks like I am up a running. Thanks. I learned alot of partitioning doing this one. I'll buy you a drink if we cross paths one day.

---

### Post by meierfra. on 2010-01-07
> There was a syntax error in the lastest PT ("size- 0" not "size= 0") 
Glad you caught that. I read  through that file two more times after I had posted it and never  noticed that. I guess I was to busy making sure that all the numbers were right and the file  had no extra spaces. (sfdisk  is very picky)  
> I learned alot 
Me too. I did some experimenting on my VirtualBox machine and have gotten pretty good in cloning XP to a logical partition and booting it:

Step 1 Use "regedit" to remove the "mounted device" registry before cloning.  (Much easier than afterwards: No need to find a CD with regedit, not need to load a hive. Just run "regedit"  and delete "mounted devices" under the "Key_Local_Maschine->System" )

Step 2  Clone XP with your favorite tool (I used "gparted" and "dd", both work just fine.)

Step 3 Run testdisk "RebuildBS" on the cloned partition.

That's it (well, maybe throw in a "chkdsk" for good measure.)


> Looks like I am up a running. 
Great.  Have fun with Window 7 and XP. 

> I'll buy you a drink if we cross paths one day. 
That should improve my triple checking skills.

---

### Post by Sugi on 2010-01-11
> **Thread Hijack**
[thred][hahy-jak] 
Taking over a thread on a message board by taking a part of the original posted topic, twisting it around and "hijacking" the thread itself. What happens is that the original content contained in the post becomes moot and whatever the "Thread Jacker" has manipulated the content to be becomes the new content thereby "hijacking" the original intent of post. People now respond to the "thread jacker's" input and the that becomes the focus of the tread.
[http://www.urbandictionary.com/define.php?term=thread+hijacking]("http://www.urbandictionary.com/define.php?term=thread+hijacking")
[IMG]http://i216.photobucket.com/albums/cc289/EricBlair_photos/Hijack-In_progress.jpg[/IMG]



HAHHA, I am just kidding.  I even got something out of that cloning xp.


Sugi

---

