---
title: "suse like tty for ubuntu"
date: 2010-12-06
forum: General Help
---

### Post by pavankumarl73 on 2010-12-06
Hello everyone,
               How to make tty of ubuntu look like tty. It looks nice.

---

### Post by a-user on 2010-12-06
?
ubuntu tty consoles look like any tty console i saw before. what do you mean?

---

### Post by pavankumarl73 on 2010-12-06
> **a-user said:**
> ?
ubuntu tty consoles look like any tty console i saw before. what do you mean?

Sorry. I meant to how to make ubuntu tty color full as suse tty

---

### Post by VCoolio on 2010-12-06
What do you mean exactly? Some picture / text on top if you go into a tty first time? That's set in /etc/issue. Or a fancy bash / zsh prompt? Then google for prompts. Or fancy colors in output etc.? That depends on the $TERM variable, maybe you could use ~/.Xdefaults to specify colors, or ~/.bashrc, and dir_colors. Maybe [this]("http://systhread.net/texts/200703bashish.php") helps.

---

### Post by a-user on 2010-12-06
do you mean the tty consoles you get with ctrl+alt+F1...F6 ?
mine are colored. i have no clue why yours are not. sry.

---

### Post by pavankumarl73 on 2010-12-06
> **a-user said:**
> do you mean the tty consoles you get with ctrl+alt+F1...F6 ?
mine are colored. i have no clue why yours are not. sry.

mine aren't colored. I get traditional black background with white text. Its the same since I installed 9.10 till 10.10. You sure might have done some alterations.

---

### Post by a-user on 2010-12-06
wait, maybe i missunderstood you. mine is grey/whit text on black too. but e.g. listing files with ls shows them colored depending on type (link, directory etc.)

so my tty is colored. yours not? do you maybe only want to change the colorsheme?

---

### Post by sisco311 on 2010-12-06
Are you looking for something like fbterm?

