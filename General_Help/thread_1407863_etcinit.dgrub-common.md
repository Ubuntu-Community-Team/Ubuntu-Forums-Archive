---
title: "/etc/init.d/grub-common"
date: 2010-02-15
forum: General Help
---

### Post by gfuggs on 2010-02-15
I would greatly appreciate it if someone could post the contents of this file.  I get errors every time I install a package or update, and it seems to be angry at this file; rightfully so I guess, as it looks to be filled with jibber-jabber.  I don't know what that crap is, but it doesn't look to be helping things.  


jim@king:~$ cat /etc/init.d/grub-common 
 &#65533;@&#65533;&#65533;	
enable idindex &#65533;&#65533;&#65533;d<3>wait_handshake(): Timeout waiting for DSP
<3>get_firmware(): Firmware not available (%d)
<3>Failed to read serial number
<3>cannot allocate the comm page
%s rev.%d (DSP%s) at 0x%lx irq %in&#65533;8n&#65533;8n&#65533;8n&#65533;n&#65533;n&#65533;n&#65533;8n&#65533;8n&#65533;8n&#65533;8n&#65533;n&#65533;8ea/%s<4>Firmware not found !
Indigo IOx<3>malloc_pages err=%d
PCMsnd_indigoiox<3>cannot get memory region
<3>cannot grab irq
&chip->mode_mutex5636156301<3>new pcm error %d
<6>Card registered: %s
<3>new control error jim@king:~$

---

### Post by Iowan on 2010-02-15
Here's the one from my Karmic machine.

---

### Post by Detonate on 2010-02-15
This is what the file looks like on my install, Grub2 on Karmic 64 bit.  I seems your file got corrupted, maybe you can just cut and past this in the file.

geek@karmic64:~$ cat /etc/init.d/grub-common
#! /bin/sh
### BEGIN INIT INFO
# Provides:          grub-common
# Required-Start:    $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Record successful boot for GRUB
# Description:       GRUB displays the boot menu at the next boot if it
#                    believes that the previous boot failed. This script
#                    informs it that the system booted successfully.
### END INIT INFO

which grub-editenv >/dev/null 2>&1 || exit 0

# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

case $1 in
    start|restart|force-reload)
	[ "$VERBOSE" != no ] && log_action_msg "Recording successful boot for GRUB"
	[ -s /boot/grub/grubenv ] || rm -f /boot/grub/grubenv
	mkdir -p /boot/grub
	grub-editenv /boot/grub/grubenv unset recordfail
	[ "$VERBOSE" != no ] && log_end_msg $?
	;;
    stop)
	;;
    status)
	exit 0
	;;
    *)
	echo "Usage: $0 {start|stop|status|restart|force-reload}" >&2
	exit 3
	;;
esac

exit 0

---

### Post by cknight725 on 2010-02-16
Same issue here -- though the contents of my grub-common seemed to be something from another Samba config file.  

I copied and pasted Detonate's contents and its happy now.

---

### Post by gfuggs on 2010-02-16
Excellent, I replaced the junk in my grub-common with what Iowan and Detonate posted and things are back to working properly.

Thanks all.

---

