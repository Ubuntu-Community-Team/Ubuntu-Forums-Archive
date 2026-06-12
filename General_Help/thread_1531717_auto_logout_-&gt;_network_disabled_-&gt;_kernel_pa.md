---
title: "auto logout -&gt; network disabled -&gt; kernel panic"
date: 2010-07-15
forum: General Help
---

### Post by wyssen on 2010-07-15
hi everyone

I run under a standard Ubuntu Lucid 64bit with the latest updates on a Acer TravelMate 6592. Recently (since one or two weeks) it happens to me that suddenly, during working with random programs (chrome, kile, gedit...), the system locks the screen. When I enter my password for unlocking it, there is a bubble displaying that the network was disabled in the upper right corner. And a few seconds after that, the system is blocked. I think it is a kernel panic, since I cannot switch to a TTY with ALT+Fx. So I have to press the power button...

After booting up again, I need to restart properly in order to make work again the Auto eth0 config from the network manager.
This is the syslog extract before the panic. I have two extracts from two different panics.
I would appreciate, if anybody could help me with this problem. It is really random and I can work some times like for the whole day and sometimes, it just occurs after a few minutes...

----------
```
Jul 15 17:44:39 wyssen-laptop kernel: [   52.640077] eth0: no IPv6 routers present
Jul 15 17:44:48 wyssen-laptop kernel: [   61.392642] wlan0: no IPv6 routers present
Jul 15 17:45:24 wyssen-laptop AptDaemon: INFO: Initializing daemon
Jul 15 17:46:08 wyssen-laptop kernel: [  141.640174] tpm_tis 00:0b: tpm_transmit: tpm_send: error -62
Jul 15 17:46:33 wyssen-laptop ntpdate[1774]: can't find host ntp.ubuntu.com
Jul 15 17:46:33 wyssen-laptop ntpdate[1774]: no servers can be used, exiting
Jul 15 17:47:05 wyssen-laptop init: udevtrigger post-stop process (501) terminated with status 1
Jul 15 17:47:06 wyssen-laptop udevd[402]: worker [438] unexpectedly returned with status 0x0100
Jul 15 17:47:06 wyssen-laptop udevd[402]: worker [438] failed while handling '/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:33/IFX0102:00'
Jul 15 17:48:10 wyssen-laptop kernel: [  263.900321] tpm_tis 00:0b: tpm_transmit: tpm_send: error -62
Jul 15 17:50:11 wyssen-laptop kernel: [  384.650109] tpm_tis 00:0b: tpm_transmit: tpm_send: error -62
Jul 15 17:51:24 wyssen-laptop AptDaemon: INFO: Quiting due to inactivity
Jul 15 17:51:24 wyssen-laptop AptDaemon: INFO: Shutdown was requested
Jul 15 17:54:02 wyssen-laptop kernel: [  615.582692] [drm:radeon_fence_wait] *ERROR* fence(ffff88007681ee80:0x00006473) 510ms timeout going to reset GPU
Jul 15 17:54:02 wyssen-laptop kernel: [  615.584118] [drm] CP reset succeed (RBBM_STATUS=0x9000C100)
Jul 15 17:54:02 wyssen-laptop kernel: [  615.584129] [drm] radeon: cp idle (0x10000000)
Jul 15 17:54:03 wyssen-laptop kernel: [  616.133123] radeon: wait for empty RBBM fifo failed ! Bad things might happen.
Jul 15 17:54:03 wyssen-laptop kernel: [  616.684727] Failed to wait GUI idle while programming pipes. Bad things might happen.
Jul 15 17:54:03 wyssen-laptop kernel: [  616.684763] [drm] radeon: ring at 0x0000000020000000
Jul 15 17:54:04 wyssen-laptop kernel: [  617.238175] [drm:r100_ring_test] *ERROR* radeon: ring test failed (sracth(0x15E4)=0xCAFEDEAD)
Jul 15 17:54:04 wyssen-laptop kernel: [  617.238180] [drm:r100_cp_init] *ERROR* radeon: cp isn't working (-22).
Jul 15 17:54:04 wyssen-laptop kernel: [  617.238186] [drm:rv515_gpu_reset] *ERROR* Failed to reset GPU (RBBM_STATUS=0x9001C100)
Jul 15 17:54:04 wyssen-laptop kernel: [  617.238193] [drm:radeon_fence_wait] *ERROR* fence(ffff88007681ee80:0x00006473) 2170ms timeout
Jul 15 17:54:04 wyssen-laptop kernel: [  617.238195] [drm:radeon_fence_wait] *ERROR* last signaled fence(0x00006473)
Jul 15 17:54:04 wyssen-laptop kernel: [  617.242605] [drm:radeon_fence_wait] *ERROR* fence(ffff88006f1693c0:0x00006476) 700ms timeout going to reset GPU
Jul 15 17:54:04 wyssen-laptop kernel: [  617.244023] [drm] CP reset succeed (RBBM_STATUS=0x9000C100)
Jul 15 17:54:04 wyssen-laptop kernel: [  617.244029] [drm:rv515_gpu_reset] *ERROR* Failed to reset GPU (RBBM_STATUS=0x9000C100)
Jul 15 17:54:04 wyssen-laptop kernel: [  617.244039] [drm:radeon_fence_wait] *ERROR* fence(ffff88006f1693c0:0x00006476) 710ms timeout
Jul 15 17:54:04 wyssen-laptop kernel: [  617.244042] [drm:radeon_fence_wait] *ERROR* last signaled fence(0x00006476)
Jul 15 17:54:04 wyssen-laptop kernel: [  617.244547] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(6).
Jul 15 17:54:04 wyssen-laptop kernel: [  617.244549] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Jul 15 17:54:04 wyssen-laptop kernel: [  617.244775] [drm:radeon_ib_schedule] *ERROR* radeon: couldn't schedule IB(7).
Jul 15 17:54:04 wyssen-laptop kernel: [  617.244777] [drm:radeon_cs_ioctl] *ERROR* Faild to schedule IB !
Jul 15 17:54:04 wyssen-laptop kernel:Jul 15 17:58:42 wyssen-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
```
----------



