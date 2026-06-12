---
title: "How to change Ubuntu rootdelay"
date: 2010-07-15
forum: General Help
---

### Post by JoelAllen on 2010-07-15
I recently installed ubuntu 10.04

when i boot up i get "gave up waiting for root device" then i get dropped to a shell.

my hardware is taking too long... cause if i wait a few minutes then type exit it boots normally. 

so i must have to increase my rootdelay.

please try to explain step by step in detail cause im totally new to ubuntu.

i read around i people just say "edit /boot/grub/menu.lst" but i dont really know what that means... :D

---

### Post by dcstar on 2010-07-16
> **JoelAllen said:**
> 
........
i read around i people just say "edit /boot/grub/menu.lst" but i dont really know what that means... :D

That is an ancient file that does not apply to the version you are using - totally ignore any information related to it.

You need to edit the /etc/default/grub file and then do other steps to make these sort of changes.

Do a web search for Grub2 HOWTO and see if you can find something you can understand.

---

### Post by JoelAllen on 2010-07-16
i did in terminal:

```

sudo gedit /etc/default/grub

```

and here is what is in the file: (i didnt put the stuff in comments)

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR='lsb release -i -s 2> /dev/null || echo Debian'
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" "

```

then i read that you do in terminal:

```
sudo update-grub
```

so what do i have to change or add to make my rootdelay much longer?

---

### Post by Blue Screen on 2010-08-31
Here is the fix for root delay...

After the Busy Box error message comes up, wait 15 seconds, then type "exit" (without the quotes.) and hit enter.

You should boot into your Ubuntu OS.  If not, keep typing exit and hit enter until it does.

To avoid this procedure in the future, open your Terminal (in Accessories) and enter this command:

sudo gedit /etc/default/grub  (spaces between sudo gedit / are required)

In the pop up window, edit as follows:

GRUB_TIMEOUT=0

Under GRUB_CMDLINE_LINUX=" " add this line:

GRUB_DISABLE_LINUX_UUID=true

Click save and go back to command terminal.  Enter:

sudo update-grub  (enter)

Then reboot your computer.  You should no longer have the hang up or the need to enter commands,

There you go.  This resolved my own root delay issue on Ubuntu 10.04.  :D

---

### Post by denegen on 2010-09-08
I ran into the same problem after adding a Sweex SATA PCI controller  on Ubuntu 10.04.

In my case I added a file 09_linux_rootdelay as root to /etc/grub.d/ with the following contents.

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
    title="$(gettext_quoted "%s, with Linux %s (recovery mode), rootdelay=90")"
  else
    title="$(gettext_quoted "%s, with Linux %s, rootdelay=90")"
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
    echo    '$(printf "$(gettext_quoted "Loading Linux %s ...")" ${version})'
EOF
  fi
  cat << EOF
    linux    ${rel_dirname}/${basename} rootdelay=90 root=${linux_root_device_thisversion} ro ${args}
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

list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
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

```This is a copy of 10_linux, with minor changes to set the rootdelay:

```

linux    ${rel_dirname}/${basename} rootdelay=90 root=${linux_root_device_thisversion} ro ${args}

```Naming the file 09_linux_rootdelay allows the file to add entries before the entires created by 10_linux and so will be used as default. Also after kernel updates, these entries should still work and UUIDs are preserved.

Be sure to run sudo chmod +x on the file and run sudo update-grup afterwards.

---

### Post by pirround on 2012-03-20
> **denegen said:**
> I ran into the same problem after adding a Sweex SATA PCI controller  on Ubuntu 10.04.

In my case I added a file 09_linux_rootdelay as root to /etc/grub.d/ with the following contents.

<snip>

Be sure to run sudo chmod +x on the file and run sudo update-grup afterwards.

Thanks denegen - exactly what I needed to know =D>(and couldn't find elsewhere).  (The last command should be
     *sudo update-grub*
of course.

---

### Post by oldos2er on 2012-03-20
Closed, necromancy.

---

### Post by oldfred on 2013-12-01
I do not know what problem is. 
Some other threads with possible info:

 See post #4 busybox exit & boot - blue screen;s post
[http://ubuntuforums.org/showthread.php?t=1531999&highlight=rootdelay](http://ubuntuforums.org/showthread.php?t=1531999&highlight=rootdelay)
busybox See quixote post
[http://ubuntuforums.org/showthread.php?t=1561652&highlight=rootdelay](http://ubuntuforums.org/showthread.php?t=1561652&highlight=rootdelay)

---

