---
title: "Xserver crashes and cannot boot to my ubuntu box"
date: 2010-06-01
forum: General Help
---

### Post by shahansudu on 2010-06-01
Hi,
   I had my laptop running for a while and when I got back screen saver has crashed. I couldent get it to give me anything that I can work on so had to do a hard reboot. Now I cannot get it to boot, when it reaches the point starting Xserver it fails and keeps trying in a loop. All the google searches I found relate to a bug and the situation is different where the systems were working. In my case I cannot even log into the machine. 

I have a Dell Latitude E6500 and running 9.04 64 bit, linux-headers-2.6.28-18-generic. Here's what I see in the syslog

```

Jun  1 11:19:11 shahan-research NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Jun  1 11:19:11 shahan-research NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Jun  1 11:19:11 shahan-research NetworkManager: <info>  Activation (eth0) successful, device activated. 
Jun  1 11:19:11 shahan-research NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Jun  1 11:19:12 shahan-research acpid: client 3660[0:0] has disconnected 
Jun  1 11:19:12 shahan-research acpid: client connected from 4057[0:0] 
Jun  1 11:19:14 shahan-research kernel: [   36.003588] [drm:i915_setparam] *ERROR* unknown parameter 4
Jun  1 11:19:14 shahan-research kernel: [   36.059051] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
Jun  1 11:19:17 shahan-research kernel: [   39.788047] eth0: no IPv6 routers present
Jun  1 11:19:17 shahan-research kernel: [   39.908054] [drm:i915_gem_idle] *ERROR* hardware wedged
Jun  1 11:19:17 shahan-research kernel: [   39.910099] [drm:gm45_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0
Jun  1 11:19:21 shahan-research acpid: client 4057[0:0] has disconnected 
Jun  1 11:19:21 shahan-research acpid: client connected from 4080[0:0] 
Jun  1 11:19:22 shahan-research kernel: [   44.731364] [drm:i915_setparam] *ERROR* unknown parameter 4
Jun  1 11:19:22 shahan-research kernel: [   44.786718] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
Jun  1 11:19:23 shahan-research ntpdate[4103]: adjust time server 91.189.94.4 offset 0.199370 sec
Jun  1 11:19:26 shahan-research kernel: [   48.640092] [drm:i915_gem_idle] *ERROR* hardware wedged
Jun  1 11:19:26 shahan-research kernel: [   48.642114] [drm:gm45_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0
Jun  1 11:19:27 shahan-research gdm[3652]: CRITICAL: gdm_config_value_get_bool: assertion `value->type == GDM_CONFIG_VALUE_BOOL' failed 
Jun  1 11:19:28 shahan-research vmnetBridge: RTM_NEWLINK: name:wlan0 index:4 flags:0x00001003 
Jun  1 11:19:28 shahan-research vmnetBridge: Can't remove interface wlan0 4 (does not exist). 
Jun  1 11:19:29 shahan-research acpid: client 4080[0:0] has disconnected 
Jun  1 11:19:29 shahan-research acpid: client connected from 4165[0:0] 
Jun  1 11:19:30 shahan-research kernel: [   52.775761] zenity[4184]: segfault at 400001c4f ip 00007ff12ab6bf19 sp 00007fffbaf99968 error 4 in libc-2.9.so[7ff12aaeb000+168000]
Jun  1 11:19:30 shahan-research kernel: [   52.800135] zenity[4198]: segfault at 400001c4f ip 00007f024c89af19 sp 00007fff02974e38 error 4 in libc-2.9.so[7f024c81a000+168000]
Jun  1 11:19:30 shahan-research gdm[4218]: WARNING: Display :0 is busy. There is another X server running already. 
Jun  1 11:19:31 shahan-research kernel: [   53.113169] mtrr: no MTRR for e0000000,1ff0000 found
Jun  1 11:19:32 shahan-research acpid: client 4165[0:0] has disconnected 
Jun  1 11:19:32 shahan-research acpid: client connected from 4228[0:0] 
Jun  1 11:19:34 shahan-research kernel: [   56.775784] [drm:i915_setparam] *ERROR* unknown parameter 4
Jun  1 11:19:34 shahan-research kernel: [   56.831090] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
Jun  1 11:19:38 shahan-research kernel: [   60.684061] [drm:i915_gem_idle] *ERROR* hardware wedged
Jun  1 11:19:38 shahan-research kernel: [   60.686093] [drm:gm45_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0
Jun  1 11:19:42 shahan-research acpid: client 4228[0:0] has disconnected 
Jun  1 11:19:42 shahan-research acpid: client connected from 4250[0:0] 
Jun  1 11:19:44 shahan-research kernel: [   66.511936] [drm:i915_setparam] *ERROR* unknown parameter 4
Jun  1 11:19:44 shahan-research kernel: [   66.567597] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
Jun  1 11:19:48 shahan-research kernel: [   70.420079] [drm:i915_gem_idle] *ERROR* hardware wedged
Jun  1 11:19:48 shahan-research kernel: [   70.422153] [drm:gm45_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0
Jun  1 11:19:52 shahan-research acpid: client 4250[0:0] has disconnected 
Jun  1 11:19:52 shahan-research acpid: client connected from 4270[0:0] 
Jun  1 11:19:54 shahan-research kernel: [   76.248313] [drm:i915_setparam] *ERROR* unknown parameter 4
Jun  1 11:19:54 shahan-research kernel: [   76.303768] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
Jun  1 11:19:58 shahan-research kernel: [   80.156074] [drm:i915_gem_idle] *ERROR* hardware wedged
Jun  1 11:19:58 shahan-research kernel: [   80.158185] [drm:gm45_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0
Jun  1 11:19:58 shahan-research vmnetBridge: RTM_NEWLINK: name:wlan0 index:4 flags:0x00001003 
Jun  1 11:19:58 shahan-research vmnetBridge: Can't remove interface wlan0 4 (does not exist). 
Jun  1 11:19:59 shahan-research gdm[4217]: CRITICAL: gdm_config_value_get_bool: assertion `value->type == GDM_CONFIG_VALUE_BOOL' failed 
Jun  1 11:20:00 shahan-research acpid: client 4270[0:0] has disconnected 
Jun  1 11:20:00 shahan-research acpid: client connected from 4330[0:0] 
Jun  1 11:20:01 shahan-research kernel: [   83.055680] zenity[4350]: segfault at 400001c4f ip 00007fd086d16f19 sp 00007fffc15548f8 error 4 in libc-2.9.so[7fd086c96000+168000]
Jun  1 11:20:01 shahan-research kernel: [   83.080652] zenity[4364]: segfault at 400001c4f ip 00007f3af41fcf19 sp 00007fff5861dd68 error 4 in libc-2.9.so[7f3af417c000+168000]
Jun  1 11:20:01 shahan-research gdm[4387]: WARNING: Display :0 is busy. There is another X server running already. 
Jun  1 11:20:01 shahan-research console-kit-daemon[3442]: WARNING: Couldn't read /proc/3441/environ: Failed to open file '/proc/3441/environ': No such file or directory 
Jun  1 11:20:01 shahan-research /USR/SBIN/CRON[4401]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun  1 11:20:01 shahan-research kernel: [   83.415735] mtrr: no MTRR for e0000000,1ff0000 found
Jun  1 11:20:03 shahan-research acpid: client 4330[0:0] has disconnected 
Jun  1 11:20:03 shahan-research acpid: client connected from 4485[0:0] 
Jun  1 11:20:05 shahan-research kernel: [   87.002374] [drm:i915_setparam] *ERROR* unknown parameter 4
Jun  1 11:20:05 shahan-research kernel: [   87.060831] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
Jun  1 11:20:08 shahan-research kernel: [   90.896304] [drm:i915_gem_idle] *ERROR* hardware wedged
Jun  1 11:20:08 shahan-research kernel: [   90.901706] [drm:gm45_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0
Jun  1 11:20:12 shahan-research acpid: client 4485[0:0] has disconnected 
Jun  1 11:20:12 shahan-research acpid: client connected from 4557[0:0] 
Jun  1 11:20:13 shahan-research kernel: [   95.822700] [drm:i915_setparam] *ERROR* unknown parameter 4
Jun  1 11:20:13 shahan-research kernel: [   95.878049] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
Jun  1 11:20:17 shahan-research kernel: [   99.728289] [drm:i915_gem_idle] *ERROR* hardware wedged
Jun  1 11:20:17 shahan-research kernel: [   99.733867] [drm:gm45_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0
Jun  1 11:20:21 shahan-research acpid: client 4557[0:0] has disconnected 
Jun  1 11:20:21 shahan-research acpid: client connected from 4573[0:0] 
Jun  1 11:20:23 shahan-research kernel: [  105.758508] [drm:i915_setparam] *ERROR* unknown parameter 4
Jun  1 11:20:23 shahan-research kernel: [  105.814079] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
Jun  1 11:20:27 shahan-research kernel: [  109.665269] [drm:i915_gem_idle] *ERROR* hardware wedged
Jun  1 11:20:27 shahan-research kernel: [  109.671057] [drm:gm45_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0
Jun  1 11:20:28 shahan-research init: tty4 main process (2338) killed by TERM signal
Jun  1 11:20:28 shahan-research init: tty5 main process (2339) killed by TERM signal
Jun  1 11:20:28 shahan-research init: tty2 main process (2343) killed by TERM signal
Jun  1 11:20:28 shahan-research init: tty3 main process (2345) killed by TERM signal
Jun  1 11:20:28 shahan-research init: tty6 main process (2346) killed by TERM signal
Jun  1 11:20:28 shahan-research init: tty1 main process (3994) killed by TERM signal
Jun  1 11:20:31 shahan-research kernel: [  113.053095] type=1503 audit(1275405631.130:17): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=0 name="/usr/local/lib/libz.so.1.2.5" pid=4702 profile="/usr/sbin/mysqld"
Jun  1 11:20:31 shahan-research mysqld_safe[4714]: ended
Jun  1 11:20:32 shahan-research kernel: [  114.106564] type=1503 audit(1275405632.181:18): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=0 name="/usr/local/lib/libz.so.1.2.5" pid=4718 profile="/usr/sbin/mysqld"
Jun  1 11:20:35 shahan-research vmnetBridge: RTM_DELLINK: name:pan0 index:7 flags:0x00001002 
Jun  1 11:20:35 shahan-research vmnetBridge: Can't remove interface pan0 7 (does not exist). 
Jun  1 11:20:35 shahan-research bluetoothd[3618]: bridge pan0 removed
Jun  1 11:20:35 shahan-research bluetoothd[3618]: Stopping SDP server
Jun  1 11:20:35 shahan-research bluetoothd[3618]: Exit
Jun  1 11:20:35 shahan-research exiting on signal 15

```

any help is greatly appreciated.. looking for a fix that will let me log into my machine

---

### Post by TeoBigusGeekus on 2010-06-01
If you can get in a terminal (boot in safe mode), perhaps purging and then reinstalling gdm will do something.

---

