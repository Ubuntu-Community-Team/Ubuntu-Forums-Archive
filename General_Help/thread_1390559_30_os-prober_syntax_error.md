---
title: "30_os-prober syntax error"
date: 2010-01-25
forum: General Help
---

### Post by dspisak on 2010-01-25
Hello.  I ran update-grub and received this syntax error.

```
spisaks@djs-pc:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/30_os-prober: 120: Syntax error: "done" unexpected (expecting ";;")
```

I am not a code expert but I cannot find anything wrong.  Here is the file 30_os-prober.

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
	done
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

Any help will be appreciated.  Thank you.

Dan

---

### Post by Leppie on 2010-01-25
did you modify this file yourself, or did you download/copy paste someone else's 30_prober?
you could've found the error yourself quite easily (with a text editor):
```
EOF
    [COLOR=Red]**done**[/COLOR]
    ;;
    linux)
      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"


```that's the culprit...

as the message said:
```

/etc/grub.d/30_os-prober: 120: Syntax error: "done" unexpected (expecting ";;")

```in line 120 the "done" statement is found instead of ";;". removing the "done" line at line 120 will solve this issue. but if you copied this from someone else, there might be other errors.
i have attached a copy of the original 30_os-prober

---

### Post by dspisak on 2010-01-25
[QUOTE=
that's the culprit...

i have attached a copy of the original 30_os-prober[/QUOTE]

Hi, Leppe.  Thank you for the quick response.  I tried deleting "done" and update-grub then responded with ";;" unexpected.  Then removed ";;" and update-grub then responded with ")" unexpected.  At that point I reinserted "done" and ";;".  Thanks for the original 30_os-prober.  I'll put it in the grub.d folder and see what happens.

Dan

---

### Post by Leppie on 2010-01-25
> **dspisak said:**
> Hi, Leppe.  Thank you for the quick response.  I tried deleting "done" and update-grub then responded with ";;" unexpected.  Then removed ";;" and update-grub then responded with ")" unexpected.  At that point I reinserted "done" and ";;".  Thanks for the original 30_os-prober.  I'll put it in the grub.d folder and see what happens.

Dan
i checked with my 30_os-prober and i do not have that "done" statement at line 120 (and i haven't modified mine (yet)).

---

### Post by dspisak on 2010-01-25
I extracted your prober.gz, copied it to the grub.d folder and ran update-grub.  It appears to work correctly.  Thanks for the "fresh" 30_os-prober.

Dan

---

### Post by Leppie on 2010-01-25
you're welcome, glad all is working well now :)

---

### Post by k.aji on 2010-04-03
Thank's and also to this file prober.gz,

last time accidently, I deleted th 30_os-prober file.
Now it is working ..,

Anyway, I wonder how this script run ?
anyone can help me ?

---

