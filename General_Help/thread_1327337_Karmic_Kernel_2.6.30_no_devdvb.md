---
title: "Karmic Kernel 2.6.30 no /dev/dvb/"
date: 2009-11-15
forum: General Help
---

### Post by jarlethorsen on 2009-11-15
I have successfully been running ubuntu 8.10 for a long time. Now I have upgraded to 9.10 only to find that one of the tools I am depending on does not work with kernel 2.6.31.

So I install kernel 2.6.30 by installing the following packages (one after the other):
 [http://launchpadlibrarian.net/27828446/linux-headers-2.6.30-9_2.6.30-9.10_all.deb](http://launchpadlibrarian.net/27828446/linux-headers-2.6.30-9_2.6.30-9.10_all.deb)
[http://launchpadlibrarian.net/27828448/linux-headers-2.6.30-9-generic_2.6.30-9.10_i386.deb](http://launchpadlibrarian.net/27828448/linux-headers-2.6.30-9-generic_2.6.30-9.10_i386.deb)
[http://launchpadlibrarian.net/27828447/linux-image-2.6.30-9-generic_2.6.30-9.10_i386.deb](http://launchpadlibrarian.net/27828447/linux-image-2.6.30-9-generic_2.6.30-9.10_i386.deb)

This kernel boots fine, but for some reason it does not create any /dev/dvb/* devices. (They are all put under /dev/*)

How can I get kernel 2.6.30 to create the devices correcly???

This problem is really bugging me as at keeps me from running my mythtv system which is the centerpiece of our home!

This problem seems to be related to:
[http://ubuntuforums.org/showthread.php?t=1306715&highlight=%2Fdev%2Fdvb](http://ubuntuforums.org/showthread.php?t=1306715&highlight=%2Fdev%2Fdvb)
[http://ubuntuforums.org/showthread.php?t=1307814&highlight=%2Fdev%2Fdvb](http://ubuntuforums.org/showthread.php?t=1307814&highlight=%2Fdev%2Fdvb)

---

### Post by DeMus on 2009-11-15
> **jarlethorsen said:**
> I have successfully been running ubuntu 8.10 for a long time. Now I have upgraded to 9.10 only to find that one of the tools I am depending on does not work with kernel 2.6.31.

So I install kernel 2.6.30 by installing the following packages (one after the other):
 [http://launchpadlibrarian.net/27828446/linux-headers-2.6.30-9_2.6.30-9.10_all.deb](http://launchpadlibrarian.net/27828446/linux-headers-2.6.30-9_2.6.30-9.10_all.deb)
[http://launchpadlibrarian.net/27828448/linux-headers-2.6.30-9-generic_2.6.30-9.10_i386.deb](http://launchpadlibrarian.net/27828448/linux-headers-2.6.30-9-generic_2.6.30-9.10_i386.deb)
[http://launchpadlibrarian.net/27828447/linux-image-2.6.30-9-generic_2.6.30-9.10_i386.deb](http://launchpadlibrarian.net/27828447/linux-image-2.6.30-9-generic_2.6.30-9.10_i386.deb)

This kernel boots fine, but for some reason it does not create any /dev/dvb/* devices. (They are all put under /dev/*)

How can I get kernel 2.6.30 to create the devices correcly???

This problem is really bugging me as at keeps me from running my mythtv system which is the centerpiece of our home!

This problem seems to be related to:
[http://ubuntuforums.org/showthread.php?t=1306715&highlight=%2Fdev%2Fdvb](http://ubuntuforums.org/showthread.php?t=1306715&highlight=%2Fdev%2Fdvb)
[http://ubuntuforums.org/showthread.php?t=1307814&highlight=%2Fdev%2Fdvb](http://ubuntuforums.org/showthread.php?t=1307814&highlight=%2Fdev%2Fdvb)

Install Jaunty instead, then install the 2.6.30 kernel. I also did that and it works great.
In Karmic it is difficult to step back to an older kernel.

---

### Post by jarlethorsen on 2009-11-15
I have a big system with several disk running raid, so wiping the disks and re-install would require a lot of work for me. This will be the LAST resort.

---

### Post by matthewbpt on 2009-11-15
What is the tool thats missing in 2.6.31?

---

### Post by jarlethorsen on 2009-11-15
> **matthewbpt said:**
> What is the tool thats missing in 2.6.31?

opensasc-ng will not work with this kernel: [https://opensvn.csie.org/traccgi/opensascng/ticket/58](https://opensvn.csie.org/traccgi/opensascng/ticket/58)

---

### Post by jarlethorsen on 2009-11-16
The problem was solved by creating a /etc/udev/rules.d/50-udev.rules containing:
> 
# There are a number of modifiers that are allowed to be used in some of the
# fields.  See the udev man page for a full description of them.
#
# default is OWNER="root" GROUP="root", MODE="0600"
#

KERNEL=="*", OWNER="root" GROUP="root", MODE="0600"

# all block devices
SUBSYSTEM=="block",		GROUP="disk", MODE="0640"
KERNEL=="root",			GROUP="disk", MODE="0640"

# console devices
KERNEL=="tty",			NAME="%k", GROUP="tty", MODE="0666", OPTIONS="last_rule"
KERNEL=="console",              NAME="%k", MODE="0600", OPTIONS="last_rule"
KERNEL=="tty[0-9]*",            NAME="%k", GROUP="tty", MODE="0660", OPTIONS="last_rule"
KERNEL=="vc/[0-9]*",		NAME="%k", GROUP="tty", MODE="0660", OPTIONS="last_rule"

# pty devices
#  Set this to 0660 if you only want users belonging to tty group
#  to be able to allocate PTYs
KERNEL=="ptmx",                 NAME="%k", GROUP="tty", MODE="666", OPTIONS="last_rule"
KERNEL=="pty[pqrstuvwxyzabcdef][0123456789abcdef]", NAME="%k", GROUP="tty", MODE="660", OPTIONS="last_rule"
KERNEL=="tty[pqrstuvwxyzabcdef][0123456789abcdef]", NAME="%k", GROUP="tty", MODE="660", OPTIONS="last_rule"
KERNEL=="pty/m*",		NAME="%k", GROUP="tty", MODE="0660", OPTIONS="last_rule"

# serial+dialup devices
KERNEL=="ippp*",		NAME="%k", MODE="0660"
KERNEL=="isdn*",		NAME="%k", MODE="0660"
KERNEL=="isdnctrl*",		NAME="%k", MODE="0660"
KERNEL=="capi",                 NAME="capi20", GROUP="uucp", MODE="0660"
KERNEL=="capi*",                NAME="capi/%n", GROUP="uucp", MODE="0660"
KERNEL=="dcbri*",		NAME="%k", MODE="0660"
KERNEL=="ircomm*",		NAME="%k", GROUP="uucp", MODE="0660"
KERNEL=="tts/[0-9]*",		NAME="%k", GROUP="uucp", MODE="0660"
KERNEL=="tts/USB[0-9]*",	NAME="%k", GROUP="uucp", MODE="0660"
KERNEL=="tty[A-Z]*",            NAME="%k", GROUP="uucp", MODE="0660"
KERNEL=="pppox*",               NAME="%k", GROUP="uucp", MODE="0660"
KERNEL=="ircomm*",              NAME="%k", GROUP="uucp", MODE="0660"
KERNEL=="modems/mwave*",        NAME="%k", GROUP="uucp", MODE="0660"
KERNEL=="hvc*",                 NAME="%k", GROUP="uucp", MODE="0660"
KERNEL=="hvsi*",                NAME="%k", GROUP="uucp", MODE="0660"
KERNEL=="iseries/vtty*",        NAME="%k", GROUP="uucp", MODE="0660"
KERNEL=="ttyUSB*", SYSFS{product}=="Palm Handheld*", SYMLINK+="pilot", GROUP="uucp", MODE="0660"
KERNEL=="ttyUSB*", SYSFS{product}=="palmOne Handheld*", SYMLINK+="pilot", GROUP="uucp", MODE="0660"
KERNEL=="ttyUSB*", SYSFS{product}=="Handspring Visor*", SYMLINK+="pilot", GROUP="uucp", MODE="0660"

# vc devices
KERNEL=="vcs",			NAME="%k", OWNER="vcsa", GROUP="tty", OPTIONS="last_rule"
KERNEL=="vcs[0-9]*",		NAME="%k", OWNER="vcsa", GROUP="tty", OPTIONS="last_rule"
KERNEL=="vcsa",			NAME="%k", OWNER="vcsa", GROUP="tty", OPTIONS="last_rule"
KERNEL=="vcsa[0-9]*",		NAME="%k", OWNER="vcsa", GROUP="tty", OPTIONS="last_rule"
KERNEL=="vcc/*",		NAME="%k", OWNER="vcsa", GROUP="tty", OPTIONS="last_rule"

# memory devices
KERNEL=="random",		MODE="0666", OPTIONS="last_rule"
KERNEL=="urandom",		MODE="0444", OPTIONS="last_rule"
KERNEL=="mem",			GROUP="kmem", MODE="0640", OPTIONS="last_rule"
KERNEL=="kmem",			GROUP="kmem", MODE="0640", OPTIONS="last_rule"
KERNEL=="port",			GROUP="kmem", MODE="0640", OPTIONS="last_rule"
KERNEL=="full",			MODE="0666", OPTIONS="last_rule"
KERNEL=="null",			MODE="0666", OPTIONS="last_rule"
KERNEL=="zero",			MODE="0666", OPTIONS="last_rule"
# 183 = /dev/hwrng        Generic random number generator
KERNEL=="hw_random",            NAME="hwrng", SYMLINK+="%k"

# misc devices
KERNEL=="nvram",		MODE="0660"
KERNEL=="rtc",			MODE="0644"

# pnp devices
ACTION=="add", SUBSYSTEM=="pnp", RUN+="/bin/sh -c 'while read id; do /lib/udev/modprobe pnp:d$$id; done < /sys/$devpath/id'"

# floppy devices
KERNEL=="fd[01]*",		GROUP="floppy", MODE="0660"
# fix floppy devices
KERNEL=="nvram", ACTION=="add", RUN+="load_floppy_module.sh"
KERNEL=="fd[0-9]*", ACTION=="add", SYSFS{device/cmos}=="*", RUN+="create_floppy_devices -c -t $sysfs{device/cmos} -m %M /dev/%k"
KERNEL=="fd[0-9]*", ACTION=="remove", RUN+="/bin/sh -c 'rm -f /dev/%k*'"

# audio devices
KERNEL=="dsp*",			MODE="0660"
KERNEL=="audio*",		MODE="0660"
KERNEL=="midi*",		MODE="0660"
KERNEL=="mixer*",		MODE="0660"
KERNEL=="sequencer*",		MODE="0660"
KERNEL=="sound/*",		MODE="0660"
KERNEL=="snd/*",		MODE="0660"
KERNEL=="beep",			MODE="0660"
KERNEL=="admm*",		MODE="0660"
KERNEL=="adsp*",		MODE="0660"
KERNEL=="aload*",		MODE="0660"
KERNEL=="amidi*",		MODE="0660"
KERNEL=="dmfm*",		MODE="0660"
KERNEL=="dmmidi*",		MODE="0660"
KERNEL=="sndstat",		MODE="0660"

# lp devices
KERNEL=="lp*",			GROUP="lp", MODE="0660"
KERNEL=="parport*",		GROUP="lp", MODE="0660"
KERNEL=="irlpt*",		GROUP="lp", MODE="0660"
KERNEL=="usblp*",		GROUP="lp", MODE="0660"
KERNEL=="usb/lp*",		GROUP="lp", MODE="0660"

# tape devices
SUBSYSTEM=="ide", SYSFS{media}=="tape", ACTION=="add", \
		RUN+="modprobe $env{UDEV_MODPROBE_DBG} ide-scsi idescsi_nocd=1"
KERNEL=="ht*",			GROUP="disk", MODE="0660"
KERNEL=="nht*",			GROUP="disk", MODE="0660"
KERNEL=="pt[0-9]*",		GROUP="disk", MODE="0660"
KERNEL=="npt*",			GROUP="disk", MODE="0660"
KERNEL=="st*",			GROUP="disk", MODE="0660"
KERNEL=="nst*",			GROUP="disk", MODE="0660"
KERNEL=="osst*",		GROUP="disk", MODE="0660"
KERNEL=="nosst*",		GROUP="disk", MODE="0660"

# diskonkey devices
KERNEL=="diskonkey*",		GROUP="disk", MODE="0640"

# rem_ide devices
KERNEL=="microdrive*",		GROUP="disk", MODE="0640"

# kbd devices
KERNEL=="kbd",			MODE="0644"

# joystick devices
KERNEL=="js[0-9]*",		MODE="0644"
KERNEL=="djs[0-9]*",		MODE="0644"

# v4l devices
KERNEL=="video*",		MODE="0660"
KERNEL=="radio*",		MODE="0660"
KERNEL=="winradio*",		MODE="0660"
KERNEL=="vtx*",			MODE="0660"
KERNEL=="vbi*",			MODE="0660"
KERNEL=="video/*",		MODE="0660"
KERNEL=="vttuner",		MODE="0660"
KERNEL=="v4l/*",		MODE="0660"

# input devices
KERNEL=="input/*",		MODE="0660"

# gpm devices
KERNEL=="gpmctl",		MODE="0700"

# dri devices
KERNEL=="nvidia*",		MODE="0660"
KERNEL=="3dfx*",		MODE="0660"
KERNEL=="card[0-9]*",		NAME="dri/%k", MODE="0666"

# usb devices
KERNEL=="usb/dabusb*",		MODE="0660"
KERNEL=="usb/mdc800*",		MODE="0660"
KERNEL=="usb/rio500",		MODE="0660"

# s390 devices
KERNEL=="z90crypt",		MODE="0666"
KERNEL=="slram[0-9]*", 		SYMLINK+="xpram%n"

# DVB
KERNEL=="dvb",			MODE="0660"
SUBSYSTEM=="dvb", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter%%i/%%s $${K%%%%.*} $${K#*.}'", \
	NAME="%c", MODE="0660"

# alsa devices
KERNEL=="controlC[0-9]*",	NAME="snd/%k"
KERNEL=="hw[CD0-9]*",		NAME="snd/%k"
KERNEL=="pcm[CD0-9cp]*",	NAME="snd/%k"
KERNEL=="midi[CD0-9]*",		NAME="snd/%k"
KERNEL=="timer",		NAME="snd/%k"
KERNEL=="seq",			NAME="snd/%k"

# input devices
KERNEL=="mice",			NAME="input/%k"
KERNEL=="mouse*",		NAME="input/%k"

KERNEL=="event*", SYSFS{idVendor}=="03f0", SYSFS{device/interface}=="Virtual Mouse", SYSFS{device/bInterfaceProtocol}=="02", NAME="input/%k", SYMLINK+="input/hp_ilo_mouse"

KERNEL=="event*",		NAME="input/%k"
KERNEL=="js*",			NAME="input/%k", SYMLINK+="%k"
KERNEL=="ts*",			NAME="input/%k"

# IEEE1394 (firewire) devices (must be before raw devices below)
SUBSYSTEM=="ieee1394_protocol", KERNEL=="raw1394",      	NAME="%k"
KERNEL=="dv1394*",      	NAME="dv1394/%n"
KERNEL=="video1394*",   	NAME="video1394/%n"

KERNEL=="raw[0-9]*",		NAME="raw/%k"

KERNEL=="lp[0-9]*",		SYMLINK+="par%n"
BUS=="usb", KERNEL=="lp[0-9]*",	NAME="usb/%k"

KERNEL=="microcode",		NAME="cpu/%k"
KERNEL=="msr[0-9]*",     	NAME="cpu/%n/msr"
KERNEL=="cpu[0-9]*",     	NAME="cpu/%n/cpuid"

KERNEL=="ram1",			SYMLINK+="ram"
KERNEL=="video0",		SYMLINK+="video"
KERNEL=="radio0",		SYMLINK+="radio"
KERNEL=="audio0",		SYMLINK+="audio"
KERNEL=="dsp0",			SYMLINK+="dsp"
KERNEL=="fb0",			SYMLINK+="fb"
KERNEL=="qft0",			SYMLINK+="ftape"
KERNEL=="isdnctrl0",		SYMLINK+="isdnctrl"
KERNEL=="mixer0",		SYMLINK+="mixer"
KERNEL=="ram0",			SYMLINK+="ramdisk"
KERNEL=="sbpcd0",		SYMLINK+="sbpcd"
KERNEL=="radio0",		SYMLINK+="radio"
KERNEL=="tty0",			SYMLINK+="systty"
KERNEL=="vbi0",			SYMLINK+="vbi"
KERNEL=="null",			SYMLINK+="XOR"

KERNEL=="tun",			NAME="net/%k"

KERNEL=="device-mapper",	NAME="mapper/control"

# old compat symlinks with enumeration
KERNEL=="sr[0-9]*",		SYMLINK+="cdrom cdrom-%k"
KERNEL=="scd[0-9]*",		SYMLINK+="cdrom cdrom-%k"
KERNEL=="pcd[0-9]*",		SYMLINK+="cdrom cdrom-%k"
KERNEL=="fd[0-9]*",		SYMLINK+="floppy floppy-%k"

# Section for zaptel device
KERNEL=="zapctl",     		NAME="zap/ctl"
KERNEL=="zaptimer",   		NAME="zap/timer"
KERNEL=="zapchannel", 		NAME="zap/channel"
KERNEL=="zappseudo",  		NAME="zap/pseudo"
KERNEL=="zap[0-9]*",  		NAME="zap/%n"

KERNEL=="pktcdvd", NAME="%k/control"

KERNEL=="hd[a-z]", BUS=="ide", SYSFS{removable}=="1", \
	SYSFS{device/media}=="floppy", \
	SYMLINK+="floppy floppy-%k", OPTIONS+="ignore_remove, all_partitions"

KERNEL=="hd[a-z]", BUS=="ide", SYSFS{removable}=="1", SYSFS{device/media}=="cdrom", SYMLINK+="cdrom cdrom-%k"

KERNEL=="hd[a-z]", BUS=="ide", SYSFS{removable}=="1", PROGRAM=="check-cdrom.sh %k DVD", SYMLINK+="dvd dvd-%k"
KERNEL=="sr[0-9]*", BUS=="scsi", PROGRAM=="check-cdrom.sh %k DVD", SYMLINK+="dvd dvd-%k"

KERNEL=="hd[a-z]", BUS=="ide", SYSFS{removable}=="1", PROGRAM=="check-cdrom.sh %k CD-R", SYMLINK+="cdwriter cdwriter-%k cdrw cdrw-%k"
KERNEL=="sr[0-9]*", BUS=="scsi", PROGRAM=="check-cdrom.sh %k CD-R", SYMLINK+="cdwriter cdwriter-%k cdrw cdrw-%k"

KERNEL=="hd[a-z]", BUS=="ide", SYSFS{removable}=="1", PROGRAM="check-cdrom.sh %k DVD-R", SYMLINK+="dvdwriter dvdwriter-%k dvdrw dvdrw-%k"
KERNEL=="sr[0-9]*", BUS=="scsi", PROGRAM=="check-cdrom.sh %k DVD-R", SYMLINK+="dvdwriter dvdwriter-%k dvdrw dvdrw-%k"

# rename sr* to scd*
KERNEL=="sr[0-9]*", BUS=="scsi", NAME="scd%n"
KERNEL=="hd*[0-9]", BUS=="ide", SYSFS{../removable}=="1", \
	OPTIONS+="ignore_remove"


#######################################
# Persistent block device stuff - begin
#######################################
# persistent disk links: /dev/disk/{by-id,by-uuid,by-label,by-path}
# scheme based on "Linux persistent device names", 2004, Hannes Reinecke <hare@suse.de>

ACTION!="add", GOTO="persistent_end"

KERNEL=="dm-[0-9]*", GOTO="persistent_end"

KERNEL=="nst[0-9]*", IMPORT{parent}=="ID_*"
KERNEL=="nst[0-9]*", SUBSYSTEM=="scsi_tape", ENV{ID_SERIAL}=="", IMPORT{program}="scsi_id -u -g -x -s %p -d $tempnode"
KERNEL=="nst[0-9]*", SUBSYSTEM=="scsi_tape", ENV{ID_SERIAL}=="", IMPORT{program}="scsi_id -u -g -x -a -s %p -d $tempnode"
KERNEL=="nst[0-9]*", SUBSYSTEM=="scsi_tape", ENV{ID_SERIAL}=="?*", SYMLINK+="tape/by-id/$env{ID_BUS}-$env{ID_SERIAL}-nst"

# type 8 devices are "Medium Changers"
KERNEL=="sg*", IMPORT{parent}=="ID_*"
KERNEL=="sg*", SUBSYSTEM=="scsi_generic", SYSFS{type}=="8", ENV{ID_SERIAL}=="", IMPORT{program}="scsi_id -g -u -x -s %p -d $tempnode"
KERNEL=="sg*", SUBSYSTEM=="scsi_generic", SYSFS{type}=="8", ENV{ID_SERIAL}=="", IMPORT{program}="scsi_id -g -u -x -a -s %p -d $tempnode"
KERNEL=="sg*", SUBSYSTEM=="scsi_generic", SYSFS{type}=="8", ENV{ID_SERIAL}=="?*", SYMLINK+="tape/by-id/$env{ID_BUS}-$env{ID_SERIAL}"

SUBSYSTEM!="block", GOTO="persistent_end"

# skip rules for inappropriate block devices
KERNEL=="ram*|loop*|fd*|nbd*|gnbd*", GOTO="persistent_end"

# never access removable ide devices, the drivers are causing event loops on open()
BUS=="ide", DRIVER!="ide-cdrom", SYSFS{removable}=="1",	GOTO="persistent_end"
BUS=="ide", KERNEL=="hd*[0-9]", SYSFS{../removable}=="1", GOTO="persistent_end"

# by-id (hardware serial number)
KERNEL=="hd*[!0-9]", IMPORT{program}="/lib/udev/ata_id --export $tempnode"
KERNEL=="hd*[!0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/ata-$env{ID_MODEL}_$env{ID_SERIAL}"
KERNEL=="hd*[0-9]", IMPORT{parent}=="ID_*", SYMLINK+="disk/by-id/ata-$env{ID_MODEL}_$env{ID_SERIAL}-part%n"

KERNEL=="sd*[!0-9]|sr*", SYSFS{ieee1394_id}=="*", ENV{ID_SERIAL}="$sysfs{ieee1394_id}", ENV{ID_BUS}="ieee1394"
KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}=="", IMPORT{program}="/lib/udev/usb_id -x"
KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}=="", IMPORT{program}="/lib/udev/scsi_id -g -x -s %p -d $tempnode"
KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}=="", IMPORT{program}="/lib/udev/scsi_id -g -x -a -s %p -d $tempnode"
KERNEL=="dasd*[!0-9]", IMPORT{program}="/lib/udev/dasd_id --export $tempnode"
KERNEL=="nst[0-9]*|st*|sd*[!0-9]|sr*|dasd*[!0-9]|cciss?c", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/$env{ID_BUS}-$env{ID_SERIAL}"

# for partitions import parent information
KERNEL=="sd*[0-9]|dasd*[0-9]", IMPORT{parent}=="ID_*"
KERNEL=="cciss?c[0-9]d[0-9]", ENV{ID_SERIAL}!="?*", IMPORT{program}="scsi_id -g -x -s %p -d $tempnode", ENV{ID_BUS}="cciss"
KERNEL=="cciss?c[0-9]d[0-9]", ENV{ID_SERIAL}!="?*", IMPORT{program}="scsi_id -g -x -a -s %p -d $tempnode", ENV{ID_BUS}="cciss"
KERNEL=="sd*[0-9]|dasd*[0-9]|cciss*p[0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/$env{ID_BUS}-$env{ID_SERIAL}-part%n"

# by-path (shortest physical path)
KERNEL=="*[!0-9]|sr*", ENV{ID_TYPE}=="?*", IMPORT{program}="/lib/udev/path_id %p", SYMLINK+="disk/by-path/$env{ID_PATH}"
KERNEL=="st*", IMPORT{program}="path_id %p", SYMLINK+="tape/by-path/$env{ID_PATH}"
KERNEL=="sr*|st*", GOTO="persistent_end"
KERNEL=="*[0-9]", IMPORT{parent}=="ID_*"
KERNEL=="*[0-9]", ENV{ID_PATH}=="?*", SYMLINK+="disk/by-path/$env{ID_PATH}-part%n"

# by-label/by-uuid (filesystem properties)
KERNEL=="*[!0-9]", SYSFS{removable}=="1", GOTO="persistent_end"
IMPORT{program}="/lib/udev/vol_id --export $tempnode"
ENV{ID_FS_UUID}=="?*", SYMLINK+="disk/by-uuid/$env{ID_FS_UUID}"
ENV{ID_FS_LABEL_SAFE}=="?*", SYMLINK+="disk/by-label/$env{ID_FS_LABEL_SAFE}"

# BIOS Enhanced Disk Device
KERNEL=="*[!0-9]", IMPORT{program}="/lib/udev/edd_id --export $tempnode"
KERNEL=="*[!0-9]", ENV{ID_EDD}=="?*", SYMLINK+="disk/by-id/edd-$env{ID_EDD}"
KERNEL=="*[0-9]", ENV{ID_EDD}=="?*", SYMLINK+="disk/by-id/edd-$env{ID_EDD}-part%n"

LABEL="persistent_end"

#####################################
# Persistent block device stuff - end
#####################################


ACTION=="add", SUBSYSTEM=="usb_device", \
	PROGRAM="/bin/sh -c 'K=%k; K=$${K#usbdev}; printf bus/usb/%%03i/%%03i $${K%%%%.*} $${K#*.}'", \
	NAME="%c", MODE="0644"

ACTION=="add", SUBSYSTEM=="?*", ENV{MODALIAS}=="?*", RUN+="modprobe $env{UDEV_MODPROBE_DBG} $env{MODALIAS}"

ACTION=="add", SUBSYSTEM=="pcmcia", ENV{MODALIAS}=="?*", RUN+="/bin/sh -c 'echo 1 > /sys/$DEVPATH/allow_func_id_match'"

# sd:           0 TYPE_DISK, 7 TYPE_MOD, 14 TYPE_RBC
# sr:           4 TYPE_WORM, 5 TYPE_ROM
# st/osst:      1 TYPE_TAPE
# sg: 		8 changer, [36] scanner
ACTION=="add", SUBSYSTEM=="scsi" , SYSFS{type}=="0|7|14", \
	RUN+="/bin/sh -c 'echo 60 > /sys$$DEVPATH/timeout'"
ACTION=="add", SUBSYSTEM=="scsi" , SYSFS{type}=="1", \
	RUN+="/bin/sh -c 'echo 900 > /sys$$DEVPATH/timeout'"


ACTION=="add", SUBSYSTEM=="scsi_device"	RUN+="modprobe sg"
ACTION=="add", SUBSYSTEM=="scsi_device", SYSFS{type}=="0|7|14", \
	RUN+="modprobe sd_mod"
ACTION=="add", SUBSYSTEM=="scsi_device", SYSFS{type}=="[45]", \
	RUN+="modprobe sr_mod"

ACTION=="add", KERNEL=="sg[0-9]*", BUS=="scsi", SYSFS{type}=="[36]", \
	SYMLINK+="scanner scanner-%k", MODE="0660"

ACTION=="add", KERNEL=="sg[0-9]*", BUS=="scsi", SYSFS{type}=="8", \
	SYMLINK+="changer changer-%k", MODE="0660", GROUP="disk"

ACTION=="add", SUBSYSTEM=="scsi_device", SYSFS{type}=="1", SYSFS{device/vendor}=="On[sS]tream", \
	SYSFS{model}!="ADR*", RUN+="modprobe osst"
ACTION=="add", SUBSYSTEM=="scsi_device", SYSFS{type}=="1", SYSFS{device/vendor}=="On[sS]tream", \
	SYSFS{model}=="ADR*", RUN+="modprobe st"
ACTION=="add", SUBSYSTEM=="scsi_device", SYSFS{type}=="1", SYSFS{device/vendor}!="On[sS]tream", \
	RUN+="modprobe st"

# mmc block devices
ACTION=="add", SUBSYSTEM=="mmc", RUN+="modprobe mmc_block"

RUN+="socket:/org/kernel/udev/monitor"




This also solved the problem with missing audio.

---

### Post by Jose Catre-Vandis on 2009-12-30
Also appears to resolve:

[http://ubuntuforums.org/showthread.php?t=1316032](http://ubuntuforums.org/showthread.php?t=1316032)

---

### Post by deepee_oz on 2010-01-15
I have eight USB devices on my Karmic 32bit test system. 
I've created a /etc/udev/rules.d/50-udev.rules exactly as above.
However, when I reboot and run lsusb I only see one device.
When I remove or rename 50-udev.rules, reboot and run lsusb again I can see all my devices.

Something I'm missing?

---

### Post by aschix on 2010-01-21
I'm running a fresh 9.10 system with 2.6.31 kernel. I added the rule described above, but just got the effect that there are no devices shown by lsusb, and no entries for /dev/dvb created. 
What would I have to modify?
Thanks,
Daniel

---

