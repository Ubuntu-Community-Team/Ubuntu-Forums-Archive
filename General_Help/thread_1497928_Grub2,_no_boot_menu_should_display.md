---
title: "Grub2, no boot menu should display"
date: 2010-05-31
forum: General Help
---

### Post by Sonia. on 2010-05-31
Hi,
I was using old version of grub in which i see this message "Press any key to get boot menu" then on pressing any key, i can see boot menu and with out pressing any key by user, windows booted successfully.

Now, i want this in grub2. Currently, grub2 shows boot menu without pressing any key. I want like this: on booting User first see this message "Press any key to get boot menu" and if user presses any key only then boot menu display otherwise windows should boot directly.


Thanks in advance.

---

### Post by drs305 on 2010-05-31
I can help you get part of what you want...

First, I don't know of a way to display the "Press any key" message during boot. You just have to *know* that you have to press the SHIFT key to interrupt the sequence.

Second, to get a blank screen it's a bit awkward because the blank screen is designed for single OS machines in Grub2. But one of the advantages of Grub2 is that you (root) can modify the scripts to accomplish this.

First, let's set the default to be Windows:
1. Determine which *menuentry* is your Windows one. You can count them in /boot/grub/grub.cfg, starting at 0, or run this command. For example, if Windows is the third menuentry, it would be 2 in the /etc/default/grub GRUB_DEFAULT= setting. Don't count any entries starting with a # symbol.
```
grep "menuentry" /boot/grub/grub.cfg
```

Open the two files we will be modifying - /etc/default/grub and /etc/grub.d/30_os-prober - as root:
```
gksu gedit /etc/default/grub /etc/grub.d/30_os-prober
```

In /etc/default/grub, make these changes. You don't have to include the # symbol or what follows. Those are just notes.

> GRUB_DEFAULT=0  # Change to the Windows number you came up with.   
GRUB_HIDDEN_TIMEOUT=5   # Number of seconds for the blank screen to wait for user to press the SHIFT key.
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10  # Set this to the number of seconds you want the menu displayed if the SHIFT key is pressed. When the timeout expires if nothing is selected, the default OS will boot.

Save the file and go to the /etc/grub.d/30_os-prober tab.
You must comment (#) two lines. In Grub 1.98 they are at approximately lines 28 and 62.

> adjust_timeout () {
[COLOR="Red"]**#**[/COLOR]  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${GRUB_HIDDEN_TIMEOUT}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then

...

EOF
      fi
    fi
[COLOR="Red"]**#**[/COLOR]  fi
}

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then
  adjust_timeout
  exit 0
fi

Save the file, then update Grub2:
```
sudo update-grub
```

---

### Post by Sonia. on 2010-06-01
I have grub2 and i don't have adjust_timeout() in this file:
/etc/grub.d/30_os-prober tab.

Please provide me updates.

Thanks in advance,

---

### Post by Elfy on 2010-06-01
I'd suggest you post your os_prober file here. 

Run this from a terminal 

```
cat /etc/grub.d/30_os-prober
```

Paste the whole thing here - please put [noparse]```
[/noparse] at the beginning of the paste and [noparse]
```[/noparse] at the end of the paste.

---

### Post by Sonia. on 2010-06-01
This is the result

```



#! /bin/sh -e
# update-grub helper script.
# Copyright (C) 2006,2007,2008  Free Software Foundation, Inc.
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

if [ -z "`which os-prober 2> /dev/null`" -o -z "`which linux-boot-prober 2> /dev/null`" ] ; then
  # missing os-prober and/or linux-boot-prober
  exit 0
fi

OSPROBED="`os-prober 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"
if [ -z "${OSPROBED}" ] ; then
  # empty os-prober output, nothing doing
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

  case ${BOOT} in
    chain)
      CHAINROOT="`grub-probe --target=drive --device ${DEVICE} 2> /dev/null`"

      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
	set root=${CHAINROOT}
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

        LINUXROOT="`grub-probe --target=drive --device ${LBOOT} 2> /dev/null`"

        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

        cat << EOF
menuentry "${LLABEL} (on ${DEVICE})" {
	set root=${LINUXROOT}
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
    hurd|*)
      echo "  ${LONGNAME} is not yet supported by update-grub." >&2
    ;;
  esac
done




```

---

### Post by dino99 on 2010-06-01
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html)

---

### Post by Jakiejake on 2010-06-01
> **Sonia. said:**
> Hi,
I was using old version of grub in which i see this message "Press any key to get boot menu" then on pressing any key, i can see boot menu and with out pressing any key by user, windows booted successfully.

Now, i want this in grub2. Currently, grub2 shows boot menu without pressing any key. I want like this: on booting User first see this message "Press any key to get boot menu" and if user presses any key only then boot menu display otherwise windows should boot directly.


Thanks in advance.

Try Startup-manager

---

### Post by drs305 on 2010-06-01
Sonia,

The file you posted must be an earlier version of Grub 2's 30_os-prober, as it is much different than the one used now. You can check your Grub2 version number with this command:
```
grub-install -v
```
You probably have version 1.97~beta or earlier. Unfortunately I am no longer using any of the early versions of G2 on my machines and can't try to tweak the scripts. 

If you post your */etc/default/grub* contents we can make sure you have the options set up correctly. Please let us know if you have another OS (Windows, other Linux, etc) on your computer.

There were a lot of bug reports about how G2 displayed (or didn't display) the menu early on, and I will try to look through them once I know which version of G2 you are using and whether you are dual-booting or not.

---

### Post by Sonia. on 2010-06-01
grub2 version is 1.96.
Looking forward for updates

Thanks in advance

---