Second extract:
-----------
```
Jul 15 17:07:15 wyssen-laptop kernel: [  360.440344]  [<ffffffff8100a04c>] do_one_initcall+0x3c/0x1a0
Jul 15 17:07:15 wyssen-laptop kernel: [  360.440355]  [<ffffffff810a1a5f>] sys_init_module+0xdf/0x260
Jul 15 17:07:15 wyssen-laptop kernel: [  360.440365]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
Jul 15 17:07:37 wyssen-laptop dbus-daemon: Reloaded configuration
Jul 15 17:07:38 wyssen-laptop kernel: [  383.560094] tpm_tis 00:0b: tpm_transmit: tpm_send: error -62
Jul 15 17:07:38 wyssen-laptop kernel: [  383.560967] parport_pc 00:0a: unable to assign resources
Jul 15 17:07:38 wyssen-laptop kernel: [  383.560983] parport_pc: probe of 00:0a failed with error -16
Jul 15 17:07:42 wyssen-laptop dbus-daemon: Reloaded configuration
Jul 15 17:09:01 wyssen-laptop AptDaemon: INFO: Quiting due to inactivity
Jul 15 17:09:01 wyssen-laptop AptDaemon: INFO: Shutdown was requested
Jul 15 17:09:33 wyssen-laptop pulseaudio[1554]: ratelimit.c: 3 events suppressed
Jul 15 17:12:23 wyssen-laptop kernel: [  668.254330] CE: hpet increasing min_delta_ns to 15000 nsec
Jul 15 17:17:01 wyssen-laptop CRON[3321]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 15 17:23:34 wyssen-laptop kernel: [ 1339.573458] soffice.bin[3384]: segfault at 7ffc72e9ced9 ip 00007ffc72e9ced9 sp 00007ffc62451bd0 error 14 in libglib-2.0.so.0.2400.1[7ffc7313d000+db000]
Jul 15 17:26:57 wyssen-laptop kernel: [ 1543.082551] npviewer.bin[2060]: segfault at ff999ea8 ip 00000000ff999ea8 sp 00000000ffef5f8c error 14
Jul 15 17:28:18 wyssen-laptop kernel: [ 1623.472158] CE: hpet increasing min_delta_ns to 22500 nsec
Jul 15 17:29:43 wyssen-laptop avahi-daemon[983]: Invalid query packet.
Jul 15 17:30:38 wyssen-laptop avahi-daemon[983]: last message repeated 2 times
Jul 15 17:41:14 wyssen-laptop anacron[3625]: Anacron 2.3 started on 2010-07-15
Jul 15 17:41:14 wyssen-laptop anacron[3625]: Normal exit (0 jobs run)
Jul 15 17:41:15 wyssen-laptop NetworkManager: <info>  Sleeping...
Jul 15 17:41:15 wyssen-laptop NetworkManager: <info>  (eth0): now unmanaged
Jul 15 17:41:15 wyssen-laptop NetworkManager: <info>  (eth0): device state change: 8 -> 1 (reason 37)
Jul 15 17:41:15 wyssen-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 37).
Jul 15 17:41:15 wyssen-laptop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1322
Jul 15 17:41:15 wyssen-laptop NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Jul 15 17:41:15 wyssen-laptop avahi-daemon[983]: Withdrawing address record for 64.106.21.203 on eth0.
Jul 15 17:41:15 wyssen-laptop avahi-daemon[983]: Leaving mDNS multicast group on interface eth0.IPv4 with address 64.106.21.203.
Jul 15 17:41:15 wyssen-laptop avahi-daemon[983]: Interface eth0.IPv4 no longer relevant for mDNS.
Jul 15 17:41:15 wyssen-laptop NetworkManager: <info>  (eth0): cleaning up...
Jul 15 17:41:15 wyssen-laptop NetworkManager: <info>  (eth0): taking down device.
Jul 15 17:41:15 wyssen-laptop avahi-daemon[983]: Withdrawing address record for fe80::2a0:d1ff:fea1:ec66 on eth0.
Jul 15 17:41:15 wyssen-laptop NetworkManager: <info>  (wlan0): now unmanaged
Jul 15 17:41:15 wyssen-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 1 (reason 37)
Jul 15 17:41:15 wyssen-laptop NetworkManager: <info>  (wlan0): cleaning up...
Jul 15 17:41:15 wyssen-laptop NetworkManager: <info>  (eth0): carrier now OFF (device state 1)
Jul 15 17:42:25 wyssen-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jul 15 17:42:25 wyssen-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="972" x-info="http://www.rsyslog.com"] (re)start
Jul 15 17:42:25 wyssen-laptop rsyslogd: rsyslogd's groupid changed to 103
Jul 15 17:42:25 wyssen-laptop rsyslogd: rsyslogd's userid changed to 101
Jul 15 17:42:25 wyssen-laptop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jul 15 17:42:25 wyssen-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 15 17:42:25 wyssen-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 15 17:42:25 wyssen-laptop kernel: [    0.000000] Linux version 2.6.32-23-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 (Ubuntu 2.6.32-23.37-generic 2.6.32.15+drm33.5)
```
-----------

