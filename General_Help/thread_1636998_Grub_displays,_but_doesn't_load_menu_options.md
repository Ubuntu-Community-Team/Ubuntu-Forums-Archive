---
title: "Grub displays, but doesn't load menu options"
date: 2010-12-03
forum: General Help
---

### Post by lcdrovers on 2010-12-03
Hello, this problem just started an hour ago, and I think I might know what could be wrong, but I'm completely unsure, so I'd really appreciate some help. I am using Ubuntu 10.10, manually installed, on a Dell Studio 15 laptop, dual booting with Windows 7.

While a few kids were playing nearby where I was working, one of the pillows they were playing with hit my laptop's screen and moved the screen's hinge backwards, applying pressure past where the hinge ends. This didn't seem to cause any physical harm to the computer, but I moved away from where they were playing, and in the process, shut the laptop, putting it into sleep mode. I opened the laptop and entered my password to unlock it. About half a second after entering my password and displaying the desktop and open windows, it brought up the password prompt again, as if I'd just opened my laptop up and removed it from standby, although I had not in fact touched it since I had entered my password a mere half second before. I thought that that was strange, and then attempted to continue my work. However, although the mouse worked fine, when I attempted to apply a keyboard shortcut (Ctrl+Alt+2, which runs a 2-finger scroll script and has to be run every time I take the computer out of standby), Ubuntu didn't register it (I didn't touch the keyboard otherwise, although I should have checked whether it worked all =\). I tried it again, and it still did not apply the script. Then I thought, "Oh, the pillow must have knocked something out of whack. I'll restart." When I restarted, grub loaded as usual, but the timeout ("loading the primary in Xs." sort of thing) that it usually displays did not display this time. I didn't notice it at the time; I selected Ubuntu, and it appeared to be loading it, removing the grub menu, but then hung. I waited 5 minutes for the computer to display the login screen, but it did not, so I restarted again, thinking that it might just be something stupid. It didn't work again, hanging again. I tried this with both the most recent linux kernel and the second most recent kernel, neither of which worked. But what was interesting is that Windows 7, which is also on the grub menu, loaded and displayed perfectly, as did GRUB Invaders, a game that can be loaded directly from grub.

After this little escapade, I thought something was just wrong in grub.cfg, and it somehow wasn't mapping the Ubuntu menu entries to the appropriate OS and kernel. So I loaded up a live CD, and attempted to look at the linux entries. These are the menu entries 10_linux, 00_header, and 20_linux_xen.

10_linux:
```
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
```00_header
```
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

transform="s,x,x,"

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
locale_dir=`echo ${GRUB_PREFIX}/locale | sed ${transform}`
grub_lang=`echo $LANG | cut -d _ -f 1`

. ${libdir}/grub/grub-mkconfig_lib

# Do this as early as possible, since other commands might depend on it.
# (e.g. the `loadfont' command might need lvm or raid modules)
for i in ${GRUB_PRELOAD_MODULES} ; do
  echo "insmod $i"
done

if [ "x${GRUB_DEFAULT}" = "x" ] ; then GRUB_DEFAULT=0 ; fi
if [ "x${GRUB_DEFAULT}" = "xsaved" ] ; then GRUB_DEFAULT='${saved_entry}' ; fi
if [ "x${GRUB_TIMEOUT}" = "x" ] ; then GRUB_TIMEOUT=5 ; fi
if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=640x480 ; fi

if [ "x${GRUB_DEFAULT_BUTTON}" = "x" ] ; then GRUB_DEFAULT_BUTTON="$GRUB_DEFAULT" ; fi
if [ "x${GRUB_DEFAULT_BUTTON}" = "xsaved" ] ; then GRUB_DEFAULT_BUTTON='${saved_entry}' ; fi
if [ "x${GRUB_TIMEOUT_BUTTON}" = "x" ] ; then GRUB_TIMEOUT_BUTTON="$GRUB_TIMEOUT" ; fi

