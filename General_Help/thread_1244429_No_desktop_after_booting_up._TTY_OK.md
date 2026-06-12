---
title: "No desktop after booting up. TTY OK"
date: 2009-08-19
forum: General Help
---

### Post by miguel64086 on 2009-08-19
This is a very weird one.
I have Ubuntu 9.04 and this started happening right after a mandatory reboot after some package updates.

The PC goes to GRUB and after I select Ubuntu, it start to load and right before the desktop is suppose to appear, it the monitor shuts down, as if the video card stops sending a signal. The monitor then goes into power saving mode and shuts down.
After a few secs, I can hear the ubuntu music that indicates it finished loading.

1- At that point I can SSH and I can use VNCViewer to remote to the desktop... but I can't use the actual monitor attached to the PC.
2- I can even go into TTY... but no desktop.
3- I can even boot into WinXP... but would want to do that? ;)
4- If I try to load the CD-live... same behavior
5- I can even access my files on my Samba share!
6- I boot up on SAFE MODE... went through a couple of stuff and same thing
7- I tried to repair graphical errors... same stuff.
8- Repair broken packages, no luck
9- Use VNC Viewer to ran the Janitor... no luck

I recently upgraded the RAM from 1 GB to 4 GB... it worked for a while... but once in a while I get a message at the BIOS saying "overclocking failed". I bought this PC at this local store and I'm afraid they overclock it to make it faster than it is and didn't tell me. But why would they don't tell? I mean... they didn't charge me for it... I don't know how to overclock it, even of course I don't know how to revert it either. I guess that would be my last option.


Any help would be appreciated.

Current Version:
Linux <host> 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

I read the dmesg stuff... but no idea what they mean:

The only two things that I notice are:
1- [ 25.960858] [drm:i915_setparam] *ERROR* unknown parameter 4
[ 25.960890] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 26.911438] [drm:i915_getparam] *ERROR* Unknown parameter 6

which according to this link is a known bug.

2- AMI BIOS detected: BIOS may corrupt low RAM, working it around.
which I have no clue what it means

---

### Post by VipX1 on 2009-08-19
It's not the overlocking if there is any for sure. If XP runs then it is harder on the CPU than Ubuntu so it's not CPU related..
You could upgrade your visual effects with VNC, that would force Ubuntu to look for graphics drivers. Also in synaptic there's utilities for the different graphics cards that you can install.. What graphics card do you have? What motherboard?

---

### Post by miguel64086 on 2009-08-20
Here are my specs
Thank so much for your help.
I'll try to update the visual effects tomorrow.
:)


id:	
core
description: 	Motherboard
product: 	P5L-VM 1394
vendor: 	ASUSTeK Computer INC.
physical id: 	
0
version: 	Rev 1.xx
serial: 	MB-1234567890
slot: 	To Be Filled By O.E.M.

id:	
firmware
description: 	BIOS
vendor: 	American Megatrends Inc.
physical id: 	
0
version: 	0802 (03/19/2007)
size: 	64KiB
capacity: 	448KiB
capabilities: 	isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification

id:	
display
description: 	VGA compatible controller
product: 	82945G/GZ Integrated Graphics Controller
vendor: 	Intel Corporation
physical id: 	
2
bus info: 	
pci@0000:00:02.0
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	msi pm bus_master cap_list
configuration:	
latency	=	0

---

### Post by miguel64086 on 2009-08-21
OK... I found this
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

to roll back the driver to 2.4 for my intel graphic card...
and it did not help

any more suggestions?

---

### Post by bchurchill on 2009-08-22
Since you did upgrade memory recently, I would run memtest off of a live CD just to be safe.  Memory does weird things...

So this happened after mandatory updates?  But why would the live CD be affected by that?  That seems to imply (at least to me, I could be wrong) this is a hardware issue.  It seems like X is having issues with your video device.  Try running

```
xinit
```or

```
startx
```from a tty.

and just out of curiosity,

```
 ps -e | grep gnome 
```


EDIT: also check log files: /var/log/syslog, /var/log/messages, /var/log/Xorg*

---

### Post by miguel64086 on 2009-08-26
Sorry for the late response... I know you are trying to help me and I really appreciate it.

When I go to TTY and do
sudo startx, I get
X: warning; process set to priority -1 instead of requested priority 0
Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again.

Please consult the The X.org Foundation support at...
ddxSigGiveUp: Closing log.

If I do 
sudo xinit same thing

If I remove the file .X0-lock I get pretty much same error, but this time ask me to check another log file which says 
xf860OpenConsole: VT_GETSTATE failed: Bad file descriptor.

-===============================================

when I do
ps -e | grep gnome, I get the following processes running:
gnome-settings-
gnome-keyring-d
gnome-panel
gnome-power-man
gnome-screensav

BTW... I run the memory check and it was fine.

