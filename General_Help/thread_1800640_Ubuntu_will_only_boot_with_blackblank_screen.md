---
title: "Ubuntu will only boot with black/blank screen"
date: 2011-07-09
forum: General Help
---

### Post by Anno8 on 2011-07-09
Hi, 
Ok, so I had a black screen when I was starting up my PC instead of the normal Ubuntu with the dots underneath. I have Ubuntu 11.04 on a dual-boot with Windows Vista. It would still boot normally and work fine but I wanted it with the Ubuntu and dots etc.

After looking at many sites to try and fix it that didn't work I found this: [http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/). That didn't work so I found this next: [http://ubuntuforums.org/showpost.php?p=10750902&postcount=13](http://ubuntuforums.org/showpost.php?p=10750902&postcount=13).

I did what it said by removing ```
vt.handoff=7
```
Then when rebooted I got the Ubuntu with the purple background and dots but the boot would hang (always when all 5 dots were orange). I booted into recovery mode and I chose "File System Check" on reboot and it would get to the bit with 5 orange dots then it would check disk for errors and go to login screen then work fine.

If I added [COLOR="Orange"]vt.handoff=7[/COLOR] it would boot normally with a black screen again.




RESULTS.txt is from when I had [COLOR="Orange"]vt.handoff=7[/COLOR] removed and I was in Recovery mode>resume normal boot>"sudo bash ~/Desktop/boot_info_script.sh".

RESULTS1.txt is from when I booted up with the disk check and was in Terminal.

-----

EDIT: Also just recently I'm getting a lot of boot hangs, freezes (where everything on screen will freeze and if I was playing music in Banshee it repeats the last 3 seconds until I hold down button on PC), and it will sometimes just restart randomly. Not sure if that related or not...

Thanks :)

---

### Post by Anno8 on 2011-07-09
bump...

---

### Post by wildmanne39 on 2011-07-09
Hi, you need to be careful messing with the grub you will make it where it will not boot at all, here is a link so you can change your boot screen picture, but it is still a little tricky.
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by wildmanne39 on 2011-07-10
Hi, I just looked at your boot script you have this installed as wubi, I am not sure you can change the picture in a wubi install, here are some links just for wubi.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
I do not recommend changing grub until you read what these links have to say, and I would post the question in the wubi mega thread.

---

### Post by Anno8 on 2011-07-10
> **wildmanne39 said:**
> Hi, you need to be careful messing with the grub you will make it where it will not boot at all, here is a link so you can change your boot screen picture, but it is still a little tricky.
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Where in that link should I be looking?

---

### Post by Anno8 on 2011-07-10
> **wildmanne39 said:**
> Hi, I just looked at your boot script you have this installed as wubi

Are you sure?
I'm 99.999% sure I installed a normal dual boot with Windows Vista.

---

### Post by wildmanne39 on 2011-07-10
> **Anno8 said:**
> Where in that link should I be looking?Hi, move your mouse to here you see the text that begins with http. Please do not mess with grub until you go to the links in my last post.

---

### Post by Anno8 on 2011-07-10
> **wildmanne39 said:**
> Hi, move your mouse to here you see the text that begins with http. Please do not mess with grub until you go to the links in my last post.

Where do you want me to look on this page: [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)?
Do you want me to read all of it?
I can't see anything to do with my problem in that link.

---

### Post by wildmanne39 on 2011-07-10
> **Anno8 said:**
> Where do you want me to look on this page: [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)?
Do you want me to read all of it?
I can't see anything to do with my problem in that link.
Hi, if you look in the first paragraph it has a link for using grub customizer that will let you change the boot screen, but like I said it is still a little hard to use,and It might not work with your system because you are using wubi right? Also you are going to need to slow down and read the page when you click on grub customizer, but I still recommend posting this question in the mega thread before you go ahead and try to change your grub menu because it will not be that easy to fix if you break it.

---

### Post by Anno8 on 2011-07-10
> **wildmanne39 said:**
> you are using wubi right?
Not right, I already told you:
> **Anno8 said:**
> I'm 99.999% sure I installed a normal dual boot with Windows Vista.