cat << EOF
if [ -s \$prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
EOF
if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
   set default="${GRUB_DEFAULT_BUTTON}"
else
   set default="${GRUB_DEFAULT}"
fi
EOF
else
    cat <<EOF
set default="${GRUB_DEFAULT}"
EOF
fi
cat <<EOF
if [ "\${prev_saved_entry}" ]; then
  set saved_entry="\${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "\${boot_once}" ]; then
    saved_entry="\${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "\${have_grubenv}" ]; then if [ -z "\${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
EOF
if [ -n "${GRUB_VIDEO_BACKEND}" ]; then
    cat <<EOF
  insmod ${GRUB_VIDEO_BACKEND}
EOF
else
    # Insert all available backends; GRUB will use the most appropriate.
    for backend in $(cat "${GRUB_PREFIX}/video.lst"); do
    # video_bochs and video_cirrus require probing PCI space, and some
    # machines don't seem to like this.  These are generally
    # non-essential at least for i386-pc, so disable them as a
    # short-term fix for Ubuntu 10.10.
    case "${backend}" in
        video_bochs|video_cirrus)
        cpu="$(uname -m)"
        case "${cpu}" in
            i[3456]86|x86_64)
            [ -d /sys/firmware/efi ] || continue
            ;;
        esac
        ;;
    esac
    cat <<EOF
  insmod ${backend}
EOF
    done
fi
cat <<EOF
}

EOF

serial=0;
gfxterm=0;
for x in ${GRUB_TERMINAL_INPUT} ${GRUB_TERMINAL_OUTPUT}; do
    if [ xserial = "x$x" ]; then
    serial=1;
    fi
    if [ xgfxterm = "x$x" ]; then
    gfxterm=1;
    fi
done

if [ "x$serial" = x1 ]; then
    if ! test -e ${GRUB_PREFIX}/serial.mod ; then
    echo "Serial terminal not available on this platform." >&2 ; exit 1
    fi

    if [ "x${GRUB_SERIAL_COMMAND}" = "x" ] ; then
    grub_warn "Requested serial terminal but GRUB_SERIAL_COMMAND is unspecified. Default parameters will be used."
    GRUB_SERIAL_COMMAND=serial
    fi
    echo "${GRUB_SERIAL_COMMAND}"
fi

if [ "x$gfxterm" = x1 ]; then
    # Make the font accessible
    prepare_grub_to_access_device `${grub_probe} --target=device "${GRUB_FONT_PATH}"`

    cat << EOF
if loadfont `make_system_path_relative_to_its_root "${GRUB_FONT_PATH}"` ; then
  set gfxmode=${GRUB_GFXMODE}
  load_video
  insmod gfxterm
fi
EOF
fi

case x${GRUB_TERMINAL_INPUT} in
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
terminal_input ${GRUB_TERMINAL_INPUT}
EOF
  ;;
esac

case x${GRUB_TERMINAL_OUTPUT} in
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
terminal_output ${GRUB_TERMINAL_OUTPUT}
EOF
  ;;
esac

if [ "x$gfxterm" = x1 ]; then
    if [ "x$GRUB_THEME" != x ] && [ -f "$GRUB_THEME" ] \
    && is_path_readable_by_grub "$GRUB_THEME"; then
    echo "Found theme: $GRUB_THEME" >&2
    prepare_grub_to_access_device `${grub_probe} --target=device "$GRUB_THEME"`
    cat << EOF