Thanks in advance

---

### Post by wyssen on 2010-07-19
Do you need anymore information about my system?

---

### Post by alm on 2010-10-26
Similar problem here. JUST INSTALLED A CLEAN ubuntu 10.10  64bits desktop edition. No problems reported during installation.

Just wanted to know if you could fix it somehow.

Curious thing is that I have an Acer TravelMate 6592G too.

Another curious thing is that gdm does not load automatically during the boot, it goes waiting something for about 3 minutes and then loads ok. Sometimes, instead of waiting 3 long minutes, I just start gdm manually (sudo gdm start) which works like a charm.

It also may be related to the sleep/wake up operation as it does not work. It sleeps the screen and the harddrive, but you can hear the fan not sleeping, also it does not wake up at all.

Randomly the screen goes totally black. No messages before the panic (networking wirelessly, not tested jet with eth connection). Not able to switch to tty or anything ...

The only thing working is to press the on/off button till power off.

While working ok (before the panics), if I switch to tty1 two messages appears:
[    8.021314] parport_pc 00:0a: unable to assign resources
[  130.340381] tpm_tis 00:0b: tpm_transmit: tpm_send: error -62


Don't even know where to look

ANY IDEA WILL HELP !!!

---

### Post by wyssen on 2010-10-28
Hi

I did not find any solution to that problem. But after a few weeks with it, it suddenly disapeared. I can not help you any further. Install all the latest updates, but if you tell me that you have a clean install, this should be the case...
sorry about that!

---

