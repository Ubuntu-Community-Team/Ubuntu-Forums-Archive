---
title: "On init crashing NetworkManager and other modules"
date: 2012-05-07
forum: General Help
---

### Post by b1gag3 on 2012-05-07
Hi there,

I got a problem with my ubuntu on my acer asprice one 722. All started with the upgrade from 11.10 to 12.04. At first my wifi didn't worked and after several updates my ethernet died. There's already a thread for this issues (see here [http://ubuntuforums.org/showthread.php?t=1971434](http://ubuntuforums.org/showthread.php?t=1971434)). At the moment my wifi is working, but with another problem. I must start the NetworkManager manually after the login.

This problem and several tries to solve it started at this point of the thread: [http://ubuntuforums.org/showthread.php?p=11906098#post11906098](http://ubuntuforums.org/showthread.php?p=11906098#post11906098)

Summary: 

[LIST]
[*] At startup (on logon-screen) Ubuntu plays a warning sound, but no popup or message appears.
[*] The network manager applet is missing after the login.
[*] Its not possible to start the applet with "nm-applet &"
[*] Starting the NetworkManager manually starts the applet, too.
[/LIST]

chilli555, the user who helped me to get a working wifi, "suggested" a solution published at comment #14 in [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/875539](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/875539)
But at /usr/sbin/ i got both directories "lightdm" and "gdm" and I don't know if I (safety first) should rename one of them without any problem.

logs
```
chris@Roncarli:~$ **nm-applet &**
[1] 2711
chris@Roncarli:~$ 
** (nm-applet:2711): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files
** Message: applet now removed from the notification area

** (nm-applet:2711): WARNING **: Failed to register as an agent: (2) The name org.freedesktop.NetworkManager was not provided by any .service files
** Message: Starting applet secret agent because GNOME Shell disappeared

** (nm-applet:2711): WARNING **: Failed to register as an agent: (2) The name org.freedesktop.NetworkManager was not provided by any .service files
```

**_yesterday_**
```
chris@Roncarli:~$ **dmesg | grep etwork**
[   18.433317] udevd[356]: renamed network interface eth0 to eth1
[   18.470800] type=1400 audit(1336301912.281:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=382 comm="apparmor_parser"
[   19.816343] init: network-manager main process (683) terminated with status 1
[   19.816439] init: network-manager main process ended, respawning
[   20.387274] type=1400 audit(1336301914.197:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=861 comm="apparmor_parser"
```

```
chris@Roncarli:~$ **sudo cat /var/log/syslog | grep etwork**
May  6 12:58:33 Roncarli avahi-daemon[739]: Network interface enumeration completed.
May  6 12:58:33 Roncarli kernel: [   18.470800] type=1400 audit(1336301912.281:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=382 comm="apparmor_parser"
May  6 12:58:33 Roncarli kernel: [   19.816343] init: network-manager main process (683) terminated with status 1
May  6 12:58:33 Roncarli kernel: [   19.816439] init: network-manager main process ended, respawning
May  6 12:58:34 Roncarli kernel: [   20.387274] type=1400 audit(1336301914.197:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=861 comm="apparmor_parser"
```

```
chris@Roncarli:~$ **sudo cat /var/log/syslog | grep init | tail -n25**
May  6 13:07:12 Roncarli kernel: [    0.000000] Memory: 3833196k/4440064k available (5825k kernel code, 77300k reserved, 2850k data, 740k init, 2997548k highmem)
May  6 13:07:12 Roncarli kernel: [    0.000000]       .init : 0xc1879000 - 0xc1932000   ( 740 kB)
May  6 13:07:12 Roncarli kernel: [    0.004080] Security Framework initialized
May  6 13:07:12 Roncarli kernel: [    0.004121] AppArmor: AppArmor initialized
May  6 13:07:12 Roncarli kernel: [    0.164970] devtmpfs: initialized
May  6 13:07:12 Roncarli kernel: [    0.170136] Trying to unpack rootfs image as initramfs...
May  6 13:07:12 Roncarli kernel: [    0.441742] SCSI subsystem initialized
May  6 13:07:12 Roncarli kernel: [    0.467462] pnp: PnP ACPI init
May  6 13:07:12 Roncarli kernel: [    0.757383] audit: initializing netlink socket (disabled)
May  6 13:07:12 Roncarli kernel: [    0.757408] type=2000 audit(1336309613.756:1): initialized
May  6 13:07:12 Roncarli kernel: [    0.878813] fuse init (API version 7.17)
May  6 13:07:12 Roncarli kernel: [    1.050418] Freeing initrd memory: 13792k freed
May  6 13:07:12 Roncarli kernel: [    1.644317] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
May  6 13:07:12 Roncarli kernel: [   18.749286] Bluetooth: HCI device and connection manager initialized
May  6 13:07:12 Roncarli kernel: [   18.749295] Bluetooth: HCI socket layer initialized
May  6 13:07:12 Roncarli kernel: [   18.749301] Bluetooth: L2CAP socket layer initialized
May  6 13:07:12 Roncarli kernel: [   18.757638] Bluetooth: SCO socket layer initialized
May  6 13:07:12 Roncarli kernel: [   18.838445] Bluetooth: RFCOMM TTY layer initialized
May  6 13:07:12 Roncarli kernel: [   18.838464] Bluetooth: RFCOMM socket layer initialized
May  6 13:07:12 Roncarli kernel: [   18.839339] init: network-manager main process (588) terminated with status 1
May  6 13:07:12 Roncarli kernel: [   18.839430] init: network-manager main process ended, respawning
May  6 13:07:13 Roncarli kernel: [   19.428796] init: failsafe main process (682) killed by TERM signal
May  6 13:07:14 Roncarli kernel: [   20.918302] init: gdm main process (963) killed by TERM signal
May  6 13:12:41 Roncarli NetworkManager[3750]:    SCPlugin-Ifupdown: init!
May  6 13:12:41 Roncarli NetworkManager[3750]:    SCPlugin-Ifupdown: end _init.
```

_**today**_ (after installing lastest updates)
```
chris@Roncarli:~$ **dmesg | grep etwork**
[   11.229378] udevd[434]: renamed network interface eth0 to eth1
[   13.401141] type=1400 audit(1336408560.212:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=607 comm="apparmor_parser"
[   13.401348] type=1400 audit(1336408560.212:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=603 comm="apparmor_parser"
[   23.812795] init: network-manager main process (792) terminated with status 1
[   23.813011] init: network-manager main process ended, respawning
[   25.467099] type=1400 audit(1336408572.276:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=870 comm="apparmor_parser"
```

```
chris@Roncarli:~$ **sudo cat /var/log/syslog | grep init | tail -n25**
May  7 18:36:05 Roncarli kernel: [    0.004080] Security Framework initialized
May  7 18:36:05 Roncarli kernel: [    0.004118] AppArmor: AppArmor initialized
May  7 18:36:05 Roncarli kernel: [    0.164971] devtmpfs: initialized
May  7 18:36:05 Roncarli kernel: [    0.170083] Trying to unpack rootfs image as initramfs...
May  7 18:36:05 Roncarli kernel: [    0.441626] SCSI subsystem initialized
May  7 18:36:05 Roncarli kernel: [    0.467359] pnp: PnP ACPI init
May  7 18:36:05 Roncarli kernel: [    0.753387] audit: initializing netlink socket (disabled)
May  7 18:36:05 Roncarli kernel: [    0.753412] type=2000 audit(1336415746.752:1): initialized
May  7 18:36:05 Roncarli kernel: [    0.874818] fuse init (API version 7.17)
May  7 18:36:05 Roncarli kernel: [    1.047734] Freeing initrd memory: 13796k freed
May  7 18:36:05 Roncarli kernel: [    1.641876] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
May  7 18:36:06 Roncarli kernel: [   19.594399] init: failsafe main process (700) killed by TERM signal
May  7 18:36:09 Roncarli kernel: [   22.196198] Bluetooth: HCI device and connection manager initialized
May  7 18:36:09 Roncarli kernel: [   22.196207] Bluetooth: HCI socket layer initialized
May  7 18:36:09 Roncarli kernel: [   22.196213] Bluetooth: L2CAP socket layer initialized
May  7 18:36:09 Roncarli kernel: [   22.196228] Bluetooth: SCO socket layer initialized
May  7 18:36:09 Roncarli kernel: [   22.247432] Bluetooth: RFCOMM TTY layer initialized
May  7 18:36:09 Roncarli kernel: [   22.247446] Bluetooth: RFCOMM socket layer initialized
May  7 18:36:09 Roncarli bluetoothd[819]: Failed to init alert plugin
May  7 18:36:09 Roncarli bluetoothd[819]: Failed to init time plugin
May  7 18:36:10 Roncarli kernel: [   23.812795] init: network-manager main process (792) terminated with status 1
May  7 18:36:10 Roncarli kernel: [   23.813011] init: network-manager main process ended, respawning
May  7 18:36:10 Roncarli bluetoothd[819]: Failed to init proximity plugin
May  7 18:36:11 Roncarli bluetoothd[819]: Failed to init gatt_example plugin
May  7 18:36:14 Roncarli kernel: [   27.846893] init: gdm main process (951) killed by TERM signal
```

As you see today other and the gdm module will be terminated on the init process. The "crashing" bluetooth modules are maybe caused by the disabled bluetooth device. I guess the problem is the termininated gdm module. This maybe avoids the respawn of the networkmanager.

I hope somebody got any clue whats (not) happening on the startup. Let me know if you need more informations/logs.

regards,
b1gag3 | Chris

---

### Post by b1gag3 on 2012-05-09
*bump* :S

---

### Post by b1gag3 on 2012-05-22
You got to *bump* it up...

---

