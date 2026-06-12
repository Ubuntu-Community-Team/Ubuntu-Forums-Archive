---
title: "always going single user after boot"
date: 2010-11-22
forum: General Help
---

### Post by robmiller on 2010-11-22
I'm running mythbuntu on 10.04 with an AMD athlon and nvidia geforce4 (nvidia-96) graphics.  Shortly into the boot procedure, the system appears to switch into single user mode, killing all the processes I want running and dropping me into the recovery menu.  

On 20 Nov I was having problems booting the system, which I traced to a probably loose sata cable to the (single) hard drive.  While working on this I performed a normal system update, and then started having the problem described above.  the update included 

menu 2.1.43ubuntu1
libc-bin 2.11.1-0ubuntu7.5
plymouth 0.8.2-2ubuntu2.1
grub-pc 1.98-1ubuntu8
xserver-xorg-core 2:1.7.6-2ubuntu7.4
initramfs-tools 0.92bubuntu78

amongst other things.  I'm not posting over in the 'install/updates' forum as no one else seems to have the problem, and my current hypothesis is that this is the result of a corrupted file somewhere while having the disk problems.

boot.log pretty much sums up what is happening (the fsck is just on my most recent boot):

```

root@media:~# cat /var/log/boot.log 
fsck from util-linux-ng 2.17.2
/dev/sda1 has been mounted 20 times without being checked, check forced.
/dev/sda1: 222668/60768256 files (12.7% non-contiguous), 199992605/243059425 blocks
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
Loading the saved-state of the serial devices... 
Skip stopping firewall: ufw (not enabled)
 * Asking all remaining processes to terminate...

```after this I get various messages about services being shut down, and definitely gdm gets killed. as you may see from the above, it appears to be working and then things start getting tuned off.  startx works; gdm-binary works; 'service gdm start' works though I may have to start dbus by hand as well.  

I can't find anything that is not working or at least failing with an error message, but of course it is not easy to separate problems from correct upstart state shutdowns:

```

Nov 22 12:04:00 media NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Nov 22 12:04:00 media NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Nov 22 12:04:00 media NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Nov 22 12:04:00 media rpc.statd[662]: Caught signal 15, un-registering and exiting.
Nov 22 12:04:00 media modem-manager: Caught signal 15, shutting down...
Nov 22 12:04:00 media init: plymouth main process (264) killed by TERM signal
Nov 22 12:04:00 media init: upstart-udev-bridge main process ended, respawning
Nov 22 12:04:00 media init: udev main process ended, respawning
Nov 22 12:04:00 media init: portmap main process (636) killed by TERM signal
Nov 22 12:04:00 media init: portmap main process ended, respawning

```I attach a sample bootchart for another view on what's happening.

My experience with ubuntu is relatively limited compared to other linuxen, and after banging my head on this for most of the weekend it really is time to ask for help.  Please, I would very much appreciate any insights or suggestions for ways to trace what is causing the system to switch out of the normal runlevel.

thanks,

rob.

---

### Post by amite on 2010-11-22
>  I'm running mythbuntu on 10.04 with an AMD athlon and nvidia geforce4  (nvidia-96) graphics.  Shortly into the boot procedure, the system  appears to switch into single user mode, killing all the processes I  want running and dropping me into the recovery menu.you should check your run level which possibly be 1 in ur case.change it to 5.follow instructions here 
[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)

---

### Post by robmiller on 2010-11-22
> **amite said:**
> you should check your run level which possibly be 1 in ur case.change it to 5.follow instructions here 
[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)

Thanks for the reply.  yes, runlevel reports '1 S' once I've logged in as root, so actually I'm in runlevel 'S' and upstart drops me into the recovery menu according to /etc/init/rcS.conf

telinit 2 reports on the vt 7 console a short list of successful service starts and then stops i/o on vt7, but now I can switch to vt 1 etc. to login.  syslog reports everything basically ok except 'plymouth-stop pre-start process (2420) terminated with status 1' which seems (?) ok.

shifting up through 3,4,5 reports tty's killed by term signal and similar 'terminated with status 1' for apport and plymouth-stop.  everything is fine for text login, though I do not get here with 'text' appended to the kernel command line.

this doesn't get gdm going of course because it is on upstart, and depends on dbus and mountall (to emit filesystem).  dbus claims it is running, but attempting to start mountall dumps a bunch of errors into syslog starting with ```
'NetworkManager: <WARN>  nm_dbus_manager_init_bus(): Could not get the system bus.  Make sure the message bus daemon is running!  Message: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused'
```so, dbus isn't really running, and stop/start doesn't fix it because /var/run/dbus/* doesn't get cleared out (why doesn't /etc/init/dbus.conf have a post-stop script to do this?).  but dbus was running before, and NetworkManager ran at least for a while until it catches signal 15 when it looks like the system is told to go into single user mode:

```

