---
title: "Hardy won't Boot"
date: 2010-08-01
forum: General Help
---

### Post by calvert888 on 2010-08-01
So, I've been running Ubuntu for a few years now and this is the first time in a while that I've been really stumped. My power went out earlier today. Of course my Ubuntu box was on, so it had a hard shutdown. When it booted back up upon power coming back on, it went to the normal Ubuntu startup screen with the orange progress bar, but stopped about halfway through. It then goes to a black screen, with a continuous stream of y's scrolling down the left of the screen. Like this:

```
y
y
y
y
y
y
y
y
y
y
y
y
y
```

So, I try selecting other sessions (Ctrl-Alt-F1, F2, etc) and only get anything from F1, where it says "Starting Up... <cr> Loading, please wait..."

I then reboot into recovery mode and get the same continuous y's. However, now when I press Ctrl-Alt-Del, I get the Recovery Menu, which lets me into a root shell.

Below is my fdisk -l output. Any ideas?


```
Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4fa84fa8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7475    60042906    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb051badd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24315   195310206   83  Linux
/dev/sdb2           24316       24502     1502077+  82  Linux swap / Solaris
/dev/sdb3   *       24503       28326    30716280    7  HPFS/NTFS
/dev/sdb4           28327       34706    51247350    b  W95 FAT32
```

---

### Post by MaxIBoy on 2010-08-01
Well, if you have access to a root shell, please post the output of this command:
```
cd /etc/init.d
grep yes *
```
Because it looks like one of the initscripts containing the "yes" command got somehow corrupted. (At least, that is my first guess, I might be wrong.)

---

### Post by calvert888 on 2010-08-01
Here it is:

> bootmisc.sh:[ "$DELAYLOGIN" ] || DELAYLOGIN=yes
brltty:	sed -i -e 's/^RUN_BRLTTY=.*/RUN_BRLTTY=yes/' /etc/default/brltty
brltty:# Edit /etc/default/brltty and set RUN_BRLTTY=yes to allow brltty to be
brltty:if [ "$RUN_BRLTTY" != yes ]; then
checkfs.sh:			BAT=yes
checkfs.sh:		if [ "$FSCKFIX" = yes ]
checkroot.sh:	# Set SULOGIN in /etc/default/rcS to yes if you want a sulogin to
checkroot.sh:	[ "$SULOGIN" = yes ] && sulogin -t 30 $CONSOLE
checkroot.sh:			[ "$FSTYPE" = "swap" ] && swap_on_lv=yes
checkroot.sh:			[ "$FSTYPE" = "swap" ] && swap_on_file=yes
checkroot.sh:		( [ "$PASS" != 0 ] && [ "$PASS" != "" ]   ) && rootcheck=yes
checkroot.sh:		if [ "$swap_on_lv" = yes ]
checkroot.sh:		elif [ "$swap_on_file" = yes ]
checkroot.sh:			ENABLE_SWAP=yes
checkroot.sh:		ENABLE_SWAP=yes
checkroot.sh:	if [ "$ENABLE_SWAP" = yes ]
checkroot.sh:	if [ "$rootcheck" = yes ]
checkroot.sh:					rootfatal=yes
checkroot.sh:	if [ "$rootfatal" = yes ]
checkroot.sh:	if which on_ac_power >/dev/null 2>&1 && [ "$rootcheck" = yes ]
checkroot.sh:		[ "$rootcheck" = yes ] && log_warning_msg "Fast boot enabled, so skipping file system check."
checkroot.sh:	if [ "$rootcheck" = yes ]
checkroot.sh:	if [ "$rootcheck" = yes ]
checkroot.sh:		if [ "$FSCKFIX" = yes ]
checkroot.sh:			INIT_MTAB_FILE=yes
checkroot.sh:	if [ "$INIT_MTAB_FILE" = yes ]
clamav-freshclam:  [ 'true' = "$lcvar" ] || [ 'yes' = "$lcvar" ] || [ 1 = "$lcvar" ]
console-screen.sh:	    VT="yes"
console-screen.sh:    if [ "${DO_VCSTIME}" = "yes" -a -x ${VCSTIME} ] ; then
cryptdisks:LOUD="yes"
cupsys:	if [ "$LOAD_LP_MODULE" = "yes" -a -f /usr/lib/cups/backend/parallel \
gdm:		# if usplash is running, make sure to stop it now, yes "start" kills it.
gdm:			DO_NOT_SWITCH_VT=yes /etc/init.d/usplash start
hwclock.sh:FIRST=no	# debian/rules sets this to 'yes' when creating hwclockfirst.sh
hwclock.sh:    [ "$GMT" = "-u" ] && UTC="yes"
hwclock.sh:		if [ "X$FIRST" = "Xyes" ] && [ ! -r /etc/localtime ]; then
hwclock.sh:       yes)	GMT="--utc"
hwclock.sh:       yes)	BADYEAR="--badyear" ;;
hwclock.sh:	    if [ "$FIRST" != yes ]; then
hwclockfirst.sh:FIRST=yes	# debian/rules sets this to 'yes' when creating hwclockfirst.sh
hwclockfirst.sh:    [ "$GMT" = "-u" ] && UTC="yes"
hwclockfirst.sh:		if [ "X$FIRST" = "Xyes" ] && [ ! -r /etc/localtime ]; then
hwclockfirst.sh:       yes)	GMT="--utc"
hwclockfirst.sh:       yes)	BADYEAR="--badyear" ;;
hwclockfirst.sh:	    if [ "$FIRST" != yes ]; then
nfs-common:            AUTO_NEED_IDMAPD=yes
nfs-common:    	    AUTO_NEED_GSSD=yes
nfs-common:    AUTO_NEED_IDMAPD=yes
nfs-common:    yes|no)
nfs-common:        NEED_STATD=yes
nfs-common:    yes|no)	
nfs-common:    yes|no)	
nfs-common:	if [ "$NEED_STATD" = yes ]; then
nfs-common:	if [ "$NEED_IDMAPD" = yes ] || [ "$NEED_GSSD" = yes ]
nfs-common:	    	if [ "$NEED_IDMAPD" = yes ]
nfs-common:		if [ "$NEED_GSSD" = yes ]
nfs-common:	if [ "$NEED_GSSD" = yes ]
nfs-common:	if [ "$NEED_IDMAPD" = yes ]
nfs-common:	if [ "$NEED_STATD" = yes ]
nfs-common:	if [ "$NEED_STATD" = yes ]
nfs-common:	if [ "$NEED_GSSD" = yes ]
nfs-common:	if [ "$NEED_IDMAPD" = yes ]
nfs-kernel-server:			ClearAddr=yes
nfs-kernel-server:	        if [ "$NEED_SVCGSSD" = "yes" ]; then
nfs-kernel-server:	if [ "$NEED_SVCGSSD" = "yes" ]; then
powernowd:        [ "x$DO_MODULES" = "xyes" -a -f /proc/modules ] && load_modules
powernowd:	[ "x$DO_MODULES" = "xyes" ] || start
powernowd.early:# Set DO_MODULES to yes which will trigger the module loading part of the
powernowd.early:DO_MODULES=yes
procps:               if [ "$VERBOSE" = "yes" ]; then
rc:    QUIET=yes
rc:if [ "$QUIET" != yes ]; then
rmnologin:#                    last step in the boot process, if DELAYLOGIN=yes.
rmnologin:[ "$DELAYLOGIN" ] || DELAYLOGIN=yes
ufw:    if [ "$ENABLED" = "yes" ] || [ "$ENABLED" = "YES" ]; then
ufw:        if [ "$IPV6" = "yes" ] || [ "$IPV6" = "YES" ]; then
ufw:                ip6tables -F || error="yes"
ufw:                ip6tables -X || error="yes"
ufw:                ip6tables -P INPUT DROP || error="yes"
ufw:                ip6tables -P OUTPUT DROP || error="yes"
ufw:                ip6tables -P FORWARD DROP || error="yes"
ufw:                ip6tables -A INPUT -i lo -j ACCEPT || error="yes"
ufw:                ip6tables -A OUTPUT -o lo -j ACCEPT || error="yes"
ufw:                if [ "$error" = "yes" ]; then
ufw:            $exe -F || error="yes"
ufw:            $exe -X || error="yes"
ufw:            $exe -P INPUT $DEFAULT_INPUT_POLICY || error="yes"
ufw:            $exe -P OUTPUT $DEFAULT_OUTPUT_POLICY || error="yes"
ufw:            $exe -P FORWARD $DEFAULT_FORWARD_POLICY || error="yes"
ufw:                $exe -N ufw${type}-not-local || error="yes"
ufw:            $exe -N ufw${type}-before-input || error="yes"
ufw:            $exe -N ufw${type}-before-output || error="yes"
ufw:            $exe -N ufw${type}-before-forward || error="yes"
ufw:            $exe -A INPUT -j ufw${type}-before-input || error="yes"
ufw:            $exe -A OUTPUT -j ufw${type}-before-output || error="yes"
ufw:            $exe -A FORWARD -j ufw${type}-before-forward || error="yes"
ufw:                    error="yes"
ufw:                $exe -N ufw${type}-user-input || error="yes"
ufw:                $exe -N ufw${type}-user-output || error="yes"
ufw:                $exe -N ufw${type}-user-forward || error="yes"
ufw:                $exe -A ufw${type}-before-input -j ufw${type}-user-input || error="yes"
ufw:                $exe -A ufw${type}-before-output -j ufw${type}-user-output || error="yes"
ufw:                $exe -A ufw${type}-before-forward -j ufw${type}-user-forward || error="yes"
ufw:                    error="yes"
ufw:            $exe -A ufw${type}-before-input -j RETURN || error="yes"
ufw:            $exe -A ufw${type}-before-output -j RETURN || error="yes"
ufw:            $exe -A ufw${type}-before-forward -j RETURN || error="yes"
ufw:            $exe -N ufw${type}-after-input || error="yes"
ufw:            $exe -N ufw${type}-after-output || error="yes"
ufw:            $exe -N ufw${type}-after-forward || error="yes"
ufw:            $exe -A INPUT -j ufw${type}-after-input || error="yes"
ufw:            $exe -A OUTPUT -j ufw${type}-after-output || error="yes"
ufw:            $exe -A FORWARD -j ufw${type}-after-forward || error="yes"
ufw:                    error="yes"
ufw:            $exe -A ufw${type}-after-input -j RETURN || error="yes"
ufw:            $exe -A ufw${type}-after-output -j RETURN || error="yes"
ufw:            $exe -A ufw${type}-after-forward -j RETURN || error="yes"
ufw:        if [ "$error" = "yes" ]; then
ufw:    if [ "$ENABLED" != "yes" ] && [ "$ENABLED" != "YES" ]; then
ufw:        $exe -F || error="yes"
ufw:        $exe -X || error="yes"
ufw:        $exe -P INPUT ACCEPT || error="yes"
ufw:        $exe -P OUTPUT ACCEPT || error="yes"
ufw:        $exe -P FORWARD ACCEPT || error="yes"
ufw:    if [ "$error" = "yes" ]; then
ufw:    if [ "$ENABLED" = "yes" ] || [ "$ENABLED" = "YES" ]; then
usplash:		if [ "$(fgconsole 2>/dev/null)" = "8" ] && [ "$DO_NOT_SWITCH_VT" != "yes" ]; then
vmware:  if [ "$VMWARE_DEBUG" = 'yes' ]; then
vmware:  if [ "$VMWARE_DEBUG" = 'yes' ]; then
vmware:  loop='yes'
vmware:  while [ "$loop" = 'yes' ]; do
vmware:      echo "yes"
vmware:   if [ $retval -ne 0 -a "`isSELinuxEnabled`" = 'yes' ]; then
vmware:    echo yes
vmware:  if [ "`is_ESX_running`" = 'yes' ]; then
vmware:    if [ "$vmdb_answer_VMBLOCK_CONFED" = 'yes' ]; then
vmware:      echo yes
vmware:   /sbin/lsmod | awk 'BEGIN {n = "no";} {if ($1 == "'"$module"'") n = "yes";} END {print n;}'
vmware:   if [ "`isLoaded "$1"`" = 'yes' ]; then
vmware:   if [ "`isLoaded "$ppuser"`" = 'yes' ]; then
vmware:   if [ "`isLoaded "$vmci"`" = 'yes' ]; then
vmware:   if [ "$vmdb_answer_VSOCK_CONFED" = 'yes' ]; then
vmware:      echo yes
vmware:   if [ "$vmdb_answer_VMCI_CONFED" = 'yes' ]; then
vmware:      echo yes
vmware:         if [ "`is_vmci_needed`" = 'yes' ]; then
vmware:         if [ "`is_vsock_needed`" = 'yes' ]; then
vmware:         if [ "`is_vmblock_needed`" = 'yes' ] ; then
vmware:         if [ "$vmdb_answer_NETWORKING" = 'yes' ]; then
vmware:         if [ "$vmdb_answer_VMAUTHD_USE_LAUNCHER" = 'yes' ]; then
vmware:         if [ "`is_vsock_needed`" = 'yes' ]; then
vmware:         if [ "`is_vmci_needed`" = 'yes' ]; then
vmware:         if [ "`is_vmblock_needed`" = 'yes' ] ; then
vmware:         if [ "$vmdb_answer_NETWORKING" = "yes" ]; then
vmware:         [ "`isLoaded "$driver"`" = 'yes' ] && echo loaded || echo "not loaded"
vmware:            [ "`isLoaded "$ppuser"`" = 'yes' ] && echo loaded || echo "not loaded"
vmware:         if [ "$vmdb_answer_NETWORKING" = "yes" ]; then
vmware:            [ "`isLoaded "$vnet"`" = 'yes' ] && echo loaded || echo "not loaded"
vmware-autostart:  if [ "$VMWARE_DEBUG" = 'yes' ]; then
vmware-autostart:  if [ "$VMWARE_DEBUG" = 'yes' ]; then
vmware-autostart:  loop='yes'
vmware-autostart:  while [ "$loop" = 'yes' ]; do
vmware-autostart:      echo "yes"
vmware-autostart:   if [ $retval -ne 0 -a "`isSELinuxEnabled`" = 'yes' ]; then
vmware-autostart:    echo yes
vmware-autostart:  if [ "`is_ESX_running`" = 'yes' ]; then
vmware-autostart:    if [ "$vmdb_answer_VMBLOCK_CONFED" = 'yes' ]; then
vmware-autostart:      echo yes
vmware-autostart:   /sbin/lsmod | awk 'BEGIN {n = "no";} {if ($1 == "'"$module"'") n = "yes";} END {print n;}'
vmware-autostart:   if [ "`isLoaded "$1"`" = 'yes' ]; then
vmware-autostart:   if [ "`isLoaded "$ppuser"`" = 'yes' ]; then
vmware-autostart:   if [ "`isLoaded "$vmci"`" = 'yes' ]; then
vmware-autostart:   if [ "$vmdb_answer_VSOCK_CONFED" = 'yes' ]; then
vmware-autostart:      echo yes
vmware-autostart:   if [ "$vmdb_answer_VMCI_CONFED" = 'yes' ]; then
vmware-autostart:      echo yes
vmware-autostart:         if [ "`is_vmci_needed`" = 'yes' ]; then
vmware-autostart:         if [ "`is_vsock_needed`" = 'yes' ]; then
vmware-autostart:         if [ "`is_vmblock_needed`" = 'yes' ] ; then
vmware-autostart:         if [ "$vmdb_answer_NETWORKING" = 'yes' ]; then
vmware-autostart:         if [ "$vmdb_answer_VMAUTHD_USE_LAUNCHER" = 'yes' ]; then
vmware-autostart:         if [ "`is_vsock_needed`" = 'yes' ]; then
vmware-autostart:         if [ "`is_vmci_needed`" = 'yes' ]; then
vmware-autostart:         if [ "`is_vmblock_needed`" = 'yes' ] ; then
vmware-autostart:         if [ "$vmdb_answer_NETWORKING" = "yes" ]; then
vmware-autostart:         [ "`isLoaded "$driver"`" = 'yes' ] && echo loaded || echo "not loaded"
vmware-autostart:            [ "`isLoaded "$ppuser"`" = 'yes' ] && echo loaded || echo "not loaded"
vmware-autostart:         if [ "$vmdb_answer_NETWORKING" = "yes" ]; then
vmware-autostart:            [ "`isLoaded "$vnet"`" = 'yes' ] && echo loaded || echo "not loaded"
vmware-core:  if [ "$VMWARE_DEBUG" = 'yes' ]; then
vmware-core:  if [ "$VMWARE_DEBUG" = 'yes' ]; then
vmware-core:  loop='yes'
vmware-core:  while [ "$loop" = 'yes' ]; do
vmware-core:      echo "yes"
vmware-core:   if [ $retval -ne 0 -a "`isSELinuxEnabled`" = 'yes' ]; then
vmware-core:    echo yes
vmware-core:  if [ "`is_ESX_running`" = 'yes' ]; then
vmware-core:    if [ "$vmdb_answer_VMBLOCK_CONFED" = 'yes' ]; then
vmware-core:      echo yes
vmware-core:   /sbin/lsmod | awk 'BEGIN {n = "no";} {if ($1 == "'"$module"'") n = "yes";} END {print n;}'
vmware-core:   if [ "`isLoaded "$1"`" = 'yes' ]; then
vmware-core:   if [ "`isLoaded "$ppuser"`" = 'yes' ]; then
vmware-core:   if [ "`isLoaded "$vmci"`" = 'yes' ]; then
vmware-core:   if [ "$vmdb_answer_VSOCK_CONFED" = 'yes' ]; then
vmware-core:      echo yes
vmware-core:   if [ "$vmdb_answer_VMCI_CONFED" = 'yes' ]; then
vmware-core:      echo yes
vmware-core:         if [ "`is_vmci_needed`" = 'yes' ]; then
vmware-core:         if [ "`is_vsock_needed`" = 'yes' ]; then
vmware-core:         if [ "`is_vmblock_needed`" = 'yes' ] ; then
vmware-core:         if [ "$vmdb_answer_NETWORKING" = 'yes' ]; then
vmware-core:         if [ "$vmdb_answer_VMAUTHD_USE_LAUNCHER" = 'yes' ]; then
vmware-core:         if [ "`is_vsock_needed`" = 'yes' ]; then
vmware-core:         if [ "`is_vmci_needed`" = 'yes' ]; then
vmware-core:         if [ "`is_vmblock_needed`" = 'yes' ] ; then
vmware-core:         if [ "$vmdb_answer_NETWORKING" = "yes" ]; then
vmware-core:         [ "`isLoaded "$driver"`" = 'yes' ] && echo loaded || echo "not loaded"
vmware-core:            [ "`isLoaded "$ppuser"`" = 'yes' ] && echo loaded || echo "not loaded"
vmware-core:         if [ "$vmdb_answer_NETWORKING" = "yes" ]; then
vmware-core:            [ "`isLoaded "$vnet"`" = 'yes' ] && echo loaded || echo "not loaded"
vmware-mgmt:  if [ "$VMWARE_DEBUG" = 'yes' ]; then
vmware-mgmt:  if [ "$VMWARE_DEBUG" = 'yes' ]; then
vmware-mgmt:  loop='yes'
vmware-mgmt:  while [ "$loop" = 'yes' ]; do
vmware-mgmt:      echo "yes"
vmware-mgmt:   if [ $retval -ne 0 -a "`isSELinuxEnabled`" = 'yes' ]; then
vmware-mgmt:    echo yes
vmware-mgmt:  if [ "`is_ESX_running`" = 'yes' ]; then
vmware-mgmt:    if [ "$vmdb_answer_VMBLOCK_CONFED" = 'yes' ]; then
vmware-mgmt:      echo yes
vmware-mgmt:   /sbin/lsmod | awk 'BEGIN {n = "no";} {if ($1 == "'"$module"'") n = "yes";} END {print n;}'
vmware-mgmt:   if [ "`isLoaded "$1"`" = 'yes' ]; then
vmware-mgmt:   if [ "`isLoaded "$ppuser"`" = 'yes' ]; then
vmware-mgmt:   if [ "`isLoaded "$vmci"`" = 'yes' ]; then
vmware-mgmt:   if [ "$vmdb_answer_VSOCK_CONFED" = 'yes' ]; then
vmware-mgmt:      echo yes
vmware-mgmt:   if [ "$vmdb_answer_VMCI_CONFED" = 'yes' ]; then
vmware-mgmt:      echo yes
vmware-mgmt:         if [ "`is_vmci_needed`" = 'yes' ]; then
vmware-mgmt:         if [ "`is_vsock_needed`" = 'yes' ]; then
vmware-mgmt:         if [ "`is_vmblock_needed`" = 'yes' ] ; then
vmware-mgmt:         if [ "$vmdb_answer_NETWORKING" = 'yes' ]; then
vmware-mgmt:         if [ "$vmdb_answer_VMAUTHD_USE_LAUNCHER" = 'yes' ]; then
vmware-mgmt:         if [ "`is_vsock_needed`" = 'yes' ]; then
vmware-mgmt:         if [ "`is_vmci_needed`" = 'yes' ]; then
vmware-mgmt:         if [ "`is_vmblock_needed`" = 'yes' ] ; then
vmware-mgmt:         if [ "$vmdb_answer_NETWORKING" = "yes" ]; then
vmware-mgmt:         [ "`isLoaded "$driver"`" = 'yes' ] && echo loaded || echo "not loaded"
vmware-mgmt:            [ "`isLoaded "$ppuser"`" = 'yes' ] && echo loaded || echo "not loaded"
vmware-mgmt:         if [ "$vmdb_answer_NETWORKING" = "yes" ]; then
vmware-mgmt:            [ "`isLoaded "$vnet"`" = 'yes' ] && echo loaded || echo "not loaded"
vmware-server:  loop='yes'
vmware-server:  while [ "$loop" = 'yes' ]; do
vmware-server:   /sbin/lsmod | awk 'BEGIN {n = "no";} {if ($1 == "'"$module"'") n = "yes";} END {print n;}'
vmware-server:   if [ "$VMWARE_DEBUG" = 'yes' ]; then
vmware-server:   if [ "$VMWARE_DEBUG" = 'yes' ]; then
vmware-server:   if [ "`isLoaded "$1"`" = 'yes' ]; then
vmware-server:   if [ "`isLoaded "$ppuser"`" = 'yes' ]; then
vmware-server:      if [ "$vmdb_answer_NETWORKING" = 'yes' ]; then
vmware-server:      if [ "$vmdb_answer_NETWORKING" = "yes" ]; then
vmware-server:      [ "`isLoaded "$driver"`" = 'yes' ] && echo loaded || echo "not loaded"
vmware-server:         [ "`isLoaded "$ppuser"`" = 'yes' ] && echo loaded || echo "not loaded"
vmware-server:      if [ "$vmdb_answer_NETWORKING" = "yes" ]; then
vmware-server:         [ "`isLoaded "$vnet"`" = 'yes' ] && echo loaded || echo "not loaded"