Anyway I don't think you understand what I said in my first post...
I got the splash screen with Ubuntu and the dots working by following this: [http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/) and then this: [http://ubuntuforums.org/showpost.php?p=10750902&postcount=13](http://ubuntuforums.org/showpost.php?p=10750902&postcount=13).

But when I reboot it hangs at 5 orange dots before I get to the login screen. I went into the recovery mode and did File System Check and it would work and I would get to the login screen. If I then added [COLOR="DarkRed"]vt.handoff=7[/COLOR] to the grub file again it will go back to what I had before (black screen but everything working fine).

So the only way I can get it to work with the splash screen (Ubuntu and dots etc.) is to boot into recovery and choose File System Check every time I boot...
If I want to use computer without going into recovery mode and choosing File System Check I have to add [COLOR="DarkRed"]vt.handoff=7[/COLOR] to the grub file again (but this gives me a black screen during startup).

I want to have the splash screen and not have to go into recovery mode each time.

---

### Post by wildmanne39 on 2011-07-10
Hi, yes I understood that from the start, that is what grub customizer is for in that link I gave you.
Also I looked at your boot script it looks like you have ubuntu installed with wubi and also installed as a dual boot.

---

### Post by Anno8 on 2011-07-10
> **wildmanne39 said:**
> Hi, yes I understood that from the start, that is what grub customizer is for in that link I gave you

So how would I go about fixing my problem with Grub Customizer?
Is there a guide somewhere?

> **wildmanne39 said:**
> Also I looked at your boot script it looks like you have ubuntu installed with wubi and also installed as a dual boot.

Are you sure?
Is that bad?

---

### Post by Anno8 on 2011-07-10
bump

---

### Post by wildmanne39 on 2011-07-10
> **Anno8 said:**
> bumpHi, the boot script says wubi and a dual install, that is why I am afraid that you may end up with a system that is unbootable, but I admit I am not an expert in reading these scripts but it mentions wubi and I have never seen it do that otherwise. On the link that I gave you if you read further down the page it tells you about being able to put pictures in the boot menu, that is what I did I have a nice picture as my boot screen, but it still took a lot of effort to get it there and reading. I believe when you install grub customizer you will find links to my pages on using it, I am not going to be on mos of the day, I am working on a guide for the cube and effects.  Also you are only allowed to bump a thread after 24 hours, and only once every 24 hours.

---

### Post by oldfred on 2011-07-10
If you boot windows then you should also get a choice to boot the wubi install of Ubuntu. You have both a full install and a wubi install in windows.

Which is giving you issues. Is the real issue related to video issues? Or is it just slow booting in your opinion.

If video issues what have you tried & what video card do you have?

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by MG&amp;TL on 2011-07-10
Sorry, didn't realise there was two pages..how do I delete a post?

---

### Post by wildmanne39 on 2011-07-10
Hi oldfred, thank you for taking a look at the script information for me, I appreciate it very much.
@Anno8
I think you can get the screen you want by going into windows and deleting your wubi install, but since you have ubuntu already installed in a dual boot with windows I can not promise that it will not have some kind of side effect. Oldfred is very good with booting issues and reading boot script information that is why I asked him to take a look and he confirmed that you have ubuntu installed both ways.

---

### Post by Anno8 on 2011-07-11
> **wildmanne39 said:**
> put pictures in the boot menu

No, the boot menu screen works fine, I don't want to change that or put a picture background on it.

You know the screen between the boot menu and the login screen? With the Ubuntu logo and the 5 dots that change from white to orange?
I have a black screen where that should be.


> **oldfred said:**
> If you boot windows then you should also get a choice to boot the wubi install of Ubuntu. You have both a full install and a wubi install in windows.

After I choose Windows in the GRUB menu I get no choice for anything, it boots straight into Windows.
I installed Ubuntu by shrinking my NTFS partition then I booted to the Live CD and installed Ubuntu into the free space.
How do I check if I have/uninstall wubi?

> **oldfred said:**
>  Which is giving you issues. Is the real issue related to video issues? Or is it just slow booting in your opinion.

I didn't know I had wubi installed, and I don't want to use it.
Booting speed is fine.

> **oldfred said:**
> If video issues what have you tried & what video card do you have?

What I have tried: look at my [first post]("http://ubuntuforums.org/showpost.php?p=11029731&postcount=1")

Video Card: nVidia Corporation C61 [GeForce 6150SE nForce 430 (rev a2)

--


This is what is in my /etc/default/grub (if it is of any help.)
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT=40
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=" vga=791"
```

---

### Post by Anno8 on 2011-07-11
Ok, if I delete [COLOR="DarkRed"]vt.handoff=7[/COLOR] from [COLOR="Sienna"]/etc/grub.d/10_linux[/COLOR] and then change ```
GRUB_CMDLINE_LINUX=" vga=791"
```
to```
GRUB_CMDLINE_LINUX="splash vga=791 quiet"
``` in [COLOR="Sienna"]/etc/default/grub[/COLOR]
I get the Ubuntu logo with the orange and white dots on reboot. But because I changed [COLOR="Sienna"]/etc/default/grub[/COLOR] I get the dots that change from orange to white (about 3 times I think), but unlike in post [#1]("http://ubuntuforums.org/showpost.php?p=11029731&postcount=1") where it would stop at 5 orange dots this time it goes to the bit with 5 orange dots then goes to 1 white dot, 4 orange dots, then goes back to 5 orange dots before freezing again.



I also found out that if I go into Recovery Mode>resume normal boot>[COLOR="DarkRed"]sudo service gdm start[/COLOR] (with the above^ paragraph settings) I can get to the normal login screen  just like if I chose [COLOR="DarkRed"]File System Check[/COLOR] like in post [#1]("http://ubuntuforums.org/showpost.php?p=11029731&postcount=1").

But for some reason it won't work if I just chose to boot normally like this it freezes.
Is there some way I can get it to show where it freezes and the error etc.?

---

### Post by Anno8 on 2011-07-11
If I press [COLOR="DarkRed"]ESC[/COLOR] during boot (with the Ubuntu logo etc.) and before it freezes, it goes to a black screen then goes to black screen with some text then boots.


Also if I wait until it freezes then I press [COLOR="DarkRed"]ESC[/COLOR] then I press [COLOR="DarkRed"]CTRL+ALT+DELETE[/COLOR] it will show a black screen with some text just before it restarts. I managed to get a snapshot of it:
[IMG]https://media.catch.com/v2/media/dist/AIADAMBQGAYDAMBQGAYDAMBQGAYDAMBRME2GGMJTGE2GKMLBMU2TSZJVGNTDGZTFGZQWEMRQGAZDKOBXVPMGDB5J2JMIW%3D%3D%3D/EKFZHIDIZ2YGX4LWIOPO62C7LW53LELXAASXV6Y%3D[/IMG]

---

### Post by Anno8 on 2011-07-11
[SIZE="2"]Here is some of my boot files.
I currently have to press [COLOR="DarkRed"]ESC[/COLOR] during boot to get to the log in screen or it will freeze.[/SIZE]



[COLOR="DarkOrange"][FONT="Arial Black"][SIZE="3"]/etc/default/grub[/SIZE][/FONT][/COLOR]
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT=40
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX="vga=792 splash quiet"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```




[COLOR="DarkOrange"][FONT="Arial Black"][SIZE="3"]/etc/grub.d/10_linux[/SIZE][/FONT][/COLOR]
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

if [ "x`${grub_probe} --device ${GRUB_DEVICE} --target=fs 2>/dev/null || true`" = xbtrfs ]; then
  rootsubvol="`make_system_path_relative_to_its_root /`"
  rootsubvol="${rootsubvol#/}"
  if [ "x${rootsubvol}" != x ]; then
    GRUB_CMDLINE_LINUX="rootflags=subvol=${rootsubvol} ${GRUB_CMDLINE_LINUX}"
  fi
fi

for word in $GRUB_CMDLINE_LINUX_DEFAULT; do
  if [ "$word" = splash ]; then
    GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT"
  fi
done

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
  if ! ${recovery} ; then
      save_default_entry | sed -e "s/^/\t/"
  fi

  cat << EOF
	set gfxpayload=\$linux_gfx_mode
EOF

  if [ -z "${prepare_boot_cache}" ]; then
    prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
  fi
  printf '%s\n' "${prepare_boot_cache}"
  if [ "x$5" != "xquiet" ]; then
    message="$(gettext_printf "Loading Linux %s ..." ${version})"
    cat << EOF
	echo	'$message'
EOF
  fi
  cat << EOF
	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  if test -n "${initrd}" ; then
    if [ "x$5" != "xquiet" ]; then
      message="$(gettext_printf "Loading initial ramdisk ...")"
      cat << EOF
	echo	'$message'
EOF
    fi
    cat << EOF
	initrd	${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

list=`for i in /boot/vmlinuz-* /boot/vmlinux-* /vmlinuz-* /vmlinux-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`
prepare_boot_cache=

# Use ELILO's generic "efifb" when it's known to be available.
# FIXME: We need an interface to select vesafb in case efifb can't be used.
if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
  echo "set linux_gfx_mode=$GRUB_GFXPAYLOAD_LINUX"
else
  cat << EOF
if [ \${recordfail} != 1 ]; then
  if [ -e \${prefix}/gfxblacklist.txt ]; then
    if hwmatch \${prefix}/gfxblacklist.txt 3; then
      if [ \${match} = 0 ]; then
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
EOF
fi
cat << EOF
export linux_gfx_mode
if [ "\$linux_gfx_mode" != "text" ]; then load_video; fi
EOF

in_submenu=false
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

  initramfs=
  for i in "config-${version}" "config-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initramfs=`grep CONFIG_INITRAMFS_SOURCE= "${dirname}/${i}" | cut -f2 -d= | tr -d \"`
      break
    fi
  done

  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  elif test -z "${initramfs}" ; then
    # "UUID=" magic is parsed by initrd or initramfs.  Since there's
    # no initrd or builtin initramfs, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

  linux_entry "${OS}" "${version}" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}" "${version}" true \
	"single ${GRUB_CMDLINE_LINUX}"
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`

  if [ "$list" ] && ! $in_submenu; then
    echo "submenu \"Previous Linux versions\" {"
    in_submenu=:
  fi
done

if $in_submenu; then
  echo "}"
fi
```




[COLOR="DarkOrange"][FONT="Arial Black"][SIZE="3"]/etc/initramfs-tools/modules[/SIZE][/FONT][/COLOR]
```
# List of modules that you want to include in your initramfs.
# They will be loaded at boot time in the order below.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
uvesafb mode_option=1024x768-24 mtrr=3 scroll=ywrap
```


[SIZE="2"][FONT="Arial"]What else should I post here to help you guys out?[/FONT][/SIZE]

---

### Post by wildmanne39 on 2011-07-11
Hi, did you try to uninstall the wubi install through window? like I said I think it will fix your issue. Changing all of those boot parameters is only going to cause you problems, I doubt it will ever get you the screen you want, I will tell you that I used grub customizer to change my background image and it stays on the screen until it gets to the login screen which I also changed to a very cool back ground.

---

### Post by oldfred on 2011-07-12
I also have not made many adjustments to the grub settings file.

I do know that you should not use a vga setting any more.

vga=xxx is a deprecated boot option
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)
"VGA Deprecated" Message on Boot
[http://ubuntuforums.org/showthread.php?t=1453524](http://ubuntuforums.org/showthread.php?t=1453524)
VGA conversions:
[http://wiki.archlinux.org/index.php/Gensplash](http://wiki.archlinux.org/index.php/Gensplash)
[http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes](http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes)

Use a setting like this except for the xy size you need:

GRUB_GFXMODE=1024x768

---

### Post by Anno8 on 2011-07-13
> **oldfred said:**
> 
vga=xxx is a deprecated boot option
Use a setting like this except for the xy size you need:
GRUB_GFXMODE=1024x768

So in [COLOR="DarkRed"]/etc/default/grub[/COLOR] I should change ```
GRUB_CMDLINE_LINUX="vga=792 splash quiet"
``` to ```
GRUB_GFXMODE=1024x768
```?

---

### Post by Anno8 on 2011-07-13
> **wildmanne39 said:**
> I used grub customizer to change my background image

Good for you.
I don't want to have a custom image, I just want the normal one to work.

---

### Post by Anno8 on 2011-07-13
Is there a way to tell where it is freezing during boot?

---

### Post by oldfred on 2011-07-13
you can remove the quiet & splash on a one time basis by using e in the grub menu and editing out the quiet splash. The you see each command being processed and may see the last command(s) that are causing the problem. It is not always the last command, though. The infomation is also recorded in the log files. If booting then you can view all logs in system, administration, log file view. They are in /var/log otherwise.

The actual setting you should use is the one that matches your monitor & video card. So it may not be 
1024x768.

---

### Post by Anno8 on 2011-07-13
> **oldfred said:**
> 
Use a setting like this except for the xy size you need:

GRUB_GFXMODE=1024x768

My native monitor resolution is 1440x900 but I'm using 1024x768 at boot because 1440x900 was not available.

---

### Post by Anno8 on 2011-07-13
> **oldfred said:**
> you can remove the quiet & splash on a one time basis by using e in the grub menu and editing out the quiet splash. The you see each command being processed and may see the last command(s) that are causing the problem. It is not always the last command, though. The infomation is also recorded in the log files. If booting then you can view all logs in system, administration, log file view. They are in /var/log otherwise.

I edited out quiet splash from the grub menu by pressing e and it booted up fine here is the boot.log:
```

Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... done.
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
fsck from util-linux-ng 2.17.2
udevd[342]: can not read '/etc/udev/rules.d/z80_user.rules'


/dev/sda6: clean, 287355/1978592 files, 6528158/7907584 blocks
init: ureadahead-other main process (615) terminated with status 4

 * Starting network connection manager[122G[ OK ]
 * Starting load fallback graphics devices[122G[ OK ]
 * Stopping load fallback graphics devices[122G[ OK ]
 * Starting GNOME Display Manager[122G[ OK ]

```

so it seems to be a problem with having a splash screen...

---

### Post by oldfred on 2011-07-13
I think messages is the full listing of everything that is loaded on booting. Boot log used to not have anything.

I am surprised that just removing quiet & splash let it work.:) But whatever works.

---

### Post by Anno8 on 2011-07-14
> **oldfred said:**
> 
I am surprised that just removing quiet & splash let it work.:)

It worked but it still didn't solve my problem.



But if I change my /etc/default/grub to this:
```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT=40
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_GFXMODE=1024x768
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

```
and I add [COLOR="DarkRed"]vt.handoff=7[/COLOR] to line 69 of [COLOR="DarkOrange"]/etc/grub.d/10_linux[/COLOR]

It boots up with a purple screen instead of a black screen

---

### Post by Anno8 on 2011-07-14
Has anyone ever had a purple screen during boot?
How to fix?

---

### Post by wildmanne39 on 2011-07-14
Hi, I am glad oldfred was able to help.

---

### Post by Anno8 on 2011-07-14
I'm currently getting a purple screen during boot but in /etc/default/grub in line 20 if I change ```
# GRUB_TERMINAL="console"
```
to ```
GRUB_TERMINAL="console"
```
It works with the splash screen and everything but everything looks weird like it was an older version of Ubuntu or something...

---

### Post by linuxman94 on 2011-07-14
The grub_terminal option disables booting to a graphical environment.  I also get the purple screen during boot.  It's do to the proprietary graphics drivers.  I don't really mind it because i can still get into ubuntu.

---

### Post by Anno8 on 2011-07-14
> **linuxman94 said:**
> i can still get into ubuntu.

I can too but I would like a nicer boot screen

---

### Post by linuxman94 on 2011-07-14
Have you tried [this]("http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/")?

---

### Post by wildmanne39 on 2011-07-14
> **Anno8 said:**
> I can too but I would like a nicer boot screenHI, thats why I used grub2 to select my own.

---

### Post by linuxman94 on 2011-07-14
He wants a better looking plymouth boot screen, not a background for the grub2 loader.

---

### Post by Anno8 on 2011-07-14
> **linuxman94 said:**
> Have you tried [this]("http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/")?

Just tried it.
It boots up and everything looks like it's working. The Ubuntu logo and the dots show up but it freezes just before the login screen.

Looking at the [page]("http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/") the script looks like it did exactly what I did in post [#1]("http://ubuntuforums.org/showpost.php?p=11029731&postcount=1"): > **Anno8 said:**
> After looking at many sites to try and fix it that didn't work I found this: [http://idyllictux.wordpress.com/2010...ricted-driver/](http://idyllictux.wordpress.com/2010...ricted-driver/). That didn't work so I found this next: [http://ubuntuforums.org/showpost.php...2&postcount=13](http://ubuntuforums.org/showpost.php...2&postcount=13)
except the script did it automatically...

---

### Post by linuxman94 on 2011-07-14
I suspect something is wrong with the video drivers.  Boot into recovery mode and select the option for failsafe x.  When the dialog pops up close it.  Once you are logged in go to the menu and open the additional drivers application.  Install the drivers that it recommends for your graphics card.

---

### Post by Anno8 on 2011-07-14
> **linuxman94 said:**
> I suspect something is wrong with the video drivers.  Boot into recovery mode and select the option for failsafe x.  When the dialog pops up close it.  Once you are logged in go to the menu and open the additional drivers application.  Install the drivers that it recommends for your graphics card.

Did that then I restarted and booted normally and it booted up good but it didn't load unity, it loaded the old "Ubuntu (classic)". So I configured video drivers etc. But when I rebooted again it freezes...

---

### Post by Anno8 on 2011-07-14
List of ways to get Ubuntu to start while using [this]("http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/") configuration:

*press ESC key during boot but before it freezes
*go into recovery mode>resume normal boot>"sudo service gdm start"
*go into recovery and choose File System Check
*press the "e" key while in GRUB menu and remove "quiet" and "splash"
*use the non-propriety drivers

I need to find out why it's freezing and fix it...

---

### Post by linuxman94 on 2011-07-14
Hmmm :-k Lets try this.  Get into ubuntu again and reinstall gdm by using these commands.

```
sudo apt-get remove --purge gdm
sudo apt-get install gdm
```

---

### Post by Anno8 on 2011-07-14
In System Settings>Additional Drivers>Nvidia accelerated graphics driver (version current) [recommended] it says "This driver is activated but not currently in use."

I'm pretty sure it's in use because I'm running unity...

---

### Post by linuxman94 on 2011-07-14
The additional drivers utility can be buggy at times.  Just to make sure the drivers are running, look at the /etc/X11/xorg.conf file (run cat /etc/X11/xorg.conf) and in the device section, next to driver it should list the nvidia driver. If it does you're good to go.

Edit: It's late here in Illinois so I'll help more tomorrow.

---

### Post by Anno8 on 2011-07-14
> **linuxman94 said:**
> Hmmm :-k Lets try this.  Get into ubuntu again and reinstall gdm by using these commands.

```
sudo apt-get remove --purge gdm
sudo apt-get install gdm
```

Did that and rebooted, it worked, tried rebooting again a couple times just to make sure and it freezes at 5 orange dots as usual...

---

### Post by Anno8 on 2011-07-14
> **linuxman94 said:**
> The additional drivers utility can be buggy at times.  Just to make sure the drivers are running, look at the /etc/X11/xorg.conf file (run cat /etc/X11/xorg.conf) and in the device section, next to driver it should list the nvidia driver. If it does you're good to go.

yep, it's working fine

> **linuxman94 said:**
> 
Edit: It's late here in Illinois so I'll help more tomorrow.

ok

---

### Post by linuxman94 on 2011-07-14
OK i saw this on a blog and this is what he did to get it working.

```
sudo add-apt-repository ppa:gdm2setup/gdm2setup

sudo apt-get update

sudo apt-get install python-gdm2setup
```

---

### Post by Anno8 on 2011-07-18
> **linuxman94 said:**
> OK i saw this on a blog and this is what he did to get it working.

> sudo add-apt-repository ppa:gdm2setup/gdm2setup

```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 33E1C2F5E880004C06B6696B1780999033C3C104
gpg: requesting key 33C3C104 from hkp server keyserver.ubuntu.com
gpg: key 33C3C104: "Launchpad GDM2Setup" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
```


> 
sudo apt-get install python-gdm2setup

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package python-gdm2setup
```

It didn't work...

---

### Post by Anno8 on 2011-07-18
In System Settings> Additional Drivers, I chose [COLOR="DarkRed"]NVIDIA accelerated graphics driver (**version 173**)[/COLOR] instead of what I had before which was [COLOR="DarkRed"]NVIDIA accelerated graphics driver (**version current**) [Recommended][/COLOR].

Now it boots up great, unity and 3D games work....  but is it ok to have [COLOR="Sienna"]version 173[/COLOR] instead of [COLOR="Sienna"]version current[/COLOR]?

---

### Post by Anno8 on 2011-07-19
> **Anno8 said:**
> is it ok to have [COLOR="Sienna"]version 173[/COLOR] instead of [COLOR="Sienna"]version current[/COLOR]?
???


...I guess I'll just mark this thread as solved then...

---