[http://kmandla.wordpress.com/2010/05/28/fbterm-birth-of-the-cool-for-the-console/](http://kmandla.wordpress.com/2010/05/28/fbterm-birth-of-the-cool-for-the-console/)

---

### Post by pavankumarl73 on 2010-12-06
all I meant tty like this

---

### Post by mcduck on 2010-12-06
Just edit your ~/.bashrc, there's an option for enabling the colored prompt. (uncomment the line with "force_color_prompt=yes")

All programs should use colors already, although some (like vim and top) require you to enable colors in the program's options as well.

If you want the colored boot messages, I used to enable that in previous versions, but honestly I'm not even sure if the trick I used would work any more now that Ubuntu has moved to Upstart & Plymouth.

---

### Post by TeoBigusGeekus on 2010-12-06
[http://ubuntuforums.org/showthread.php?t=1635105]("http://ubuntuforums.org/showthread.php?t=1635105")

---

### Post by pavankumarl73 on 2010-12-06
> **mcduck said:**
> Just edit your ~/.bashrc, there's an option for enabling the colored prompt. (uncomment the line with "force_color_prompt=yes")

All programs should use colors already, although some (like vim and top) require you to enable colors in the program's options as well.

If you want the colored boot messages, I used to enable that in previous versions, but honestly I'm not even sure if the trick I used would work any more now that Ubuntu has moved to Upstart & Plymouth.

I tried to edit bashrc file. Its showing some sort of error like unexpected token at some. Could u please be more specific about where should I uncomment.
  Thank you

---

### Post by mcduck on 2010-12-06
just find this line:
```
#force_color_prompt=yes
```

and change it to this:
```
force_color_prompt=yes
```

edit: if you want even more colorful prompt, you could try [Bashish]("http://bashish.sourceforge.net/"). (It should be in the repositories)

---

### Post by pavankumarl73 on 2010-12-07
> **mcduck said:**
> just find this line:
```
#force_color_prompt=yes
```

and change it to this:
```
force_color_prompt=yes
```

edit: if you want even more colorful prompt, you could try [Bashish]("http://bashish.sourceforge.net/"). (It should be in the repositories)

I tried that. But there is no colored prompt. I have read that bashrc file and I think I need to set some parameters as well. I didn't understand much of the things. And I read yesterday that suse uses some kernel patch to get colored tty.

---

### Post by a-user on 2010-12-07
> **pavankumarl73 said:**
> all I meant tty like this
what exactly do you mean by "this"? a tty with that bakground image?

or just that some words are colored?

the latter is default on ubuntu. i wonder how you disabled that.

---

### Post by pavankumarl73 on 2010-12-07
> **pavankumarl73 said:**
> I tried that. But there is no colored prompt. I have read that bashrc file and I think I need to set some parameters as well. I didn't understand much of the things. And I read yesterday that suse uses some kernel patch to get colored tty.

I forgot to mention. It colored the terminal. I want tty screen to be colored

---

### Post by pavankumarl73 on 2010-12-07
> **a-user said:**
> what exactly do you mean by "this"? a tty with that bakground image?

or just that some words are colored?

the latter is default on ubuntu. i wonder how you disabled that.

I want tty screen to be colored like the way in suse. I mean the colorful tty u get while booting up and shutting down

---

### Post by mcduck on 2010-12-07
So you don't actually want colors in terminal (or you already have them), but instead you want the *boot messages* to be colored?

What version of Ubuntu you are running?

---

### Post by VCoolio on 2010-12-07
> **pavankumarl73 said:**
> I want tty screen to be colored like the way in suse. I mean the colorful tty u get while booting up and shutting down

This may be quite difficult to accomplish. At least in archlinux it requires the files /etc/rc.d/functions (with color definitions and stuff) and then /etc/rc.sysinit to use them; I think ubuntu uses totally different boot scripts you don't want to mess with, unless there is an obscure package for it. To give you an idea about what it requires I'll paste the files:

The /etc/rc.d/functions file from archlinux:
```
#
# initscripts functions
#

# width:

STAT_COL=80
if [ ! -t 1 ]; then
  USECOLOR=""

# stty will fail when stdin isn't a terminal
elif [ -t 0 ]; then
  STAT_COL="$(/bin/stty size)"
  # stty gives "rows cols"; strip the rows number, we just want columns
  STAT_COL="${STAT_COL##* }"

else
  # is /usr/share/terminfo already mounted, and TERM recognized?
  /bin/tput cols &>/dev/null
  if [ $? -eq 0 ]; then
    STAT_COL=$(/bin/tput cols)
  fi
fi
if [ "0$STAT_COL" -eq 0 ]; then
  # if output was 0 (serial console), set default width to 80
  STAT_COL=80
  USECOLOR=""
fi

# we use 13 characters for our own stuff
STAT_COL=$(($STAT_COL - 13))

# disable colors on broken terminals
TERM_COLORS="$(/bin/tput colors 2>/dev/null)"
if [ $? = 3 ]; then
	TERM_COLORS=8
elif [ -n "${TERM_COLORS}" ]; then
	case "${TERM_COLORS}" in
		*[!0-9]*)
			USECOLOR=""
			;;
		*)
			[ "${TERM_COLORS}" -lt 8 ] && USECOLOR=""
			;;
	esac
else
	USECOLOR=""
fi
unset TERM_COLORS

# clear the TZ envvar, so daemons always respect /etc/localtime
unset TZ

# colors:
if [ "$USECOLOR" = "YES" -o "$USECOLOR" = "yes" ]; then
	C_MAIN="\033[1;37;40m"      # main text
	C_OTHER="\033[1;34;40m"     # prefix & brackets
	C_SEPARATOR="\033[1;30;40m" # separator

	C_BUSY="\033[0;36;40m"      # busy
	C_FAIL="\033[1;31;40m"      # failed
	C_DONE="\033[1;37;40m"      # completed
	C_BKGD="\033[1;35;40m"      # backgrounded

	C_H1="\033[1;37;40m"        # highlight text 1
	C_H2="\033[1;36;40m"        # highlight text 2

	C_CLEAR="\033[1;0m"
fi

if [ -t 1 ]; then
	SAVE_POSITION="\033[s"
	RESTORE_POSITION="\033[u"
	DEL_TEXT="\033[$(($STAT_COL+4))G"
else
	SAVE_POSITION=""
	RESTORE_POSITION=""
	DEL_TEXT=""
fi

# prefixes:

PREFIX_REG="::"
PREFIX_HL=" >"

# functions:

deltext() {
	printf "${DEL_TEXT}"
}

printhl() {
	printf "${C_OTHER}${PREFIX_HL} ${C_H1}${1}${C_CLEAR} \n"
}

printsep() {
	printf "\n${C_SEPARATOR}   ------------------------------\n"
}

stat_bkgd() {
	printf "${C_OTHER}${PREFIX_REG} ${C_MAIN}${1}${C_CLEAR} "
	deltext
	printf "   ${C_OTHER}[${C_BKGD}BKGD${C_OTHER}]${C_CLEAR} "
}

stat_busy() {
	printf "${C_OTHER}${PREFIX_REG} ${C_MAIN}${1}${C_CLEAR} "
	printf "${SAVE_POSITION}"
	deltext
	printf "   ${C_OTHER}[${C_BUSY}BUSY${C_OTHER}]${C_CLEAR} "
}

stat_append() {
	printf "${RESTORE_POSITION}"
	printf -- "${C_MAIN}${1}${C_CLEAR}"
	printf "${SAVE_POSITION}"
}

stat_done() {
	deltext
	printf "   ${C_OTHER}[${C_DONE}DONE${C_OTHER}]${C_CLEAR} \n"
}

stat_fail() {
	deltext
	printf "   ${C_OTHER}[${C_FAIL}FAIL${C_OTHER}]${C_CLEAR} \n"
}

stat_die() {
	retval=1
	[ "$1" = "" ] || retval=$1
	stat_fail
	exit $retval
}

status() {
	stat_busy "$1"
	shift
	$* >/dev/null 2>&1
	if [ $? -eq 0 ]; then
		stat_done
		return 0
	else
		stat_fail
		return 1
	fi
}

#  usage : in_array( $needle, $haystack )
# return : 0 - found
#          1 - not found
# Copied from makepkg
in_array() {
  local needle=$1; shift
  [ -z "$1" ] && return 1 # Not Found
  local item
  for item in "$@"; do
    local c="${item:0:1}"
    if [ "x$c" = "x@" ]; then
      item="${item:1}"
    fi
    [ "$item" = "$needle" ] && return 0 # Found
  done
  return 1 # Not Found
}

# daemons:

add_daemon() {
	[ -d /var/run/daemons ] || /bin/mkdir -p /var/run/daemons
	/bin/touch /var/run/daemons/$1
}

rm_daemon() {
	/bin/rm -f /var/run/daemons/$1
}

ck_daemon() {
	[ -f /var/run/daemons/$1 ] && return 1
	return 0
}

ck_depends() {
	for daemon in $@; do
		if ck_daemon $daemon; then
			/etc/rc.d/$daemon start
		fi
	done
}

start_daemon() {
	/etc/rc.d/$1 start
}

start_daemon_bkgd() {
	stat_bkgd "Starting $1"
	(/etc/rc.d/$1 start) &>/dev/null &
}

stop_daemon() {
	/etc/rc.d/$1 stop
}

# Status functions
status_started() {
  deltext
  echo -ne "$C_OTHER[${C_STRT}STARTED$C_OTHER]$C_CLEAR "
}

status_stopped() {
  deltext
  echo -ne "$C_OTHER[${C_STRT}STOPPED$C_OTHER]$C_CLEAR "
}

ck_status() {
  ck_daemon $1
  if [ $? -eq 1 ]; then
    status_started
  else
    status_stopped
  fi		
}

###############################
# Custom hooks in initscripts #
###############################
# Hooks can be used to include custom code in various places in the rc.* scripts
#
# Define a hook function in a functions.d file using:
#  function_name() {
#    ...
#  }
#  add_hook hook_name function_name
# It is allowed to register several hook functions for the same hook
# Is is also allowed to register the same hook function for several hooks
#
# Currently, the following hooks exist:
# sysinit_start: at the beginning of rc.sysinit
# multi_start: at the beginning of rc.multi
# single_start: at the beginning of rc.single
# shutdown_start: at the beginning of rc.shutdown
# sysinit_end: at the end of rc.sysinit
# multi_end: at the end of rc.multi
# single_end: at the end of rc.single
# sysinit_udevlaunched: after udev has been launched in rc.sysinit
# single_udevlaunched: after udev has been launched in rc.single
# sysinit_udevsettled: after uevents have settled in rc.sysinit
# single_udevsettled: after uevents have settled in rc.single
# sysinit_premount: before local filesystems are mounted, but after root is mounted read-write in rc.sysinit
# shutdown_prekillall: before all processes are being killed in rc.shutdown
# single_prekillall: before all processes are being killed in rc.single
# shutdown_postkillall: after all processes have been killed in rc.shutdown
# single_postkillall: after all processes have been killed in rc.single
# shutdown_poweroff: directly before powering off in rc.shutdown
#
# Make sure to never override the add_hook and run_hook functions via functions.d

declare -A hook_funcs

add_hook() {
	[ -z "$1" -o -z "$2" ] && return 1
	hook_funcs["$1"]="${hook_funcs["$1"]} $2"
}

run_hook() {
	local func

	[ -z "$1" ] && return 1
	for func in ${hook_funcs["$1"]}; do
		${func}
	done
}

# Function for setting console font if required
set_consolefont() {
    if [ -n "$CONSOLEFONT" ]; then
	stat_busy "Loading Console Font: $CONSOLEFONT"
	#CONSOLEMAP in UTF-8 shouldn't be used
	if [ -n "$CONSOLEMAP" ] && echo "$LOCALE" | /bin/grep -qi utf ; then
		CONSOLEMAP=""
	fi
	for i in /dev/tty[0-9]*; do
		if [ -n "$CONSOLEMAP" ]; then
			/usr/bin/setfont -m $CONSOLEMAP $CONSOLEFONT -C ${i} >/dev/null 2>&1
		else
			/usr/bin/setfont $CONSOLEFONT -C ${i} >/dev/null 2>&1
		fi
	done
	if [ $? -ne 0 ]; then
		stat_fail
	else
		if [ -n "$CONSOLEMAP" ]; then
			echo 'if [ "$CONSOLE" = "" -a "$TERM" = "linux" -a -t 1 ]; then printf "\033(K"; fi' >>/etc/profile.d/locale.sh
		fi
		stat_done
	fi
    fi
}

# Source additional functions at the end to allow overrides
for f in /etc/rc.d/functions.d/*; do
  if [ -e $f ]; then
    . $f
  fi
done

# End of file
# vim: set ft=sh sw=2 ts=2 et:

```

The /etc/rc.sysinit file:
```
#!/bin/bash
#
# /etc/rc.sysinit
#

. /etc/rc.conf
. /etc/rc.d/functions

echo " "
printhl "Arch Linux\n"
printhl "${C_H2}http://www.archlinux.org"
printhl "Copyright 2002-2007 Judd Vinet"
printhl "Copyright 2007-2010 Aaron Griffin"
printhl "Distributed under the GNU General Public License (GPL)"
printsep

run_hook sysinit_start

# mount /proc, /sys and our RAM /dev
if ! /bin/mountpoint -q /proc; then
  /bin/mount -n -t proc none /proc
fi
if ! /bin/mountpoint -q /sys; then
  /bin/mount -n -t sysfs none /sys
fi
if ! /bin/mountpoint -q /dev; then
  if grep -q devtmpfs /proc/filesystems 2>/dev/null; then
    /bin/mount -n -t devtmpfs udev /dev -o mode=0755,size=10M,nosuid
  else
    /bin/mount -n -t tmpfs udev /dev -o mode=0755,size=10M,nosuid
  fi
fi

# Copy static device nodes to /dev
/bin/cp -a /lib/udev/devices/* /dev/

# start up our mini logger until syslog takes over
/sbin/minilogd

# anything more serious than KERN_WARNING goes to the console
# 'verbose' cmdline parameter enables more messages
if /bin/grep -q " verbose" /proc/cmdline; then
	/bin/dmesg -n 8
else
	/bin/dmesg -n 3
fi

HWCLOCK_PARAMS="--hctosys"
if [ "$HARDWARECLOCK" = "UTC" ]; then
	HWCLOCK_PARAMS="$HWCLOCK_PARAMS --utc"
elif [ "$HARDWARECLOCK" = "localtime" ]; then
	HWCLOCK_PARAMS="$HWCLOCK_PARAMS --localtime"
else
	HWCLOCK_PARAMS=""
fi

if [ -n "$HWCLOCK_PARAMS" ]; then
	# enable rtc access
	/sbin/modprobe -q rtc-cmos
	# some custom kernels use rtc/genrtc, try to load those too
	/sbin/modprobe -q rtc
	/sbin/modprobe -q genrtc
	# If devtmpfs is used, the required RTC device already exists now
	# Otherwise, create whatever device is available
	if [ ! -c /dev/rtc -a ! -c /dev/rtc0 ]; then
		if [ -f /sys/class/rtc/rtc0/dev ]; then
			IFS=: read -r major minor < /sys/class/rtc/rtc0/dev
			/bin/mknod /dev/rtc0 c $major $minor
		elif [ -f /sys/class/misc/rtc/dev ]; then
			IFS=: read -r major minor < /sys/class/misc/rtc/dev
			/bin/mknod /dev/rtc c $major $minor
		fi
	fi

	# Do a clock set here for a few reasons:
	# 1. Make creation time on udev nodes sane (FS#8665)
	# 2. Filesystem checks can depend on system time
	# 3. This will set the clock, if using non-UTC, off the last known
	#    configured timezone. Any new timezone put in rc.conf is copied over at
	#    a later time.
	# This does *NOT* take into account a time adjustment file as /var may not be
	# mounted yet. A second set occurs later to match rc.conf.
	if [ -f /etc/localtime ]; then
		/sbin/hwclock $HWCLOCK_PARAMS --noadjfile
	fi
fi

echo > /proc/sys/kernel/hotplug

stat_busy "Starting UDev Daemon"
/sbin/udevd --daemon
stat_done

run_hook sysinit_udevlaunched

# Trigger udev uevents
if /bin/pidof -o %PPID /sbin/udevd >/dev/null; then
  stat_busy "Triggering UDev uevents"
  /sbin/udevadm control --property=STARTUP=1
  /sbin/udevadm trigger --action=add
  stat_done
fi

# Load modules from the MODULES array defined in rc.conf
if ! [ "$load_modules" = "off" ]; then
	if [ -f /proc/modules ]; then
		stat_busy "Loading Modules"
		for mod in "${MODULES[@]}"; do
			if [ "$mod" = "${mod#!}" ]; then
				/sbin/modprobe $mod
			fi
		done
		stat_done
	fi
fi

# Wait for udev uevents
if /bin/pidof -o %PPID /sbin/udevd >/dev/null; then
	stat_busy "Waiting for UDev uevents to be processed"
	/sbin/udevadm settle
	/sbin/udevadm control --property=STARTUP=
	stat_done
fi

run_hook sysinit_udevsettled

# bring up the loopback interface
if [ -d /sys/class/net/lo ]; then
	stat_busy "Bringing up loopback interface"
	/sbin/ifconfig lo 127.0.0.1 up
	if [ $? -ne 0 ]; then
		stat_fail
	else
		stat_done
	fi
fi

# If necessary, find md devices and manually assemble RAID arrays
if [ -f /etc/mdadm.conf -a "$(/bin/grep ^ARRAY /etc/mdadm.conf 2>/dev/null)" ]; then
	status "Activating RAID arrays" /sbin/mdadm --assemble --scan
fi

if [ "$USELVM" = "yes" -o "$USELVM" = "YES" ]; then
	if [ -x /sbin/lvm -a -d /sys/block ]; then
		# Kernel 2.6.x, LVM2 groups
		/sbin/modprobe -q dm-mod 2>/dev/null
		stat_busy "Activating LVM2 groups"
		/sbin/lvm vgchange --ignorelockingfailure -a y >/dev/null
		if [ $? -ne 0 ]; then
			stat_fail
		else
			stat_done
		fi
	fi
fi

# Set up non-root encrypted partition mappings
if [ -f /etc/crypttab -a -n "$(/bin/grep -v ^# /etc/crypttab | /bin/grep -v ^$)" ]; then
	/sbin/modprobe -q dm-mod 2>/dev/null
	stat_busy "Unlocking encrypted volumes:"
	csfailed=0
	# Arch cryptsetup packages traditionally contained the binaries
	#  /usr/sbin/cryptsetup
	#  /sbin/cryptsetup.static
	# By default, initscripts used the /sbin/cryptsetup.static.
	# Newer packages will only have /sbin/cryptsetup and no static binary
	# This ensures maximal compatibility with the old and new layout
	if [ -x /sbin/cryptsetup ]; then
		CS=/sbin/cryptsetup
	elif [ -x /usr/sbin/cryptsetup ]; then
		CS=/usr/sbin/cryptsetup
	else
		CS=/sbin/cryptsetup.static
	fi
	do_crypt() {
		if [ $# -ge 3 ]; then
			cname="$1"
			csrc="$2"
			cpass="$3"
			shift 3
			copts="$*"
			stat_append "${cname}.."
			# For some fun reason, the parameter ordering varies for
			# LUKS and non-LUKS devices.  Joy.
			if [ "${cpass}" = "SWAP" ]; then
				# This is DANGEROUS! The only possible safety check
				# is to not proceed in case we find a LUKS device
				# This may cause dataloss if it is not used carefully
				if $CS isLuks $csrc 2>/dev/null; then
					false
				else
					$CS -d /dev/urandom $copts create $cname $csrc >/dev/null
					if [ $? -eq 0 ]; then
						stat_append "creating swapspace.."
						/sbin/mkswap -f -L $cname /dev/mapper/$cname >/dev/null
					fi
				fi
			elif [ "${cpass}" = "ASK" ]; then
				printf "\nOpening '${cname}' volume:\n"

				if $CS isLuks $csrc 2>/dev/null; then
					$CS $copts luksOpen $csrc $cname < /dev/console
				else
					$CS $copts create $cname $csrc < /dev/console
				fi
			elif [ "${cpass:0:1}" != "/" ]; then
				if $CS isLuks $csrc 2>/dev/null; then
					echo "$cpass" | $CS $copts luksOpen $csrc $cname >/dev/null
				else
					echo "$cpass" | $CS $copts create $cname $csrc >/dev/null
				fi
			else
				if $CS isLuks $csrc 2>/dev/null; then
					$CS -d $cpass $copts luksOpen $csrc $cname >/dev/null
				else
					$CS -d $cpass $copts create $cname $csrc >/dev/null
				fi
			fi
			if [ $? -ne 0 ]; then
				csfailed=1
				stat_append "failed "
			else
				stat_append "ok "
			fi
		fi
	}
	while read line; do
		eval do_crypt "$line"
	done </etc/crypttab
	if [ $csfailed -eq 0 ]; then
		stat_done
	else
		stat_fail
	fi
	# Maybe someone has LVM on an encrypted block device
	if [ "$USELVM" = "yes" -o "$USELVM" = "YES" ]; then
		if [ -x /sbin/lvm -a -d /sys/block ]; then
			/sbin/lvm vgchange --ignorelockingfailure -a y >/dev/null
		fi
	fi
fi

status "Mounting Root Read-only" /bin/mount -n -o remount,ro /

FORCEFSCK=
[ -f /forcefsck ] && FORCEFSCK="-- -f"
NETFS="nonfs,nonfs4,nosmbfs,nocifs,nocodafs,noncpfs,nosysfs,noshfs,nofuse,nofuseblk,noglusterfs"

fsck_reboot() {
	echo "Automatic reboot in progress..."
	/bin/umount -a
	/bin/mount -n -o remount,ro /
	/sbin/reboot -f
	exit 0
}

if [ -x /sbin/fsck ]; then
	stat_busy "Checking Filesystems"
	FSCK_OUT=/dev/stdout
	FSCK_ERR=/dev/stdout
	FSCK_FD=
	run_hook sysinit_prefsck
	/sbin/fsck -A -T -C$FSCK_FD -a -t "$NETFS,noopts=_netdev" $FORCEFSCK >$FSCK_OUT 2>$FSCK_ERR
	fsckret=$?
	if [ ${fsckret} -gt 1 ]; then
		stat_fail
	fi
	run_hook sysinit_postfsck
	if [ $((${fsckret}&2)) -eq 2 ]; then
		echo
		echo "********************** REBOOT REQUIRED *********************"
		echo "*                                                          *"
		echo "* The system will be rebooted automatically in 15 seconds. *"
		echo "*                                                          *"
		echo "************************************************************"
		echo
		/bin/sleep 15
		fsck_reboot
	fi
	if [ ${fsckret} -gt 1 -a ${fsckret} -ne 32 ]; then
		echo
		echo "*****************  FILESYSTEM CHECK FAILED  ****************"
		echo "*                                                          *"
		echo "*  Please repair manually and reboot. Note that the root   *"
		echo "*  file system is currently mounted read-only. To remount  *"
		echo "*  it read-write type: mount -n -o remount,rw /            *"
		echo "*  When you exit the maintenance shell the system will     *"
		echo "*  reboot automatically.                                   *"
		echo "*                                                          *"
		echo "************************************************************"
		echo
		/sbin/sulogin -p
		fsck_reboot
	fi
	stat_done
fi

stat_busy "Mounting Local Filesystems"
/bin/mount -n -o remount,rw /
if [ -x /bin/findmnt -a -e /proc/self/mountinfo ]; then
	/bin/findmnt -rnu -o SOURCE,TARGET,FSTYPE,OPTIONS >| /etc/mtab
else
	cat /proc/mounts >| /etc/mtab
fi
run_hook sysinit_premount
# now mount all the local filesystems
/bin/mount -a -t $NETFS -O no_netdev
stat_done

status "Activating Swap" /sbin/swapon -a

stat_busy "Configuring System Clock"
if [ "$TIMEZONE" != "" -a -e "/usr/share/zoneinfo/$TIMEZONE" ]; then
	/bin/rm -f /etc/localtime
	/bin/cp "/usr/share/zoneinfo/$TIMEZONE" /etc/localtime
fi

clock_pid=""
if [ -n "$HWCLOCK_PARAMS" ]; then
	# This time, we set the clock for real. Use the adjustment file now that
	# /var will definitely be available, and then set the system clock once
	# the hardware clock has been adjusted accordingly. The backgrounding magic
	# is due to the fact that the second call to hwclock will almost always
	# take ~1 second because of the clock granularity, and we might as well
	# stay busy.
	(
	/sbin/hwclock --adjust
	/sbin/hwclock $HWCLOCK_PARAMS
	) &
	clock_pid=$!
fi
stat_done

RANDOM_SEED=/var/lib/misc/random-seed
if [ -f $RANDOM_SEED ]; then
	stat_busy "Initializing Random Seed"
	/bin/cat $RANDOM_SEED > /dev/urandom
	stat_done
fi

stat_busy "Removing Leftover Files"
/bin/rm -f /etc/nologin &>/dev/null
/bin/rm -f /etc/shutdownpid &>/dev/null
/bin/rm -f /var/lock/* &>/dev/null
/bin/rm -rf /tmp/* /tmp/.* &>/dev/null
/bin/rm -f /forcefsck &>/dev/null
(cd /var/run && /usr/bin/find . ! -type d -exec /bin/rm -f -- {} \; )
: >| /var/run/utmp
/bin/chmod 0664 /var/run/utmp
# Keep {x,k,g}dm happy with xorg
/bin/mkdir /tmp/.ICE-unix && /bin/chmod 1777 /tmp/.ICE-unix
/bin/mkdir /tmp/.X11-unix && /bin/chmod 1777 /tmp/.X11-unix
stat_done

#status "Updating Shared Library Links" /sbin/ldconfig

if [ "$HOSTNAME" != "" ]; then
	status "Setting Hostname: $HOSTNAME" /bin/hostname $HOSTNAME
fi

# Set the NIS domain name, if necessary
[ -f /etc/conf.d/nisdomainname ] && . /etc/conf.d/nisdomainname
if [ "$NISDOMAINNAME" != "" ]; then
	status "Setting NIS Domain Name: $NISDOMAINNAME" /bin/nisdomainname $NISDOMAINNAME
fi

status "Updating Module Dependencies" /sbin/depmod -A

# Flush old locale settings
: >| /etc/profile.d/locale.sh
/bin/chmod 755 /etc/profile.d/locale.sh
# Set user defined locale
[ -z "$LOCALE" ] && LOCALE="en_US"
stat_busy "Setting Locale: $LOCALE"
echo "export LANG=$LOCALE" >>/etc/profile.d/locale.sh
stat_done

if echo "$LOCALE" | /bin/grep -qi utf ; then
	stat_busy "Setting Consoles to UTF-8 mode"
	# UTF-8 consoles are default since 2.6.24 kernel
	# this code is needed not only for older kernels,
	# but also when user has set vt.default_utf8=0 but LOCALE is *.UTF-8.
	for i in /dev/tty[0-9]*; do
		/usr/bin/kbd_mode -u < ${i}
		printf "\033%%G" > ${i}
	done
	# the $CONSOLE check helps us avoid this when running scripts from cron
	echo 'if [ "$CONSOLE" = "" -a "$TERM" = "linux" -a -t 1 ]; then printf "\033%%G"; fi' >>/etc/profile.d/locale.sh
	stat_done
	[ -n "$KEYMAP" ] && status "Loading Keyboard Map: $KEYMAP" /bin/loadkeys -q -u $KEYMAP
else
	stat_busy "Setting Consoles to legacy mode"
	# make non-UTF-8 consoles work on 2.6.24 and newer kernels
	for i in /dev/tty[0-9]*; do
		/usr/bin/kbd_mode -a < ${i}
		printf "\033%%@" > ${i}
	done
	# the $CONSOLE check helps us avoid this when running scripts from cron
	echo 'if [ "$CONSOLE" = "" -a "$TERM" = "linux" -a -t 1 ]; then printf "\033%%@"; fi' >>/etc/profile.d/locale.sh
	stat_done
	[ -n "$KEYMAP" ] && status "Loading Keyboard Map: $KEYMAP" /bin/loadkeys -q $KEYMAP
fi

# Set console font if required
set_consolefont

# Adding persistent network/cdrom generated rules
if [ -f "/dev/.udev/tmp-rules--70-persistent-cd.rules" ]; then
	stat_busy "Adding persistent cdrom udev rules"
	/bin/cat /dev/.udev/tmp-rules--70-persistent-cd.rules >> /etc/udev/rules.d/70-persistent-cd.rules
	stat_done
fi
if [ -f "/dev/.udev/tmp-rules--70-persistent-net.rules" ]; then
	stat_busy "Adding persistent network udev rules"
	/bin/cat /dev/.udev/tmp-rules--70-persistent-net.rules >> /etc/udev/rules.d/70-persistent-net.rules
	stat_done
fi

/bin/dmesg >| /var/log/dmesg.log

# final hwclock setting needs to be done at this point
if [ -n "$clock_pid" ]; then
	wait $clock_pid
fi

run_hook sysinit_end

# End of file
# vim: set ts=2 sw=2 noet:

```

---

### Post by pavankumarl73 on 2010-12-07
Yeah as I mentioned above in one of the posts it requires kernel patching. I'm not an experienced user. I would rather like to stay with newbie attitude. And I got my terminal colourful by editing .bashrc file. So thanks for the help. I'll try to patch it when I acquire sufficient knowledge.

   Thank you

---

### Post by mcduck on 2010-12-07
Actually it shouldn't require anything more than changing a few lines in the responsible config file (definitely no kernel patching required), at least that's how I did it in previous Ubuntu versions.

But like I said, the startup procedure has changed a bit since then, and as I'm happily using the graphical boot I can't really test how it would be done in 10.10.

edit:
If you want to try it, this *should* work (I take no responsibility in case it doesn't work or things go horribly wrong :D):

You need to edit */etc/lsb-base-logging.sh*
Find the "echo '[ ok ]" -line in the *log_end_msg()* (should be line 112), and replace it with following lines:
```

printf '[ '
$TPUT setaf 2  # green
printf ok
$TPUT op  # normal
echo ' ]'

```

Save the file, and the "ok" messages during boot should now be green. (error messages should already have colors by default).

edit2: works fine on my 10.04 virtual machine, so it should work for 10.10 as well.

---

### Post by pavankumarl73 on 2010-12-07
> **mcduck said:**
> Actually it shouldn't require anything more than changing a few lines in the responsible config file (definitely no kernel patching required), at least that's how I did it in previous Ubuntu versions.

But like I said, the startup procedure has changed a bit since then, and as I'm happily using the graphical boot I can't really test how it would be done in 10.10.

Actually plymouth isn't working for me. I tried really a wide range of solutions. So finally I gave up and disabled plymouth and as it was looking traditional I thought of giving up some colors to it. Anyhow I'm happy with what I have now

---