On the Xorg.0.log no errors or warnings.
On the messages, it ends with
Aug 26 21:07:16 inca syslogd 1.5.0#5ubuntu3: restart.
Aug 26 21:07:16 inca kernel: Inspecting /boot/System.map-2.6.28-15-generic
Aug 26 21:07:16 inca kernel: Cannot find map file.
Aug 26 21:07:16 inca kernel: Loaded 58082 symbols from 70 modules.
Aug 26 21:07:16 inca kernel: [ 1731.334772] NetworkManager[8790]: segfault at 18 ip b7dff23d sp bfa0dc70 error 4 in libdbus-1.so.3.4.0[b7de3000+36000]
Aug 26 21:07:19 inca pulseaudio[11968]: pid.c: Stale PID file, overwriting.



Now... on the syslog I get the following:

Aug 26 21:07:16 inca syslogd 1.5.0#5ubuntu3: restart.
Aug 26 21:07:16 inca kernel: Inspecting /boot/System.map-2.6.28-15-generic
Aug 26 21:07:16 inca kernel: Cannot find map file.
Aug 26 21:07:16 inca kernel: Loaded 58082 symbols from 70 modules.
Aug 26 21:07:16 inca kernel: [ 1731.334772] NetworkManager[8790]: segfault at 18 ip b7dff23d sp bfa0dc70 error 4 in libdbus-1.so.3.4.0[b7de3000+36000]
Aug 26 21:07:16 inca ntpd[11346]: ntpd 4.2.4p4@1.1520-o Wed May 13 21:05:42 UTC 2009 (1)
Aug 26 21:07:16 inca ntpd[11347]: precision = 1.000 usec
Aug 26 21:07:16 inca ntpd[11347]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Aug 26 21:07:16 inca ntpd[11347]: Listening on interface #1 wildcard, ::#123 Disabled
Aug 26 21:07:16 inca ntpd[11347]: Listening on interface #2 lo, ::1#123 Enabled
Aug 26 21:07:16 inca ntpd[11347]: Listening on interface #3 eth0, fe80::21b:fcff:fe21:1aae#123 Enabled
Aug 26 21:07:16 inca ntpd[11347]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Aug 26 21:07:16 inca ntpd[11347]: Listening on interface #5 eth0, 192.168.1.101#123 Enabled
Aug 26 21:07:16 inca ntpd[11347]: kernel time sync status 0040
Aug 26 21:07:16 inca ntpd[11347]: frequency initialized 21.348 PPM from /var/lib/ntp/ntp.drift
Aug 26 21:07:17 inca acpid: client connected from 11514[111:122] 
Aug 26 21:07:17 inca bluetoothd[11531]: Bluetooth daemon
Aug 26 21:07:17 inca bluetoothd[11531]: Starting SDP server
Aug 26 21:07:17 inca bluetoothd[11531]: bridge pan0 created
Aug 26 21:07:17 inca bluetoothd[11531]: Starting experimental netlink support
Aug 26 21:07:17 inca bluetoothd[11531]: Failed to find Bluetooth netlink family
Aug 26 21:07:17 inca bluetoothd[11531]: Registered interface org.bluez.Service on path /org/bluez/11531/any
Aug 26 21:07:17 inca NetworkManager: <info>  starting... 
Aug 26 21:07:17 inca NetworkManager: <info>  (eth0): new Ethernet device (driver: 'atl1') 
Aug 26 21:07:17 inca NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_1b_fc_21_1a_ae 
Aug 26 21:07:17 inca NetworkManager: <info>  (ttyS0): ignoring due to lack of mobile broadband capabilties 
Aug 26 21:07:17 inca NetworkManager: <info>  Trying to start the supplicant... 
Aug 26 21:07:17 inca NetworkManager: <info>  Trying to start the system settings daemon... 
Aug 26 21:07:17 inca NetworkManager: <info>  (eth0): carrier now ON (device state 1) 
Aug 26 21:07:17 inca nm-system-settings:    SCPlugin-Ifupdown: init!
Aug 26 21:07:17 inca nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Aug 26 21:07:17 inca nm-system-settings:    SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet
Aug 26 21:07:17 inca nm-system-settings:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, autoconnect:0, id:Ifupdown (eth0), uuid: 681b428f-0000-0000-0000-000039000000
Aug 26 21:07:17 inca nm-system-settings:    SCPlugin-Ifupdown: autoconnect
Aug 26 21:07:17 inca nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Aug 26 21:07:17 inca nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1b_fc_21_1a_ae, iface: eth0): well known
Aug 26 21:07:17 inca nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Aug 26 21:07:17 inca nm-system-settings:    SCPlugin-Ifupdown: (165369600) ... get_connections.
Aug 26 21:07:17 inca nm-system-settings:    SCPlugin-Ifupdown: (165369600) ... get_connections (managed=false): return empty list.
Aug 26 21:07:17 inca nm-system-settings:    Ifupdown: get unmanaged devices count: 1
Aug 26 21:07:17 inca nm-system-settings:    SCPlugin-Ifupdown: end _init.
Aug 26 21:07:17 inca nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 26 21:07:17 inca nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 26 21:07:17 inca NetworkManager: <info>  (eth0): now unmanaged 
Aug 26 21:07:17 inca acpid: client connected from 11567[0:0] 
Aug 26 21:07:17 inca avahi-daemon[11598]: Found user 'avahi' (UID 110) and group 'avahi' (GID 121).
Aug 26 21:07:17 inca avahi-daemon[11598]: Successfully dropped root privileges.
Aug 26 21:07:17 inca avahi-daemon[11598]: avahi-daemon 0.6.23 starting up.
Aug 26 21:07:17 inca avahi-daemon[11598]: Successfully called chroot().
Aug 26 21:07:17 inca avahi-daemon[11598]: Successfully dropped remaining capabilities.
Aug 26 21:07:17 inca avahi-daemon[11598]: No service file found in /etc/avahi/services.
Aug 26 21:07:17 inca avahi-daemon[11598]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
Aug 26 21:07:17 inca avahi-daemon[11598]: New relevant interface eth0.IPv4 for mDNS.
Aug 26 21:07:17 inca avahi-daemon[11598]: Network interface enumeration completed.
Aug 26 21:07:17 inca avahi-daemon[11598]: Registering new address record for fe80::21b:fcff:fe21:1aae on eth0.*.
Aug 26 21:07:17 inca avahi-daemon[11598]: Registering new address record for 192.168.1.101 on eth0.IPv4.
Aug 26 21:07:17 inca avahi-daemon[11598]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 26 21:07:18 inca anacron[11707]: Anacron 2.3 started on 2009-08-26
Aug 26 21:07:18 inca anacron[11707]: Normal exit (0 jobs run)
Aug 26 21:07:18 inca /usr/sbin/cron[11750]: (CRON) INFO (pidfile fd = 3)
Aug 26 21:07:18 inca /usr/sbin/cron[11751]: (CRON) STARTUP (fork ok)
Aug 26 21:07:18 inca /usr/sbin/cron[11751]: (CRON) INFO (Skipping @reboot jobs -- not system startup)
Aug 26 21:07:18 inca avahi-daemon[11598]: Server startup complete. Host name is inca.local. Local service cookie is 2323498329.
Aug 26 21:07:19 inca console-kit-daemon[11369]: WARNING: Couldn't read /proc/11368/environ: Failed to open file '/proc/11368/environ': No such file or directory 
Aug 26 21:07:19 inca pulseaudio[11968]: pid.c: Stale PID file, overwriting.
Aug 26 21:07:21 inca pulseaudio[11968]: module-x11-xsmp.c: X11 session manager not running.
Aug 26 21:07:21 inca pulseaudio[11968]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Aug 26 21:07:22 inca NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Aug 26 21:07:22 inca NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Aug 26 21:07:26 inca ntfs-3g[12213]: Version 2009.2.1 external FUSE 27 
Aug 26 21:07:26 inca ntfs-3g[12213]: Mounted /dev/sdb5 (Read-Write, label "Whoopty", NTFS 3.1) 
Aug 26 21:07:26 inca ntfs-3g[12213]: Cmdline options: rw,nosuid,nodev,uhelper=hal,locale=en_US.UTF-8 
Aug 26 21:07:26 inca ntfs-3g[12213]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,fsname=/dev/sdb5,blkdev,blksize=4096 
Aug 26 21:07:26 inca hald: mounted /dev/sdb5 on behalf of uid 1000
Aug 26 21:08:21 inca kernel: [ 1807.992171] [drm:i915_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 1




no idea what it means or if the errors are meaningful... google fails me on this  :(


Thank you for your help

---

### Post by bchurchill on 2009-08-26
I'm certainly no expert on these matters either and don't know a lot.  It looks like x and gnome have started... but for some reason they can't output to the screen.  This suggests a video card/driver problem.  I just noticed that you mentioned you had updated things on your computer.  So a driver probably got upgraded without your permission.  It's slightly possible there's already a fix:

```

sudo apt-get update && sudo apt-get upgrade

```If not, you may consider filing a bug report, since this doesn't sound like something that would affect just you.  

Also look in your /ect/X11 for xorg.conf and possibly a backup file.  If there's a backup file you can try restoring it.  Another option is to move the xorg.conf file somewhere else and start X without one, which will force it to use default settings.  (And if those work, you can check the xorg logs to get the settings used and put that in xorg.conf, but this is unneccessary)

If that fails, try reconfiguring x:

```

sudo dpkg-reconfigure xserver-xorg

```This will update the xorg configuration files, and (hopefully) will use a different video driver.  However I don't really know how the xorg config works...

Your syslog and dmesg show nothing unusual.

---

### Post by miguel64086 on 2009-08-27
OK... thank you for your help, but it did not work.

I already had tried sudo apt-get update && sudo apt-get upgrade  before, and I tried it again, with no luck.
Reconfiguring X.org did not work either...
Deleting xorg.conf did not work either... after doing that, I could not even startX.
it gave errors the same errors than before...

I think I'm going to have to wipe my PC clean and reinstall from scratch

---