Nov 22 16:41:11 media NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 22 16:41:11 media NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Nov 22 16:41:11 media NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Nov 22 16:41:11 media NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Nov 22 16:41:11 media NetworkManager: <WARN>  nm_signal_handler(): Caught signal 15, shutting down normally.
Nov 22 16:41:11 media NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Nov 22 16:41:11 media modem-manager: Caught signal 15, shutting down...
Nov 22 16:41:11 media rpc.statd[757]: Caught signal 15, un-registering and exiting.
Nov 22 16:41:11 media init: plymouth main process (282) killed by TERM signal
Nov 22 16:41:11 media init: upstart-udev-bridge main process ended, respawning
Nov 22 16:41:11 media init: udev main process ended, respawning
Nov 22 16:41:11 media init: portmap main process (641) killed by TERM signal
Nov 22 16:41:11 media init: portmap main process ended, respawning
Nov 22 16:41:11 media init: ssh main process (697) terminated with status 255
Nov 22 16:41:11 media init: ssh main process ended, respawning
Nov 22 16:41:11 media init: statd main process ended, respawning
Nov 22 16:41:11 media init: idmapd main process (759) killed by TERM signal
Nov 22 16:41:11 media init: idmapd main process ended, respawning
Nov 22 16:41:12 media kernel: Kernel logging (proc) stopped.
Nov 22 16:41:12 media rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="688" x-info="http://www.rsyslog.com"] exiting on signal 15.
Nov 22 16:41:12 media kernel: imklog 4.2.0, log source = /proc/kmsg started.
Nov 22 16:41:12 media rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="820" x-info="http://www.rsyslog.com"] (re)start
Nov 22 16:41:12 media rsyslogd: rsyslogd's groupid changed to 102
Nov 22 16:41:12 media rsyslogd: rsyslogd's userid changed to 101
Nov 22 16:41:12 media rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Nov 22 16:41:12 media dhclient: bound to 192.168.1.18 -- renewal in 37554 seconds.
Nov 22 16:41:12 media kernel: [   10.954122] udev: starting version 151
Nov 22 16:41:12 media sm-notify[839]: Already notifying clients; Exiting!
Nov 22 16:41:12 media rpc.statd[849]: Version 1.1.6 Starting
Nov 22 16:41:12 media rpc.statd[849]: Flags: 
Nov 22 16:41:22 media kernel: imklog 4.2.0, log source = /proc/kmsg started.
Nov 22 16:41:22 media rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="909" x-info="http://www.rsyslog.com"] (re)start
Nov 22 16:41:22 media rsyslogd: rsyslogd's groupid changed to 102
Nov 22 16:41:22 media rsyslogd: rsyslogd's userid changed to 101
Nov 22 16:41:22 media rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Nov 22 16:41:22 media init: dbus main process (918) terminated with status 1
Nov 22 16:41:22 media init: dbus main process ended, respawning
Nov 22 16:41:22 media init: Unable to connect to the system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused

```there at the end of that snippet we see dbus stopping or being stopped (and unable to restart properly because of /var/run/dbus/*), but it looks to be 11 seconds after everything is being told to close up because the system is being told to go to single user mode.

bringing us back to the question of what is sending it into single user mode in the first place?  again, I can manually start the individual services as root to eventually get gdm up, suggesting that all the individual pieces are working.

Thanks for the suggestion though!  before playing with the telinit runlevels I had not confirmed that I could get to the normal multiuser login: prompt, but I think telinit only works on the sysv-rc stuff and doesn't trigger anything in upstart.

rob.

---

### Post by robmiller on 2010-11-22
aaaaarrrrrrgggggghhhhhhhhhh.....

at some point in the past I managed to change /etc/default/grub to contain 

# Uncomment to get a beep at grub start
GRUB_CMDLINE_LINUX="1 440 480"

instead of 

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"

this resulted in having a naked '1' on the kernel command line (/proc/cmdline) when processed by the grub-pc upgrade #-o

this digit is picked up by /etc/init/rc-sysinit as an instruction to override the default runlevel to 1.

So the correct debugging technique was to look more closely at the ways of specifying the the system runlevel (as usual it did what I told it) and therefore to look very closely at the kernel command line.

rob.

---