insmod gfxmenu
EOF
    themedir="`dirname "$GRUB_THEME"`"
    for x in "$themedir"/*.pf2 "$themedir"/f/*.pf2; do
        if [ -f "$x" ]; then
        cat << EOF
loadfont (\$root)`make_system_path_relative_to_its_root $x`
EOF
        fi
    done
    if [ x"`echo "$themedir"/*.jpg`" != x"$themedir/*.jpg" ] || [ x"`echo "$themedir"/*.jpeg`" != x"$themedir/*.jpeg" ]; then
        cat << EOF
insmod jpeg
EOF
    fi
    if [ x"`echo "$themedir"/*.png`" != x"$themedir/*.png" ]; then
        cat << EOF
insmod png
EOF
    fi
    if [ x"`echo "$themedir"/*.tga`" != x"$themedir/*.tga" ]; then
        cat << EOF
insmod tga
EOF
    fi
        
    cat << EOF
set theme=(\$root)`make_system_path_relative_to_its_root $GRUB_THEME`
EOF
    elif [ "x$GRUB_BACKGROUND" != x ] && [ -f "$GRUB_BACKGROUND" ] \
        && is_path_readable_by_grub "$GRUB_BACKGROUND"; then
    echo "Found background: $GRUB_BACKGROUND" >&2
    case "$GRUB_BACKGROUND" in 
        *.png)         reader=png ;;
        *.tga)         reader=tga ;;
        *.jpg|*.jpeg)  reader=jpeg ;;
        *)             echo "Unsupported image format" >&2; exit 1 ;;
    esac
    prepare_grub_to_access_device `${grub_probe} --target=device "$GRUB_BACKGROUND"`
    cat << EOF
insmod $reader
background_image -m stretch `make_system_path_relative_to_its_root "$GRUB_BACKGROUND"`
EOF
    fi
fi

# Gettext variables and module
if [ "x${LANG}" != "xC" ] && [ -d "${locale_dir}" ] ; then
    prepare_grub_to_access_device $(${grub_probe} --target=device ${locale_dir})
  cat << EOF
set locale_dir=(\$root)$(make_system_path_relative_to_its_root ${locale_dir})
set lang=${grub_lang}
insmod gettext
EOF
fi

make_timeout ()
{
    cat << EOF
if [ "\${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=${2}
fi
EOF
}

if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
EOF
make_timeout "${GRUB_HIDDEN_TIMEOUT_BUTTON}" "${GRUB_TIMEOUT_BUTTON}"
echo else
make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
echo fi
else
make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
fi

# Play an initial tune
if [ "x${GRUB_INIT_TUNE}" != "x" ] ; then
  echo "play ${GRUB_INIT_TUNE}"
fi

if [ "x${GRUB_BADRAM}" != "x" ] ; then
  echo "badram ${GRUB_BADRAM}"
fi
```20_linux_xen
```
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

CLASS="--class gnu-linux --class gnu --class os --class xen"

if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
  OS=GNU/Linux
else
  OS="${GRUB_DISTRIBUTOR} GNU/Linux"
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

linux_entry ()
{
  os="$1"
  version="$2"
  xen_version="$3"
  recovery="$4"
  args="$5"
  xen_args="$6"
  if ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s and XEN %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s, with Linux %s and XEN %s")"
  fi
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}" "${xen_version}"
  save_default_entry | sed -e "s/^/\t/"

  if [ -z "${prepare_boot_cache}" ]; then
    prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
  fi
  printf '%s\n' "${prepare_boot_cache}"
  cat << EOF
    echo    '$(printf "$(gettext_quoted "Loading Linux %s ...")" ${version})'
    multiboot    ${rel_xen_dirname}/${xen_basename} placeholder ${xen_args}
    module    ${rel_dirname}/${basename} placeholder root=${linux_root_device_thisversion} ro ${args}
EOF
  if test -n "${initrd}" ; then
    cat << EOF
    echo    '$(gettext_quoted "Loading initial ramdisk ...")'
    module    ${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

linux_list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
        basename=$(basename $i)
    version=$(echo $basename | sed -e "s,^[^0-9]*-,,g")
        if grub_file_is_not_garbage "$i" && grep -qx "CONFIG_XEN_DOM0=y" /boot/config-${version} 2> /dev/null ; then echo -n "$i " ; fi
      done`
xen_list=`for i in /boot/xen*; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`
prepare_boot_cache=

while [ "x${xen_list}" != "x" ] ; do
    list="${linux_list}"
    current_xen=`version_find_latest $xen_list`
    xen_basename=`basename ${current_xen}`
    xen_dirname=`dirname ${current_xen}`
    rel_xen_dirname=`make_system_path_relative_to_its_root $xen_dirname`
    xen_version=`echo $xen_basename | sed -e "s,.gz$,,g;s,^xen-,,g"`
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

    linux_entry "${OS}" "${version}" "${xen_version}" false \
        "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_LINUX_DEFAULT}" "${GRUB_CMDLINE_XEN} ${GRUB_CMDLINE_XEN_DEFAULT}"
    if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
        linux_entry "${OS}" "${version}" "${xen_version}" true \
        "single ${GRUB_CMDLINE_LINUX}" "${GRUB_CMDLINE_XEN}"
    fi

    list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
    done
    xen_list=`echo $xen_list | tr ' ' '\n' | grep -vx $current_xen | tr '\n' ' '`
done
```Some of the information I gave (a lot) is probably useless, but I provided it because I didn't know whether it was important or not. If I need to provide any more information, please tell me and I will provide it promptly. I'd really appreciate any help anyone could give me on this. Thanks in advance. :o

---

### Post by lcdrovers on 2010-12-05
This is a few pages past where anyone might reasonably see and respond to it, so I'd like to bump this topic, as it remains unsolved.

---

### Post by lcdrovers on 2010-12-05
Ummm, bump again? I don't see how this could be go without a response for so long. I'd really appreciate any help, even if you're not absolutely sure about the answer.

---

### Post by lcdrovers on 2010-12-05
By the way, this is the output from the boot info script that seems to have helped so many others:

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
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

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

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325    30,800,324    30,720,000   7 HPFS/NTFS
/dev/sda3          30,800,325   780,312,987   749,512,663   7 HPFS/NTFS
/dev/sda4         780,314,622   976,773,119   196,458,498   5 Extended
/dev/sda5         780,314,624   968,691,711   188,377,088  83 Linux
/dev/sda6         968,693,760   976,773,119     8,079,360  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        08B84376B84360F4                       ntfs       RECOVERY                      
/dev/sda3        00B8457CB8457168                       ntfs       The Awesome Drive             
/dev/sda4: PTTYPE="dos" 
/dev/sda5        0b727857-88b1-4489-a0ab-f82415a593a8   ext4                                     
/dev/sda6        c36e6bdd-3128-44f5-978e-6b8a07b0a271   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 0b727857-88b1-4489-a0ab-f82415a593a8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 0b727857-88b1-4489-a0ab-f82415a593a8
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 0b727857-88b1-4489-a0ab-f82415a593a8
insmod jpeg
if background_image /usr/share/images/grub/breloom-fractalius.jpg ; then
  set color_normal=green/black
  set color_highlight=red/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 0b727857-88b1-4489-a0ab-f82415a593a8
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=0b727857-88b1-4489-a0ab-f82415a593a8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 0b727857-88b1-4489-a0ab-f82415a593a8
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0b727857-88b1-4489-a0ab-f82415a593a8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows_7" {
set root=(hd0,2)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/22_invaders ###
menuentry "GRUB Invaders" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 0b727857-88b1-4489-a0ab-f82415a593a8
    multiboot    /boot/invaders.exec
}
### END /etc/grub.d/22_invaders ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=0b727857-88b1-4489-a0ab-f82415a593a8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c36e6bdd-3128-44f5-978e-6b8a07b0a271 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 449.0GB: boot/grub/core.img
 434.8GB: boot/grub/grub.cfg
 429.0GB: boot/initrd.img-2.6.35-22-generic
 431.3GB: boot/initrd.img-2.6.35-23-generic
 449.4GB: boot/vmlinuz-2.6.35-22-generic
 449.5GB: boot/vmlinuz-2.6.35-23-generic
 431.3GB: initrd.img
 429.0GB: initrd.img.old
 449.5GB: vmlinuz
 449.4GB: vmlinuz.old
```

---

### Post by ronparent on 2010-12-05
Have you tried a grub 2 reinstall from a live cd? It is quick and easy and might sort out your problem.

[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

---

### Post by lcdrovers on 2010-12-05
> **ronparent said:**
> Have you tried a grub 2 reinstall from a live cd? It is quick and easy and might sort out your problem.

[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

I feel so stupid asking this, but it's giving me an error when running sudo update-grub "/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted)"

How do I do this?

---

### Post by lcdrovers on 2010-12-05
> **lcdrovers said:**
> I feel so stupid asking this, but it's giving me an error when running sudo update-grub "/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted)"

How do I do this?

This should be a simple answer, but in the event that it's not, could someone just post something to at least alert me to the fact that something important is happening?

Also, now when I turn on my computer, having reinstalled grub but not having run sudo update-grub, the computer boots to GRUB, but doesn't show the GRUB menu, just a blank screen.

---

### Post by ronparent on 2010-12-05
I mean a full grub reinstall. From a 10.10 live cd mount your 10.10 file system:
```
sudo mount /dev/sda5 /mnt
```

And then the grub reinstall:
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

This should get you a clean grub reinstall. Let us know if it works.:D

---

### Post by QLee on 2010-12-06
[QUOTE=lcdrovers]This should be a simple answer, but in the event that it's not, could someone just post something to at least alert me to the fact that something important is happening?
...[/QUOTE]

OS prober isn't finding your Ubuntu partition.

[QUOTE=lcdrovers]While a few kids were playing nearby where I was working, one of the  pillows they were playing with hit my laptop's screen and moved the  screen's hinge backwards, applying pressure past where the hinge ends.[/QUOTE]

If this happened to my laptop, I would suspect that the pillow caused the case (keyboard section) to pivot at the hinge and "bounce" the case while the disk was spinning (possibly even writing), so i would probably suspect a chance that there was some corruption to the partition (maybe fixable, maybe not).
Then, while booted to the live CD, I would probably run fsck on the unmounted partition, in your case /dev/sda5. Seems to be a reasonable guess, at least it's simple.

---

### Post by ronparent on 2010-12-06
I do agree with Qlee.

---

### Post by lcdrovers on 2010-12-06
> **QLee said:**
> OS prober isn't finding your Ubuntu partition.



If this happened to my laptop, I would suspect that the pillow caused the case (keyboard section) to pivot at the hinge and "bounce" the case while the disk was spinning (possibly even writing), so i would probably suspect a chance that there was some corruption to the partition (maybe fixable, maybe not).
Then, while booted to the live CD, I would probably run fsck on the unmounted partition, in your case /dev/sda5. Seems to be a reasonable guess, at least it's simple.

I've run fsck on /dev/sda5, and it said this:
```
ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda5 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
```

Then it spits out:
```
Error reading block 524347 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore Error<y>?
```

I then pressed y, to see what would happen. It returned:
```
Force rewrite<y>?
```

I pressed y again, and then it gave the same error message as before, but for block 524348. Does this mean I should just backup the files I need and get a new hard drive? Or is there a chance that it can be saved?

---

### Post by oldfred on 2010-12-06
I think you need to run the second command, the -y parameter you auto answer the yes so it continues.

From liveCD so everything is unmounted, change sdb1 to your partition(s)
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

Your boot info script also showed a problem in the windows boot partition. Grub may not be finding windows because of it and windows will not boot. If you do not have a second system, grub bypasses the menu and just boots Ubuntu. You can hold shift key from BIOS until menu appears to get menu.

From sda2:
   Boot files/dirs:   /bootmgr /Boot/BCD [COLOR=Red]/boot/grub/core.img[/COLOR]

You have a grub /boot and a windows /Boot and in windows capitals and small letters are the same, so windows will not work.
You need to delete the /boot but [COLOR=Red]not[/COLOR] the /Boot folder.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

### Post by lcdrovers on 2010-12-06
> **oldfred said:**
> I think you need to run the second command, the -y parameter you auto answer the yes so it continues.

From liveCD so everything is unmounted, change sdb1 to your partition(s)
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

Your boot info script also showed a problem in the windows boot partition. Grub may not be finding windows because of it and windows will not boot. If you do not have a second system, grub bypasses the menu and just boots Ubuntu. You can hold shift key from BIOS until menu appears to get menu.

From sda2:
   Boot files/dirs:   /bootmgr /Boot/BCD [COLOR=Red]/boot/grub/core.img[/COLOR]

You have a grub /boot and a windows /Boot and in windows capitals and small letters are the same, so windows will not work.
You need to delete the /boot but [COLOR=Red]not[/COLOR] the /Boot folder.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

Stupid question again (I'm sorry), but does that mean I should mount the Windows partition and then go into it and delete that particular folder (the /boot one, not the /Boot)?

And how would I do that? Would it be:
```
sudo mount /dev/sda2 /mnt
```
then:
```
cd /mnt
sudo rm -rf boot
```

Or am I completely wrong? I didn't want to do anything without approval for fear of messing up my system even more.

EDIT: Also, I held down Shift while the BIOS was loading, and it said "GRUB loading" in the top left corner of the screen, but then went blank and wouldn't do anything else. Is that because I wasn't able to run update-grub, or is it something else?

---

### Post by oldfred on 2010-12-06
Since you will be in windows I would be careful editing or deleting files. It may be safer but you still have to be careful to use 

gksudo nautilus

Realize that you can delete or move any system files windows needs, so just use the admin version of Nautilus for the one deletion, then close it.

Not sure about the shift not giving grub menu. Do you boot ok without it?

---

### Post by lcdrovers on 2010-12-06
> **oldfred said:**
> Since you will be in windows I would be careful editing or deleting files. It may be safer but you still have to be careful to use 

gksudo nautilus

Realize that you can delete or move any system files windows needs, so just use the admin version of Nautilus for the one deletion, then close it.

Not sure about the shift not giving grub menu. Do you boot ok without it?

-
I can't boot at all, even without pressing Shift. It just goes blank and doesn't do anything, not even booting to Ubuntu.

EDIT: It doesn't show the "GRUB loading" text that it does when I press Shift, if that matters.

I deleted the /boot folder on the Windows boot partition, using gksudo. I don't know if that was supposed to allow me to run update-grub after unmounting /dev/sda2, but I still get the same error when running it.

I don't really understand what's wrong at the moment. I thought the deletion of the /boot folder would allow me to boot into Windows, but I can't. I'm just really lost. :(

---

### Post by oldfred on 2010-12-06
No, Grub is the boot loader and it sounds like you cannot boot grub? Only after you have booted into Ubuntu should you run the sudo update-grub to find the windows install and add it to the grub menu.

If you cannot boot into Ubuntu. Should be same as ronparent's post above. Did you do that?

#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

---

### Post by lcdrovers on 2010-12-06
> **oldfred said:**
> No, Grub is the boot loader and it sounds like you cannot boot grub? Only after you have booted into Ubuntu should you run the sudo update-grub to find the windows install and add it to the grub menu.

If you cannot boot into Ubuntu. Should be same as ronparent's post above. Did you do that?

#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

I did do what ronparent suggested previously, when he suggested it. I have already carried out that exact sequence of commands, with no errors reported. Is it that I'm not installing it on the correct partition? sudo fdisk -l returned:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x72078d5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       48573   374756331+   7  HPFS/NTFS
/dev/sda4           48573       60802    98229249    5  Extended
/dev/sda5           48573       60299    94188544   83  Linux
/dev/sda6           60299       60802     4039680   82  Linux swap / Solaris
```It says "Linux" in /dev/sda5, so I assume that that's the correct partition to install GRUB to. I already reinstalled GRUB on /dev/sda5.

---

### Post by Quackers on 2010-12-06
No sir!
You mount /dev/sda5
```
sudo mount /dev/sda5 /mnt
```

then install grub to /dev/sda (not sda5)
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

As ronparent suggested :-)

---

### Post by argedion on 2010-12-06
If you suspect there could be hard drive damage I would use a program like Testdisk. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) I have used this in the past and it has fixed disk errors and allowed me to be able to boot my system. I would recommend before doing any changes to the disk that you backup everything that is important to you and put it up. If worst comes to worst you may have to purchase a new hard drive. (Before doing that go to the manufactures web site and see what kind of diagnostic programs they have sometimes they do the right thing to fix these unfortunate errors with out needing to replace the disk. However if the disk is that messed up then replacing it may be a better option in the long run. I would highly recommend you having an external drive with a fresh backup on it at all times it makes situations like this not as bad anyways

---

### Post by oldfred on 2010-12-06
When the two line reinstall does not work we try the full chroot version.
full chroot version:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

You may not have to uninstall grub but otherwise this should be similar to the above.
chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by lcdrovers on 2010-12-06
> **Quackers said:**
> No sir!
You mount /dev/sda5
```
sudo mount /dev/sda5 /mnt
```

then install grub to /dev/sda (not sda5)
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

As ronparent suggested :-)

That's what I was trying to say. I entered in those exact commands already, when ronparent suggested it. The output of fdisk was just because I was wondering if /dev/sda5 was the correct partition to install it on; it looked like it to me, but I wasn't sure. The bottom line is: I already ran that exact sequence of commands, and I still cannot boot into GRUB; I get a blank screen.

EDIT: Well, by the chroot procedure, I was able to get back to accessing the GRUB screen, and I can select an OS now, and I can boot Windows, but I can't boot Ubuntu. So, I'm back where I started. The GRUB2 documentation says this in the chroot sequence:
[QUOTE=GRUB2 Documentation]Only if you have a separate boot partition:
sdYY is the /boot partition designation (for example sdb3)
```
sudo mount /dev/sdYY /mnt/boot
```[/QUOTE]

Should I make that the Windows boot partition? It didn't work when I didn't do that, but I don't know if that would change anything.

---

### Post by oldfred on 2010-12-06
No that is a /boot partition in Ubuntu not a windows partition. Desktop users should not normally have a separate /boot unless they have an old system with the 137GB boot limit (7 or 8 years ago but some a year or two newer). Or if you have RAID or LVM you may want a /boot.

When you say you cannot boot Ubuntu, it it a selection and can you try the recovery boot ( second line) ?

---

### Post by lcdrovers on 2010-12-06
Well, I've screwed myself now. I attempted to purge and reinstall GRUB, but...I purged and couldn't reinstall :'(

I ran every command exactly as stated [here]("http://ubuntuforums.org/showthread.php?t=1581099"), and in step 2, apt-get update responded with this:
```
root@ubuntu:/# apt-get update #***
Hit http://archive.canonical.com maverick Release.gpg
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US
Hit http://archive.canonical.com maverick Release
Hit http://archive.canonical.com maverick/partner amd64 Packages
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US
Get:2 http://dl.google.com stable Release [1,338B]
Get:3 http://dl.google.com stable/main amd64 Packages [630B]
Fetched 2,157B in 4s (510B/s)
Reading package lists... Done
```

I assumed that this meant that it had successfully downloaded the packages. But then, apt-get install grub-pc gave this:

```
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Unable to locate package grub-common
E: Package 'grub-pc' has no installation candidate
```Why would it do this? And how can I fix this? I'm so confused...

---

### Post by oldfred on 2010-12-07
I am confused also, it looks like it should work.

But you should not add anything after a # as that is a comment normally
apt-get update #***

#commands should just be these without comments:
```
apt-get autoclean   
apt-get clean
apt-get update 
apt-get upgrade 
apt-get dist-upgrade

apt-get -f install
dpkg --configure -a
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda
dpkg-reconfigure grub-pc


```

---

### Post by lcdrovers on 2010-12-07
> **oldfred said:**
> I am confused also, it looks like it should work.

But you should not add anything after a # as that is a comment normally
apt-get update #***

#commands should just be these without comments:
```
apt-get autoclean   
apt-get clean
apt-get update 
apt-get upgrade 
apt-get dist-upgrade

apt-get -f install
dpkg --configure -a
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda
dpkg-reconfigure grub-pc


```

I did it first without the #*** and it gave the same message.  When running the commands you gave, it just gave the same error at "apt-get install grub-pc grub-common" that it did before. Is it possible that the issue is that I'm running a 64-bit system and a 32-bit live CD? I thought that the CD was 64-bit, but it might be 32-bit. Could that be causing the problem?

---

### Post by oldfred on 2010-12-07
That could be it as the kernel is different, but I do not know for sure.

---

### Post by Quackers on 2010-12-07
After you ran
```
apt-get update
```

did you run the purge command?
```
apt-get purge grub grub-pc grub-common
```

---

### Post by lcdrovers on 2010-12-07
> **Quackers said:**
> After you ran
```
apt-get update
```

did you run the purge command?
```
apt-get purge grub grub-pc grub-common
```

I ran apt-get purge earlier, now GRUB boots to the rescue prompt because for some reason apt-get install grub-pc grub-common won't work. I'll try using a CD that I know is 64 bit, though, that might help.

EDIT: Is there a simple way to allow access to copying files from a mounted partition? I got a permissions error when I tried from Nautilus, and "sudo cp" just returned "omitting folder danny" (that's the folder I was trying to paste somewhere else. This is from the live CD.

EDIT2: Running gksudo nautilus seemed to work.

EDIT3: Running apt-get install grub-pc grub-common gave the same error on the 64 bit CD as it did on the 32 bit CD :'(

---

### Post by oldfred on 2010-12-07
I am out of ideas. Hope someone else has an idea.

You might try looking at this but I do not know what to look for explicitly. Wrong sources?

nano /etc/apt/sources.list

---

### Post by lcdrovers on 2010-12-07
The sources list might have been it, but I won't ever know now. My wife, unbeknownst to me, had called in a technician to replace the hard drive when I told her how GRUB was acting up. The guy took the previous hard drive back for recycling :'( I'm installing Ubuntu as I'm making this post. Luckily, I had already backed up my important files, so I'll easily be able to replace what I had previously.

I guess we won't ever know how this could have been resolved. It's quite possible that it wasn't possible to resolve, considering that the hard drive may have just been completely messed up in the GRUB partition, as QLee conjectured on the first page. Either way, I'm marking this as solved, because I'm pretty sure that we had exhausted all means to fix this, and it could prove useful to someone else experiencing a similar problem.

I'd like to thank everyone who contributed to this, as although the issue was never and may never be fully resolved, I believe no stone was left unturned in the examination of this problem. You guys are awesome! :D

---