---

### Post by calvert888 on 2010-08-02
Also, here is an excerpt from my kern.log:

> Aug  1 18:02:09 Q1 kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug  1 18:02:09 Q1 kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug  1 18:02:09 Q1 kernel: Symbols match kernel version 2.6.24.
Aug  1 18:02:10 Q1 kernel: Loaded 18813 symbols from 94 modules.
Aug  1 18:02:10 Q1 kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug  1 18:02:10 Q1 kernel: [    0.000000] Initializing cgroup subsys cpu
Aug  1 18:02:10 Q1 kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
Aug  1 18:02:10 Q1 kernel: [    0.000000] BIOS-provided physical RAM map:
Aug  1 18:02:10 Q1 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Aug  1 18:02:10 Q1 kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Aug  1 18:02:10 Q1 kernel: [    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
Aug  1 18:02:10 Q1 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000005fe30000 (usable)
Aug  1 18:02:10 Q1 kernel: [    0.000000]  BIOS-e820: 000000005fe30000 - 000000005fe3e05e (ACPI NVS)
Aug  1 18:02:10 Q1 kernel: [    0.000000]  BIOS-e820: 000000005fe3e05e - 000000005ff30000 (usable)
Aug  1 18:02:10 Q1 kernel: [    0.000000]  BIOS-e820: 000000005ff30000 - 000000005ff40000 (ACPI data)
Aug  1 18:02:10 Q1 kernel: [    0.000000]  BIOS-e820: 000000005ff40000 - 000000005fff0000 (ACPI NVS)
Aug  1 18:02:10 Q1 kernel: [    0.000000]  BIOS-e820: 000000005fff0000 - 0000000060000000 (reserved)
Aug  1 18:02:10 Q1 kernel: [    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
Aug  1 18:02:10 Q1 kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Aug  1 18:02:10 Q1 kernel: [    0.000000] 639MB HIGHMEM available.
Aug  1 18:02:10 Q1 kernel: [    0.000000] 896MB LOWMEM available.
Aug  1 18:02:10 Q1 kernel: [    0.000000] found SMP MP-table at 000ff780
Aug  1 18:02:10 Q1 kernel: [    0.000000] Entering add_active_range(0, 0, 393008) 0 entries of 256 used
Aug  1 18:02:10 Q1 kernel: [    0.000000] Zone PFN ranges:
Aug  1 18:02:10 Q1 kernel: [    0.000000]   DMA             0 ->     4096
Aug  1 18:02:10 Q1 kernel: [    0.000000]   Normal       4096 ->   229376
Aug  1 18:02:10 Q1 kernel: [    0.000000]   HighMem    229376 ->   393008
Aug  1 18:02:10 Q1 kernel: [    0.000000] Movable zone start PFN for each node
Aug  1 18:02:10 Q1 kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug  1 18:02:10 Q1 kernel: [    0.000000]     0:        0 ->   393008
Aug  1 18:02:10 Q1 kernel: [    0.000000] On node 0 totalpages: 393008
Aug  1 18:02:10 Q1 kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug  1 18:02:10 Q1 kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug  1 18:02:10 Q1 kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug  1 18:02:10 Q1 kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug  1 18:02:10 Q1 kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug  1 18:02:10 Q1 kernel: [    0.000000]   HighMem zone: 1278 pages used for memmap
Aug  1 18:02:10 Q1 kernel: [    0.000000]   HighMem zone: 162354 pages, LIFO batch:31
Aug  1 18:02:10 Q1 kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug  1 18:02:10 Q1 kernel: [    0.000000] DMI 2.3 present.
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F63B0 checksum 0
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: RSDP 000F63B0, 0014 (r0 ACPIAM)
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: RSDT 5FF30000, 0034 (r1 INTEL  D865PERL 20040122 MSFT       97)
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: FACP 5FF30200, 0081 (r2 INTEL  D865PERL 20040122 MSFT       97)
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: DSDT 5FF30370, 4170 (r1 INTEL  D865PERL        6 MSFT  100000D)
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: FACS 5FF40000, 0040
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: APIC 5FF30300, 0068 (r1 INTEL  D865PERL 20040122 MSFT       97)
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: ASF! 5FF344E0, 0099 (r16 LEGEND I865PASF        1 MSFT  100000D)
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: WDDT 5FF34579, 0040 (r1 INTEL  OEMWDDT         1 MSFT  100000D)
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Aug  1 18:02:10 Q1 kernel: [    0.000000] Processor #0 15:3 APIC version 20
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Aug  1 18:02:10 Q1 kernel: [    0.000000] Processor #1 15:3 APIC version 20
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug  1 18:02:10 Q1 kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug  1 18:02:10 Q1 kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug  1 18:02:10 Q1 kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug  1 18:02:10 Q1 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug  1 18:02:10 Q1 kernel: [    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ecf0000)
Aug  1 18:02:10 Q1 kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug  1 18:02:10 Q1 kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e6000
Aug  1 18:02:10 Q1 kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e6000 - 0000000000100000
Aug  1 18:02:10 Q1 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 389938
Aug  1 18:02:10 Q1 kernel: [    0.000000] Kernel command line: root=UUID=8a523fa6-5cd5-4e9c-8637-57d7349cc403 ro quiet splash
Aug  1 18:02:10 Q1 kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug  1 18:02:10 Q1 kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug  1 18:02:10 Q1 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug  1 18:02:10 Q1 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug  1 18:02:10 Q1 kernel: [    0.000000] Initializing CPU#0
Aug  1 18:02:10 Q1 kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug  1 18:02:10 Q1 kernel: [    0.000000] Detected 2793.060 MHz processor.
Aug  1 18:02:10 Q1 kernel: [   13.240594] Console: colour VGA+ 80x25
Aug  1 18:02:10 Q1 kernel: [   13.240598] console [tty0] enabled
Aug  1 18:02:10 Q1 kernel: [   13.241306] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug  1 18:02:10 Q1 kernel: [   13.241962] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug  1 18:02:10 Q1 kernel: [   13.325152] Memory: 1545764k/1572032k available (2177k kernel code, 25004k reserved, 1006k data, 368k init, 654468k highmem)
Aug  1 18:02:10 Q1 kernel: [   13.325163] virtual kernel memory layout:
Aug  1 18:02:10 Q1 kernel: [   13.325164]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug  1 18:02:10 Q1 kernel: [   13.325165]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug  1 18:02:10 Q1 kernel: [   13.325166]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug  1 18:02:10 Q1 kernel: [   13.325168]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug  1 18:02:10 Q1 kernel: [   13.325169]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug  1 18:02:10 Q1 kernel: [   13.325170]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
Aug  1 18:02:10 Q1 kernel: [   13.325171]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
Aug  1 18:02:10 Q1 kernel: [   13.325174] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug  1 18:02:10 Q1 kernel: [   13.325233] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug  1 18:02:10 Q1 kernel: [   13.405127] Calibrating delay using timer specific routine.. 5590.90 BogoMIPS (lpj=11181805)
Aug  1 18:02:10 Q1 kernel: [   13.405164] Security Framework initialized
Aug  1 18:02:10 Q1 kernel: [   13.405173] SELinux:  Disabled at boot.
Aug  1 18:02:10 Q1 kernel: [   13.405193] AppArmor: AppArmor initialized
Aug  1 18:02:10 Q1 kernel: [   13.405198] Failure registering capabilities with primary security module.
Aug  1 18:02:10 Q1 kernel: [   13.405208] Mount-cache hash table entries: 512
Aug  1 18:02:10 Q1 kernel: [   13.405381] Initializing cgroup subsys ns
Aug  1 18:02:10 Q1 kernel: [   13.405388] Initializing cgroup subsys cpuacct
Aug  1 18:02:10 Q1 kernel: [   13.405404] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000 00000000
Aug  1 18:02:10 Q1 kernel: [   13.405414] monitor/mwait feature present.
Aug  1 18:02:10 Q1 kernel: [   13.405416] using mwait in idle threads.
Aug  1 18:02:10 Q1 kernel: [   13.405422] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug  1 18:02:10 Q1 kernel: [   13.405425] CPU: L2 cache: 1024K
Aug  1 18:02:10 Q1 kernel: [   13.405428] CPU: Physical Processor ID: 0
Aug  1 18:02:10 Q1 kernel: [   13.405431] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000041d 00000000 00000000 00000000
Aug  1 18:02:10 Q1 kernel: [   13.405444] Compat vDSO mapped to ffffe000.
Aug  1 18:02:10 Q1 kernel: [   13.405465] Checking 'hlt' instruction... OK.
Aug  1 18:02:10 Q1 kernel: [   13.421610] SMP alternatives: switching to UP code
Aug  1 18:02:10 Q1 kernel: [   13.423733] Early unpacking initramfs... done
Aug  1 18:02:10 Q1 kernel: [   13.756668] ACPI: Core revision 20070126
Aug  1 18:02:10 Q1 kernel: [   13.756727] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug  1 18:02:10 Q1 kernel: [   13.758961] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 03
Aug  1 18:02:10 Q1 kernel: [   13.758983] SMP alternatives: switching to SMP code
Aug  1 18:02:10 Q1 kernel: [   13.759884] Booting processor 1/1 eip 3000
Aug  1 18:02:10 Q1 kernel: [   13.770056] Initializing CPU#1
Aug  1 18:02:10 Q1 kernel: [   13.848386] Calibrating delay using timer specific routine.. 5586.44 BogoMIPS (lpj=11172888)
Aug  1 18:02:10 Q1 kernel: [   13.848398] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000 00000000
Aug  1 18:02:10 Q1 kernel: [   13.848407] monitor/mwait feature present.
Aug  1 18:02:10 Q1 kernel: [   13.848414] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug  1 18:02:10 Q1 kernel: [   13.848417] CPU: L2 cache: 1024K
Aug  1 18:02:10 Q1 kernel: [   13.848420] CPU: Physical Processor ID: 0
Aug  1 18:02:10 Q1 kernel: [   13.848423] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000041d 00000000 00000000 00000000
Aug  1 18:02:10 Q1 kernel: [   13.848814] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 03
Aug  1 18:02:10 Q1 kernel: [   13.848861] Total of 2 processors activated (11177.34 BogoMIPS).
Aug  1 18:02:10 Q1 kernel: [   13.848993] ENABLING IO-APIC IRQs
Aug  1 18:02:10 Q1 kernel: [   13.849172] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug  1 18:02:10 Q1 kernel: [   13.996306] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug  1 18:02:10 Q1 kernel: [   14.016290] Brought up 2 CPUs
Aug  1 18:02:10 Q1 kernel: [   14.016320] CPU0 attaching sched-domain:
Aug  1 18:02:10 Q1 kernel: [   14.016324]  domain 0: span 03
Aug  1 18:02:10 Q1 kernel: [   14.016326]   groups: 01 02
Aug  1 18:02:10 Q1 kernel: [   14.016331]   domain 1: span 03
Aug  1 18:02:10 Q1 kernel: [   14.016333]    groups: 03
Aug  1 18:02:10 Q1 kernel: [   14.016336] CPU1 attaching sched-domain:
Aug  1 18:02:10 Q1 kernel: [   14.016338]  domain 0: span 03
Aug  1 18:02:10 Q1 kernel: [   14.016340]   groups: 02 01
Aug  1 18:02:10 Q1 kernel: [   14.016344]   domain 1: span 03
Aug  1 18:02:10 Q1 kernel: [   14.016346]    groups: 03
Aug  1 18:02:10 Q1 kernel: [   14.016654] net_namespace: 64 bytes
Aug  1 18:02:10 Q1 kernel: [   14.016669] Booting paravirtualized kernel on bare hardware
Aug  1 18:02:10 Q1 kernel: [   14.017282] Time: 18:00:31  Date: 08/01/10
Aug  1 18:02:10 Q1 kernel: [   14.017312] NET: Registered protocol family 16
Aug  1 18:02:10 Q1 kernel: [   14.017607] EISA bus registered
Aug  1 18:02:10 Q1 kernel: [   14.017614] ACPI: bus type pci registered
Aug  1 18:02:10 Q1 kernel: [   14.019148] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
Aug  1 18:02:10 Q1 kernel: [   14.019151] PCI: Using configuration type 1
Aug  1 18:02:10 Q1 kernel: [   14.019179] Setting up standard PCI resources
Aug  1 18:02:10 Q1 kernel: [   14.033444] ACPI: EC: Look up EC in DSDT
Aug  1 18:02:10 Q1 kernel: [   14.037337] ACPI: Interpreter enabled
Aug  1 18:02:10 Q1 kernel: [   14.037342] ACPI: (supports S0 S1 S4 S5)
Aug  1 18:02:10 Q1 kernel: [   14.037361] ACPI: Using IOAPIC for interrupt routing
Aug  1 18:02:10 Q1 kernel: [   14.044327] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug  1 18:02:10 Q1 kernel: [   14.044854] Force enabled HPET at base address 0xfed00000
Aug  1 18:02:10 Q1 kernel: [   14.044862] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
Aug  1 18:02:10 Q1 kernel: [   14.044866] PCI quirk: region 0500-053f claimed by ICH4 GPIO
Aug  1 18:02:10 Q1 kernel: [   14.045399] PCI: Transparent bridge - 0000:00:1e.0
Aug  1 18:02:10 Q1 kernel: [   14.045426] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug  1 18:02:10 Q1 kernel: [   14.045543] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Aug  1 18:02:10 Q1 kernel: [   14.045625] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
Aug  1 18:02:10 Q1 kernel: [   14.048012] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Aug  1 18:02:10 Q1 kernel: [   14.048196] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Aug  1 18:02:10 Q1 kernel: [   14.048382] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Aug  1 18:02:10 Q1 kernel: [   14.048553] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Aug  1 18:02:10 Q1 kernel: [   14.048724] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Aug  1 18:02:10 Q1 kernel: [   14.048895] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Aug  1 18:02:10 Q1 kernel: [   14.049070] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Aug  1 18:02:10 Q1 kernel: [   14.049243] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Aug  1 18:02:10 Q1 kernel: [   14.049419] ACPI: Power Resource [URP1] (off)
Aug  1 18:02:10 Q1 kernel: [   14.049457] ACPI: Power Resource [FDDP] (off)
Aug  1 18:02:10 Q1 kernel: [   14.049494] ACPI: Power Resource [LPTP] (off)
Aug  1 18:02:10 Q1 kernel: [   14.049568] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug  1 18:02:10 Q1 kernel: [   14.049616] pnp: PnP ACPI init
Aug  1 18:02:10 Q1 kernel: [   14.049627] ACPI: bus type pnp registered
Aug  1 18:02:10 Q1 kernel: [   14.053255] pnp: PnP ACPI: found 14 devices
Aug  1 18:02:10 Q1 kernel: [   14.053258] ACPI: ACPI bus type pnp unregistered
Aug  1 18:02:10 Q1 kernel: [   14.053263] PnPBIOS: Disabled by ACPI PNP
Aug  1 18:02:10 Q1 kernel: [   14.053612] PCI: Using ACPI for IRQ routing
Aug  1 18:02:10 Q1 kernel: [   14.053616] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug  1 18:02:10 Q1 kernel: [   14.076033] NET: Registered protocol family 8
Aug  1 18:02:10 Q1 kernel: [   14.076036] NET: Registered protocol family 20
Aug  1 18:02:10 Q1 kernel: [   14.076165] hpet clockevent registered
Aug  1 18:02:10 Q1 kernel: [   14.076171] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Aug  1 18:02:10 Q1 kernel: [   14.076177] hpet0: 3 64-bit timers, 14318180 Hz
Aug  1 18:02:10 Q1 kernel: [   14.077227] AppArmor: AppArmor Filesystem Enabled
Aug  1 18:02:10 Q1 kernel: [   14.080015] Time: tsc clocksource has been installed.
Aug  1 18:02:10 Q1 kernel: [   14.092060] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
Aug  1 18:02:10 Q1 kernel: [   14.092069] system 00:0c: ioport range 0x400-0x47f has been reserved
Aug  1 18:02:10 Q1 kernel: [   14.092072] system 00:0c: ioport range 0x680-0x6ff has been reserved
Aug  1 18:02:10 Q1 kernel: [   14.092074] system 00:0c: ioport range 0x500-0x53f has been reserved
Aug  1 18:02:10 Q1 kernel: [   14.092078] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
Aug  1 18:02:10 Q1 kernel: [   14.092081] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
Aug  1 18:02:10 Q1 kernel: [   14.092084] system 00:0c: iomem range 0xfed20000-0xfed9ffff could not be reserved
Aug  1 18:02:10 Q1 kernel: [   14.092092] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Aug  1 18:02:10 Q1 kernel: [   14.092095] system 00:0d: iomem range 0xc0000-0xdffff could not be reserved
Aug  1 18:02:10 Q1 kernel: [   14.092098] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
Aug  1 18:02:10 Q1 kernel: [   14.092101] system 00:0d: iomem range 0x100000-0x5fffffff could not be reserved
Aug  1 18:02:10 Q1 kernel: [   14.092104] system 00:0d: iomem range 0x0-0x0 could not be reserved
Aug  1 18:02:10 Q1 kernel: [   14.122662] PCI: Bridge: 0000:00:01.0
Aug  1 18:02:10 Q1 kernel: [   14.122665]   IO window: disabled.
Aug  1 18:02:10 Q1 kernel: [   14.122670]   MEM window: fc900000-fe9fffff
Aug  1 18:02:10 Q1 kernel: [   14.122675]   PREFETCH window: d4800000-f47fffff
Aug  1 18:02:10 Q1 kernel: [   14.122681] PCI: Bridge: 0000:00:1e.0
Aug  1 18:02:10 Q1 kernel: [   14.122684]   IO window: b000-bfff
Aug  1 18:02:10 Q1 kernel: [   14.122689]   MEM window: fea00000-feafffff
Aug  1 18:02:10 Q1 kernel: [   14.122694]   PREFETCH window: disabled.
Aug  1 18:02:10 Q1 kernel: [   14.122712] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Aug  1 18:02:10 Q1 kernel: [   14.122725] NET: Registered protocol family 2
Aug  1 18:02:10 Q1 kernel: [   14.159973] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug  1 18:02:10 Q1 kernel: [   14.160356] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug  1 18:02:10 Q1 kernel: [   14.161146] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug  1 18:02:10 Q1 kernel: [   14.161774] TCP: Hash tables configured (established 131072 bind 65536)
Aug  1 18:02:10 Q1 kernel: [   14.161777] TCP reno registered
Aug  1 18:02:10 Q1 kernel: [   14.172093] checking if image is initramfs... it is
Aug  1 18:02:10 Q1 kernel: [   14.575354] Switched to high resolution mode on CPU 1
Aug  1 18:02:10 Q1 kernel: [   14.579182] Switched to high resolution mode on CPU 0
Aug  1 18:02:10 Q1 kernel: [   14.832630] Freeing initrd memory: 7729k freed
Aug  1 18:02:10 Q1 kernel: [   14.833747] audit: initializing netlink socket (disabled)
Aug  1 18:02:10 Q1 kernel: [   14.833773] audit(1280685631.388:1): initialized
Aug  1 18:02:10 Q1 kernel: [   14.834052] highmem bounce pool size: 64 pages
Aug  1 18:02:10 Q1 kernel: [   14.837113] VFS: Disk quotas dquot_6.5.1
Aug  1 18:02:10 Q1 kernel: [   14.837227] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug  1 18:02:10 Q1 kernel: [   14.837402] io scheduler noop registered
Aug  1 18:02:10 Q1 kernel: [   14.837405] io scheduler anticipatory registered
Aug  1 18:02:10 Q1 kernel: [   14.837408] io scheduler deadline registered
Aug  1 18:02:10 Q1 kernel: [   14.837421] io scheduler cfq registered (default)
Aug  1 18:02:10 Q1 kernel: [   14.837527] Boot video device is 0000:01:00.0
Aug  1 18:02:10 Q1 kernel: [   14.837533] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
Aug  1 18:02:10 Q1 kernel: [   14.837951] isapnp: Scanning for PnP cards...
Aug  1 18:02:10 Q1 kernel: [   15.191067] isapnp: No Plug & Play device found
Aug  1 18:02:10 Q1 kernel: [   15.232090] Real Time Clock Driver v1.12ac
Aug  1 18:02:10 Q1 kernel: [   15.232230] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug  1 18:02:10 Q1 kernel: [   15.232361] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug  1 18:02:10 Q1 kernel: [   15.233367] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug  1 18:02:10 Q1 kernel: [   15.234512] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug  1 18:02:10 Q1 kernel: [   15.234603] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug  1 18:02:10 Q1 kernel: [   15.234757] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Aug  1 18:02:10 Q1 kernel: [   15.237687] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug  1 18:02:10 Q1 kernel: [   15.237694] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug  1 18:02:10 Q1 kernel: [   15.262141] mice: PS/2 mouse device common for all mice
Aug  1 18:02:10 Q1 kernel: [   15.262323] EISA: Probing bus 0 at eisa.0
Aug  1 18:02:10 Q1 kernel: [   15.262364] EISA: Detected 0 cards.
Aug  1 18:02:10 Q1 kernel: [   15.262368] cpuidle: using governor ladder
Aug  1 18:02:10 Q1 kernel: [   15.262370] cpuidle: using governor menu
Aug  1 18:02:10 Q1 kernel: [   15.262468] NET: Registered protocol family 1
Aug  1 18:02:10 Q1 kernel: [   15.262501] Using IPI No-Shortcut mode
Aug  1 18:02:10 Q1 kernel: [   15.262539] registered taskstats version 1
Aug  1 18:02:10 Q1 kernel: [   15.262645]   Magic number: 6:955:37
Aug  1 18:02:10 Q1 kernel: [   15.262775] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug  1 18:02:10 Q1 kernel: [   15.262777] EDD information not available.
Aug  1 18:02:10 Q1 kernel: [   15.263152] Freeing unused kernel memory: 368k freed
Aug  1 18:02:10 Q1 kernel: [   15.283685] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug  1 18:02:10 Q1 kernel: [   16.544247] fuse init (API version 7.9)
Aug  1 18:02:10 Q1 kernel: [   16.575286] ACPI: Processor [CPU1] (supports 8 throttling states)
Aug  1 18:02:10 Q1 kernel: [   16.575326] ACPI: Processor [CPU2] (supports 8 throttling states)
Aug  1 18:02:10 Q1 kernel: [   16.791393] usbcore: registered new interface driver usbfs
Aug  1 18:02:10 Q1 kernel: [   16.791433] usbcore: registered new interface driver hub
Aug  1 18:02:10 Q1 kernel: [   16.802544] usbcore: registered new device driver usb
Aug  1 18:02:10 Q1 kernel: [   16.810580] USB Universal Host Controller Interface driver v3.0
Aug  1 18:02:10 Q1 kernel: [   16.810669] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug  1 18:02:10 Q1 kernel: [   16.810685] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Aug  1 18:02:10 Q1 kernel: [   16.810691] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug  1 18:02:10 Q1 kernel: [   16.811022] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Aug  1 18:02:10 Q1 kernel: [   16.811056] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000cc00
Aug  1 18:02:10 Q1 kernel: [   16.811294] usb usb1: configuration #1 chosen from 1 choice
Aug  1 18:02:10 Q1 kernel: [   16.811336] hub 1-0:1.0: USB hub found
Aug  1 18:02:10 Q1 kernel: [   16.811346] hub 1-0:1.0: 2 ports detected
Aug  1 18:02:10 Q1 kernel: [   16.915185] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Aug  1 18:02:10 Q1 kernel: [   16.915203] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Aug  1 18:02:10 Q1 kernel: [   16.915210] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug  1 18:02:10 Q1 kernel: [   16.915249] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Aug  1 18:02:10 Q1 kernel: [   16.915281] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d000
Aug  1 18:02:10 Q1 kernel: [   16.915462] usb usb2: configuration #1 chosen from 1 choice
Aug  1 18:02:10 Q1 kernel: [   16.915506] hub 2-0:1.0: USB hub found
Aug  1 18:02:10 Q1 kernel: [   16.915517] hub 2-0:1.0: 2 ports detected
Aug  1 18:02:10 Q1 kernel: [   17.019043] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Aug  1 18:02:10 Q1 kernel: [   17.019061] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Aug  1 18:02:10 Q1 kernel: [   17.019067] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug  1 18:02:10 Q1 kernel: [   17.019107] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Aug  1 18:02:10 Q1 kernel: [   17.019139] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
Aug  1 18:02:10 Q1 kernel: [   17.019328] usb usb3: configuration #1 chosen from 1 choice
Aug  1 18:02:10 Q1 kernel: [   17.019369] hub 3-0:1.0: USB hub found
Aug  1 18:02:10 Q1 kernel: [   17.019379] hub 3-0:1.0: 2 ports detected
Aug  1 18:02:10 Q1 kernel: [   17.122826] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
Aug  1 18:02:10 Q1 kernel: [   17.122845] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Aug  1 18:02:10 Q1 kernel: [   17.122852] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Aug  1 18:02:10 Q1 kernel: [   17.122893] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Aug  1 18:02:10 Q1 kernel: [   17.122922] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800
Aug  1 18:02:10 Q1 kernel: [   17.123113] usb usb4: configuration #1 chosen from 1 choice
Aug  1 18:02:10 Q1 kernel: [   17.123155] hub 4-0:1.0: USB hub found
Aug  1 18:02:10 Q1 kernel: [   17.123165] hub 4-0:1.0: 2 ports detected
Aug  1 18:02:10 Q1 kernel: [   17.207832] SCSI subsystem initialized
Aug  1 18:02:10 Q1 kernel: [   17.226715] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
Aug  1 18:02:10 Q1 kernel: [   17.226741] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Aug  1 18:02:10 Q1 kernel: [   17.226747] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug  1 18:02:10 Q1 kernel: [   17.226791] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Aug  1 18:02:10 Q1 kernel: [   17.230692] ehci_hcd 0000:00:1d.7: debug port 1
Aug  1 18:02:10 Q1 kernel: [   17.230700] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
Aug  1 18:02:10 Q1 kernel: [   17.230714] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebffc00
Aug  1 18:02:10 Q1 kernel: [   17.258457] usb 2-1: new full speed USB device using uhci_hcd and address 2
Aug  1 18:02:10 Q1 kernel: [   17.269673] libata version 3.00 loaded.
Aug  1 18:02:10 Q1 kernel: [   17.272457] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug  1 18:02:10 Q1 kernel: [   17.272669] usb usb5: configuration #1 chosen from 1 choice
Aug  1 18:02:10 Q1 kernel: [   17.272715] hub 5-0:1.0: USB hub found
Aug  1 18:02:10 Q1 kernel: [   17.272727] hub 5-0:1.0: 8 ports detected
Aug  1 18:02:10 Q1 kernel: [   17.374430] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Aug  1 18:02:10 Q1 kernel: [   17.374443] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Aug  1 18:02:10 Q1 kernel: [   17.374502] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Aug  1 18:02:10 Q1 kernel: [   17.374519] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Aug  1 18:02:10 Q1 kernel: [   17.374539] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
Aug  1 18:02:10 Q1 kernel: [   17.374573] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Aug  1 18:02:10 Q1 kernel: [   17.374586] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Aug  1 18:02:10 Q1 kernel: [   17.376189] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
Aug  1 18:02:10 Q1 kernel: [   17.376195] e100: Copyright(c) 1999-2006 Intel Corporation
Aug  1 18:02:10 Q1 kernel: [   17.376280] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 20
Aug  1 18:02:10 Q1 kernel: [   17.398829] Floppy drive(s): fd0 is 1.44M
Aug  1 18:02:10 Q1 kernel: [   17.421854] FDC 0 is a post-1991 82077
Aug  1 18:02:10 Q1 kernel: [   17.450332] e100: eth0: e100_probe: addr 0xfeafe000, irq 20, MAC addr 00:0c:f1:c0:77:6b
Aug  1 18:02:10 Q1 kernel: [   17.450451] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 17 (level, low) -> IRQ 21
Aug  1 18:02:10 Q1 kernel: [   17.502234] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[feaff000-feaff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
Aug  1 18:02:10 Q1 kernel: [   17.601010] ata_piix 0000:00:1f.1: version 2.12
Aug  1 18:02:10 Q1 kernel: [   17.601044] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Aug  1 18:02:10 Q1 kernel: [   17.601109] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Aug  1 18:02:10 Q1 kernel: [   17.602178] scsi0 : ata_piix
Aug  1 18:02:10 Q1 kernel: [   17.602283] scsi1 : ata_piix
Aug  1 18:02:10 Q1 kernel: [   17.604555] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Aug  1 18:02:10 Q1 kernel: [   17.604561] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Aug  1 18:02:10 Q1 kernel: [   17.622810] usb 5-3: new high speed USB device using ehci_hcd and address 2
Aug  1 18:02:10 Q1 kernel: [   17.885395] usb 5-3: configuration #1 chosen from 1 choice
Aug  1 18:02:10 Q1 kernel: [   18.254035] ata1.00: ATAPI: ASUS DVD-ROM DVD-E616P              0104, E1.04, max UDMA/66
Aug  1 18:02:10 Q1 kernel: [   18.254069] ata1.01: ATAPI: SONY    CD-RW  CRX230E, QYS3, max UDMA/33
Aug  1 18:02:10 Q1 kernel: [   18.424663] ata1.00: configured for UDMA/66
Aug  1 18:02:10 Q1 kernel: [   18.596301] ata1.01: configured for UDMA/33
Aug  1 18:02:10 Q1 kernel: [   18.761238] ata2.00: ATA-7: Maxtor 6Y060L0, YAR41BW0, max UDMA/133
Aug  1 18:02:10 Q1 kernel: [   18.761242] ata2.00: 120103200 sectors, multi 16: LBA 
Aug  1 18:02:10 Q1 kernel: [   18.777128] ata2.00: configured for UDMA/100
Aug  1 18:02:10 Q1 kernel: [   18.779169] scsi 0:0:0:0: CD-ROM            ASUS     DVD-E616P        1.04 PQ: 0 ANSI: 5
Aug  1 18:02:10 Q1 kernel: [   18.780112] scsi 0:0:1:0: CD-ROM            SONY     CD-RW  CRX230E   QYS3 PQ: 0 ANSI: 5
Aug  1 18:02:10 Q1 kernel: [   18.780302] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6Y060L0   YAR4 PQ: 0 ANSI: 5
Aug  1 18:02:10 Q1 kernel: [   18.780402] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
Aug  1 18:02:10 Q1 kernel: [   18.780430] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
Aug  1 18:02:10 Q1 kernel: [   18.780490] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Aug  1 18:02:10 Q1 kernel: [   18.780570] scsi2 : ata_piix
Aug  1 18:02:10 Q1 kernel: [   18.780646] scsi3 : ata_piix
Aug  1 18:02:10 Q1 kernel: [   18.781744] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 18
Aug  1 18:02:10 Q1 kernel: [   18.781748] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 18
Aug  1 18:02:10 Q1 kernel: [   18.868760] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000cf10000c0776b]
Aug  1 18:02:10 Q1 kernel: [   18.984856] ata3.00: ATA-7: ST3320620AS, 3.AAK, max UDMA/133
Aug  1 18:02:10 Q1 kernel: [   18.984861] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
Aug  1 18:02:10 Q1 kernel: [   19.068014] ata3.00: configured for UDMA/133
Aug  1 18:02:10 Q1 kernel: [   19.233896] scsi 2:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
Aug  1 18:02:10 Q1 kernel: [   19.254985] Driver 'sr' needs updating - please use bus_type methods
Aug  1 18:02:10 Q1 kernel: [   19.258779] Driver 'sd' needs updating - please use bus_type methods
Aug  1 18:02:10 Q1 kernel: [   19.261005] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
Aug  1 18:02:10 Q1 kernel: [   19.261011] Uniform CD-ROM driver Revision: 3.20
Aug  1 18:02:10 Q1 kernel: [   19.261072] sr 0:0:0:0: Attached scsi CD-ROM sr0
Aug  1 18:02:10 Q1 kernel: [   19.266125] sr1: scsi3-mmc drive: 192x/52x writer cd/rw xa/form2 cdda tray
Aug  1 18:02:10 Q1 kernel: [   19.266190] sr 0:0:1:0: Attached scsi CD-ROM sr1
Aug  1 18:02:10 Q1 kernel: [   19.266332] sd 1:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
Aug  1 18:02:10 Q1 kernel: [   19.266356] sd 1:0:0:0: [sda] Write Protect is off
Aug  1 18:02:10 Q1 kernel: [   19.266361] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug  1 18:02:10 Q1 kernel: [   19.266400] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  1 18:02:10 Q1 kernel: [   19.266493] sd 1:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
Aug  1 18:02:10 Q1 kernel: [   19.266522] sd 1:0:0:0: [sda] Write Protect is off
Aug  1 18:02:10 Q1 kernel: [   19.266528] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug  1 18:02:10 Q1 kernel: [   19.266575] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  1 18:02:10 Q1 kernel: [   19.266581]  sda: sda1
Aug  1 18:02:10 Q1 kernel: [   19.273056] sd 1:0:0:0: [sda] Attached SCSI disk
Aug  1 18:02:10 Q1 kernel: [   19.273165] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
Aug  1 18:02:10 Q1 kernel: [   19.273189] sd 2:0:0:0: [sdb] Write Protect is off
Aug  1 18:02:10 Q1 kernel: [   19.273193] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Aug  1 18:02:10 Q1 kernel: [   19.273227] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  1 18:02:10 Q1 kernel: [   19.273299] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
Aug  1 18:02:10 Q1 kernel: [   19.273318] sd 2:0:0:0: [sdb] Write Protect is off
Aug  1 18:02:10 Q1 kernel: [   19.273322] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Aug  1 18:02:10 Q1 kernel: [   19.273354] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  1 18:02:10 Q1 kernel: [   19.273360]  sdb:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
Aug  1 18:02:10 Q1 kernel: [   19.275160] sr 0:0:1:0: Attached scsi generic sg1 type 5
Aug  1 18:02:10 Q1 kernel: [   19.275195] sd 1:0:0:0: Attached scsi generic sg2 type 0
Aug  1 18:02:10 Q1 kernel: [   19.275228] sd 2:0:0:0: Attached scsi generic sg3 type 0
Aug  1 18:02:10 Q1 kernel: [   19.290561]  sdb1 sdb2 sdb3 sdb4
Aug  1 18:02:10 Q1 kernel: [   19.302979] sd 2:0:0:0: [sdb] Attached SCSI disk
Aug  1 18:02:10 Q1 kernel: [   24.753784] kjournald starting.  Commit interval 5 seconds
Aug  1 18:02:10 Q1 kernel: [   24.753795] EXT3-fs: mounted filesystem with ordered data mode.
Aug  1 18:02:10 Q1 kernel: [   33.271613] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug  1 18:02:10 Q1 kernel: [   33.347378] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug  1 18:02:10 Q1 kernel: [   33.414900] Linux agpgart interface v0.102
Aug  1 18:02:10 Q1 kernel: [   33.467188] input: PC Speaker as /devices/platform/pcspkr/input/input2
Aug  1 18:02:10 Q1 kernel: [   33.518807] agpgart: Detected an Intel 865 Chipset.
Aug  1 18:02:10 Q1 kernel: [   33.522705] agpgart: AGP aperture is 64M @ 0xf8000000
Aug  1 18:02:10 Q1 kernel: [   33.585851] iTCO_vendor_support: vendor-support=0
Aug  1 18:02:10 Q1 kernel: [   33.677615] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Aug  1 18:02:10 Q1 kernel: [   33.678744] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
Aug  1 18:02:10 Q1 kernel: [   33.678826] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Aug  1 18:02:10 Q1 kernel: [   33.855558] input: Power Button (FF) as /devices/virtual/input/input3
Aug  1 18:02:10 Q1 kernel: [   33.873216] ACPI: Power Button (FF) [PWRF]
Aug  1 18:02:10 Q1 kernel: [   33.873396] input: Sleep Button (CM) as /devices/virtual/input/input4
Aug  1 18:02:10 Q1 kernel: [   33.897177] ACPI: Sleep Button (CM) [SLPB]
Aug  1 18:02:10 Q1 kernel: [   33.953764] Intel 82802 RNG detected
Aug  1 18:02:10 Q1 kernel: [   35.035122] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Aug  1 18:02:10 Q1 kernel: [   35.526388] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Aug  1 18:02:10 Q1 kernel: [   35.929825] parport_pc 00:09: reported by Plug and Play ACPI
Aug  1 18:02:10 Q1 kernel: [   35.929854] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Aug  1 18:02:10 Q1 kernel: [   36.077124] Linux video capture interface: v2.00
Aug  1 18:02:10 Q1 kernel: [   36.172613] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
Aug  1 18:02:10 Q1 kernel: [   36.172642] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Aug  1 18:02:10 Q1 kernel: [   36.534349] usbcore: registered new interface driver snd-usb-audio
Aug  1 18:02:10 Q1 kernel: [   36.540726] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
Aug  1 18:02:10 Q1 kernel: [   36.553350] usbcore: registered new interface driver uvcvideo
Aug  1 18:02:10 Q1 kernel: [   36.553363] USB Video Class driver (v0.1.0)
Aug  1 18:02:10 Q1 kernel: [   36.596420] intel8x0_measure_ac97_clock: measured 55865 usecs
Aug  1 18:02:10 Q1 kernel: [   36.596427] intel8x0: clocking to 48000
Aug  1 18:02:10 Q1 kernel: [   37.040191] NET: Registered protocol family 17
Aug  1 18:02:10 Q1 kernel: [   37.777178] lp0: using parport0 (interrupt-driven).
Aug  1 18:02:10 Q1 kernel: [   38.526069] EXT3 FS on sdb1, internal journal
Aug  1 18:02:10 Q1 kernel: [   38.676881] device-mapper: uevent: version 1.0.3
Aug  1 18:02:10 Q1 kernel: [   38.676932] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
Aug  1 18:02:10 Q1 kernel: [   40.111098] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug  1 18:02:10 Q1 kernel: [   41.762099] NET: Registered protocol family 10
Aug  1 18:02:10 Q1 kernel: [   41.762623] lo: Disabled Privacy Extensions
Aug  1 18:02:10 Q1 kernel: [   52.588366] eth0: no IPv6 routers present
Aug  1 18:02:10 Q1 kernel: [  111.591210] No dock devices found.
Aug  1 18:02:10 Q1 kernel: [  113.063908] ppdev: user-space parallel port driver
Aug  1 18:02:10 Q1 kernel: [  113.314362] audit(1280710930.811:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5401 profile="/usr/sbin/cupsd" namespace="default"
Aug  1 18:02:10 Q1 kernel: [  113.356575] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug  1 18:02:10 Q1 kernel: [  113.356586] apm: disabled - APM is not SMP safe.

---

### Post by calvert888 on 2010-08-02
Any ideas?

I'm about *this* close to reinstalling at this point, which I would really rather not do.

Please help...

---

