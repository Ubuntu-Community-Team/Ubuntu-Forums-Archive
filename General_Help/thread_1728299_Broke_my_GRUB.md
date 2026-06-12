---
title: "Broke my GRUB"
date: 2011-04-13
forum: General Help
---

### Post by kai_kan on 2011-04-13
In an effort to build an Ubuntu boot thumb drive for a friend's misbehaving Mac, I seem to have inadvertently replaced my own GRUB with a bad one (D'Oh!). After a couple days of trying various tips I've found online, I'm hoping someone here can help me avoid a re-install. 

Here's what I know:

My system was a Win7/Ubuntu10.10 dual-boot, 64-bit. Currently I seem to be booting into GRUB2, which scrolls through a list of commands before leaving me with an introduction and a grub> prompt (no boot menu). The only way I've been able to boot is to my Ubuntu CD.

Help?

---

### Post by earthpigg on 2011-04-13
hi,

The recovery procedure outlined [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") should work for you. Any other guide for "reinstalling grub from ubuntu livecd" that includes provisions for a dual boot setup should work, too, if you don't like the formatting or verbosity of the one i linked.

---

### Post by kai_kan on 2011-04-13
> **earthpigg said:**
> hi,

The recovery procedure outlined [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") should work for you. Any other guide for "reinstalling grub from ubuntu livecd" that includes provisions for a dual boot setup should work, too, if you don't like the formatting or verbosity of the one i linked.

Thanks for the reply!

I had found and tried this link previously, but to no avail. Tried it again now, in case I missed something, and here's what I found:

1st difference was that there are many more files in my /boot directory, but they appear to just be various older versions of linux, presumably for backup.

Next, when I ran the following command:
```
sudo grub-install --root-directory=/media/ff2blah-blah-blah /dev/sda
```

I only received:
```
Installation finished. No error reported.

```

in reply... there's nothing about a device map, as they suggest there should be.

I rebooted, and nothing's changed.

More ideas please?

---

### Post by danjahner on 2011-04-13
The install command you listed looks correct, assuming you mounted the Ubuntu root partition to the location referenced by --root-directory. Try the install again, then run: 

```

sudo update-grub

```

What does that output?

---

### Post by drs305 on 2011-04-13
It should work after running "update-grub". If not, from the LiveCD please download and run the boot info script and post the contents of RESULTS.txt. It will give us a good indication of your boot setup. Post the contents within 'code' tags, which you can generate while creating the post by pressing the # icon.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by earthpigg on 2011-04-13
EDIT: look at drs305 and danjahner's posts and work with that approach before using the slightly more drastic approach I bring up below. Only resort to the below as a second-to-last resort. original post continues...

well, crap. 

the chroot method is a pain in the butt, but worth a shot.

i don't think there is any specific ubuntu documentation for this, but this looks like it will function identically (most of the time for low level stuff like this, linux is linux and grub2 is grub2):

[http://wiki.sabayon.org/index.php?title=HOWTO:_Restore_Grub2](http://wiki.sabayon.org/index.php?title=HOWTO:_Restore_Grub2)

skip to "completely reinstall and reconfigure"

i don't recall exactly what guide i used last time i had to do this, but i know it wasn't for ubuntu but still worked fine for me - and the guide linked above certainly looks familiar.

---

### Post by drs305 on 2011-04-13
Here is a link to my chroot procedure for purging/reinstalling, but looking at the boot info script results could be more productive.

[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by kai_kan on 2011-04-13
> **danjahner said:**
> The install command you listed looks correct, assuming you mounted the Ubuntu root partition to the location referenced by --root-directory. Try the install again, then run: 

```

sudo update-grub

```

What does that output?

Re-did the install, then update. That returned:

```
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

```

---

### Post by kai_kan on 2011-04-13
> **drs305 said:**
> It should work after running "update-grub". If not, from the LiveCD please download and run the boot info script and post the contents of RESULTS.txt. It will give us a good indication of your boot setup. Post the contents within 'code' tags, which you can generate while creating the post by pressing the # icon.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Thanks for this! Here's the result of the script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       321,299       321,237  de Dell Utility
/dev/sda2             321,536    20,477,951    20,156,416   7 HPFS/NTFS
/dev/sda3          20,477,952   511,997,951   491,520,000   7 HPFS/NTFS
/dev/sda4         512,007,615   976,768,064   464,760,450   5 Extended
/dev/sda5         512,007,678   957,843,494   445,835,817  83 Linux
/dev/sda6         957,843,558   976,768,064    18,924,507  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07DA-0318                              vfat       DellUtility                   
/dev/sda2        00ACEE14ACEE03CE                       ntfs       RECOVERY                      
/dev/sda3        22DEF13FDEF10BB3                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f21b44ec-b83b-4a37-9cde-ff1e837cc06b   ext4                                     
/dev/sda6        54344a14-9678-4ccc-bcda-cbec70bfa6f8   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/f21b44ec-b83b-4a37-9cde-ff1e837cc06b ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda5/boot/grub/grub.cfg: ===========================

#! /bin/sh
set -e

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
export TEXTDOMAINDIR=${prefix}/share/locale

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
    || uses_abstraction "${GRUB_DEVICE}" lvm; then
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

  # Use ELILO's generic "efifb" when it's known to be available.
  # FIXME: We need an interface to select vesafb in case efifb can't be used.
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
    echo    '$(printf "$(gettext_quoted "Loading Linux %s ...")" ${version})'
EOF
  fi
  cat << EOF
    linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
    echo    '$(gettext_quoted "Loading initial ramdisk ...")'
EOF
  fi
  if test -n "${initrd}" ; then
    cat << EOF
    initrd    ${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

list=`for i in /boot/vmlinu[zx]-* /vmlinu[zx]-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
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
       "initrd-${version}" "initramfs-${version}.img" \
       "initrd.img-${alt_version}" "initrd-${alt_version}.img" \
       "initrd-${alt_version}" "initramfs-${alt_version}.img"; do
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
UUID=f21b44ec-b83b-4a37-9cde-ff1e837cc06b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=54344a14-9678-4ccc-bcda-cbec70bfa6f8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 262.3GB: boot/grub/core.img
 277.9GB: boot/grub/grub.cfg
 263.2GB: boot/initrd.img-2.6.31-21-generic
 380.0GB: boot/initrd.img-2.6.35-22-generic
 391.9GB: boot/initrd.img-2.6.35-23-generic
 392.7GB: boot/initrd.img-2.6.35-24-generic
 316.8GB: boot/initrd.img-2.6.35-25-generic
 391.0GB: boot/initrd.img-2.6.35-27-generic
 416.1GB: boot/initrd.img-2.6.35-28-generic
 262.8GB: boot/vmlinuz-2.6.31-21-generic
 267.0GB: boot/vmlinuz-2.6.35-22-generic
 311.6GB: boot/vmlinuz-2.6.35-23-generic
 270.3GB: boot/vmlinuz-2.6.35-24-generic
 305.1GB: boot/vmlinuz-2.6.35-25-generic
 266.5GB: boot/vmlinuz-2.6.35-27-generic
 415.9GB: boot/vmlinuz-2.6.35-28-generic
 416.1GB: initrd.img
 391.0GB: initrd.img.old
 415.9GB: vmlinuz
 266.5GB: vmlinuz.old
```

---

### Post by drs305 on 2011-04-13
The grub.cfg file appears to have been replaced by the contents of the grub-mkconfig script. 

Since I have no idea how that got into your grub.cfg file, I'd suggest purging/reinstalling Grub2 (grub-pc).

You can do this on the LiveCD via the chroot procedure I linked in my earlier post. You will mount your real Ubuntu partition, copy some system files, chroot into that partition, ensure you have an Internet connection, and then remove and install Grub2. 

If you follow the instructions I'm fairly certain your system will be restored. If you have questions just ask here or in the 'chroot' thread.

---

### Post by kai_kan on 2011-04-13
> **drs305 said:**
> The grub.cfg file appears to have been replaced by the contents of the grub-mkconfig script. 

Since I have no idea how that got into your grub.cfg file, I'd suggest purging/reinstalling Grub2 (grub-pc).

You can do this on the LiveCD via the chroot procedure I linked in my earlier post. You will mount your real Ubuntu partition, copy some system files, chroot into that partition, ensure you have an Internet connection, and then remove and install Grub2. 

If you follow the instructions I'm fairly certain your system will be restored. If you have questions just ask here or in the 'chroot' thread.

I know exactly how that got in my grub file... I did it :oops: . This mess started with me accidentally substituting the grub.cfg file with one meant for a usb key, pointing to an iso image. In search of a working grub, I swapped this in, clearly a mistake.

Off to try chroot ... will keep you posted.

Thanks again!

---

### Post by drs305 on 2011-04-13
> **kai_kan said:**
> I know exactly how that got in my grub file... I did it :oops: . This mess started with me accidentally substituting the grub.cfg file with one meant for a usb key, pointing to an iso image. In search of a working grub, I swapped this in, clearly a mistake.

Off to try chroot ... will keep you posted.

Thanks again!

Since you know what caused it, your grub configuration-generating files may still be ok. You could try this first from the LiveCD if you are still around:
```
sudo mount /dev/sda5 /mnt
sudo grub-mkconfig -o /mnt/boot/grub/grub.cfg
```

---

### Post by kai_kan on 2011-04-13
> **drs305 said:**
> Since you know what caused it, your grub configuration-generating files may still be ok. You could try this first from the LiveCD if you are still around:
```
sudo mount /dev/sda5 /mnt
sudo grub-mkconfig -o /mnt/boot/grub/grub.cfg
```

WAHOO! :D

The purge/reinstall worked. Perhaps the above would have as well, but I was already halfway through the other and didn't try this. 

Thanks to everyone for their efforts, and especially drs305 for the solution. Thrilled to have my lappie back!

---

