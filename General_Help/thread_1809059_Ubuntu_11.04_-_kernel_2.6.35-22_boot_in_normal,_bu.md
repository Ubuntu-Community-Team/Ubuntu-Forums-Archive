---
title: "Ubuntu 11.04 - kernel 2.6.35-22: boot in normal, but hangs in single user mode"
date: 2011-07-21
forum: General Help
---

### Post by Rockzz on 2011-07-21
Hello,

On a laptop upgraded to Natty amd64, with the latest ATI drivers manually packaged and installed as *.deb packages, I can't boot with the lastest 2.6.38-8 kernel, as many users.

So I boot through the 2.6.35-22 previous kernel : I can boot in normal user mode, but boot hangs in single user mode.

I really hold this as important : beeing able to rescue my system if something goes wrong, without having to fight with a live CD and chroot in the faulty system (had to do this a few time ago in fact) :p

Here is the end of the failed boot log, from /var/log/syslog. Note the time jump from "03:34:56" to "03:36:00", it occurs upon a Ctrl+Alt+Suppr keys press after waiting a little while hanged. At "03:34:56", I can see my router blinking all lights at once, then some blinks then nothing, looks like a DHCP request from the booting linux that get no offer or so. After the hotkeys shortcut press, I can read "Stopping GNOME desktop" or so (I believe this has no reason to start in single user mode btw, but may be wrong).

```

Jul 21 03:29:10 sbdwad7 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.35-22-generic root=/dev/mapper/<root_lv_name> ro single
...
Jul 21 03:29:15 sbdwad7 avahi-daemon[1248]: New relevant interface eth0.IPv6 for mDNS.
Jul 21 03:29:15 sbdwad7 avahi-daemon[1248]: Registering new address record for fe80::21e:33ff:fe5b:c536 on eth0.*.
Jul 21 03:29:24 sbdwad7 kernel: [   51.120078] eth0: no IPv6 routers present
Jul 21 03:33:28 sbdwad7 NetworkManager[1252]: <info> (eth0): carrier now OFF (device state 3)
Jul 21 03:33:28 sbdwad7 NetworkManager[1252]: <info> (eth0): device state change: 3 -> 2 (reason 40)
Jul 21 03:33:28 sbdwad7 NetworkManager[1252]: <info> (eth0): deactivating device (reason: 40).
Jul 21 03:33:28 sbdwad7 kernel: [  295.120649] r8169 0000:02:00.0: eth0: link down
Jul 21 03:33:36 sbdwad7 NetworkManager[1252]: <info> (eth0): carrier now ON (device state 2)
Jul 21 03:33:36 sbdwad7 NetworkManager[1252]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Jul 21 03:33:36 sbdwad7 kernel: [  302.512186] r8169 0000:02:00.0: eth0: link up
Jul 21 03:34:56 sbdwad7 kernel: Kernel logging (proc) stopped.
Jul 21 03:34:56 sbdwad7 rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="1215" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jul 21 03:36:00 sbdwad7 kernel: imklog 4.6.4, log source = /proc/kmsg started.
Jul 21 03:36:00 sbdwad7 rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="966" x-info="http://www.rsyslog.com"] (re)start
Jul 21 03:36:00 sbdwad7 rsyslogd: rsyslogd's groupid changed to 103
Jul 21 03:36:00 sbdwad7 rsyslogd: rsyslogd's userid changed to 101
Jul 21 03:36:00 sbdwad7 rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jul 21 03:36:00 sbdwad7 kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 21 03:36:00 sbdwad7 kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 21 03:36:00 sbdwad7 kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)

```Here are a bunch of other info and some issues I'm getting, not to solve them all in once, but to provide hints on the problem context, if you need so :
 - sda is LUKS/LVM2 encrypted
 - Could initially boot consistently in the latest kernel, with ATI proprietary installed, but only after a soft reboot (on first boot: purple screen)
 - An update installed a 2.6.38-10 kernel, probably from the maverick 2.6.35-22 one. I decided to clean some previous kernels : removed 2.6.38-10 and 2.6.35-22 to only keep 2.6.38-8 (big mistake)
 - Uninstalled the ATI drivers through synaptic to reinstall them clean : no boot in normal and single user modes
 - Downloaded manually and reinstalled a 2.6.25-22 kernel, the same ATI packages than initially, cleared and reinstalled grub 1.99, from a Ubuntu live CD chroot (a "Previous kernels" entry went back in grub, but now /vmlinuz --> 2.6.35-22 and /vmlinuz.old --> 2.6.38-10 . I believe this should normally be the opposite. I didn't pin the 2.6.35-22 packages to hold them, since I have no knowledge in the pinning mechanism)
 - Since then : SSH hosts names resolution is broken (some hosts are still found, some others are not : nothing changed in ~/.ssh/*, driven by network-manager and its VPN plugin)
 - Initially, the "su" command did print an explicit message meaning there is no root user on Ubuntu I believe. I once activated, then properly deactivated it. Now, a "su' give me a prompt, but I can't find the password to get in, so it really looks deactivated. If not, it could explain why I cannot get to a root prompt as a single user

Thanks for help !

---

