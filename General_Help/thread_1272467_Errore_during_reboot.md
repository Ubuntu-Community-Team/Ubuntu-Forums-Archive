---
title: "Errore during reboot"
date: 2009-09-22
forum: General Help
---

### Post by Abdujaparov on 2009-09-22
Hi,
I've got a problem when I reboot my computer. After it's terminated the session the screen become black and the system doesn't reboot. I could wait for centuries but the screen remain black.
Where can I find the error? What is the error message file I have to look for?
I don't know what may be the cause, because I haven't got the error message.
Can somebody help me?
Thanks, bye bye.

---

### Post by schmidtbag on 2009-09-22
you should check one of the other consoles to see whats holding it back.  press ctrl+alt+F1 or F2 while its stuck and that should tell you more info.  give us as much info as you can that you think may be relateable to the problem.  also, do you know what you did last that may have caused this?

---

### Post by Abdujaparov on 2009-09-22
I have updated the system version from 8.10 to 9.04.
When I come back home I'll check.
Thanks.

---

### Post by Abdujaparov on 2009-09-23
Hi,
I tried to press crtl+alt+f1 or f2 when the screen is black but nothing happens, how can I find some messages?
Are the message saved in some files?
Thanks, bye bye.

---

### Post by scragar on 2009-09-23
Logs are stored in /var/log

---

### Post by Abdujaparov on 2009-09-23
In this file are there the information collected during the reboot of the system?
Thanks, again.
Bye bye.

---

### Post by P4man on 2009-09-23
have a look in system > adminstration > log file viewer.

---

### Post by Abdujaparov on 2009-09-30
Hi,
yesterday evening I had the same problem during the shut down.
I checked the log file and I found this:

**auth.log**
> 
Sep 29 23:50:01 angelo-ubuntu CRON[1829]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 29 23:50:01 angelo-ubuntu dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.35" (uid=1000 pid=6308 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.156" (uid=0 pid=1829 comm="/USR/SBIN/CRON "))
Sep 29 23:50:01 angelo-ubuntu CRON[1829]: pam_unix(cron:session): session closed for user root


**daemon.log**
> 
Sep 29 21:32:00 angelo-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected 
Sep 29 21:32:01 angelo-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Sep 29 21:32:05 angelo-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Sep 29 21:32:08 angelo-ubuntu NetworkManager: <debug> [1254252728.001517] periodic_update(): Roamed from BSSID 00:1C:F0:BA:A1:5E (default) to (none) ((none)) 
Sep 29 21:32:15 angelo-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Sep 29 21:32:15 angelo-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Sep 29 21:32:16 angelo-ubuntu NetworkManager: <info>  (wlan0): device state change: 8 -> 3 
Sep 29 21:32:16 angelo-ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 11). 
Sep 29 21:32:16 angelo-ubuntu NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 17594 
Sep 29 21:32:16 angelo-ubuntu NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Sep 29 21:32:16 angelo-ubuntu avahi-daemon[5620]: Withdrawing address record for 1.19.91.57 on wlan0.
Sep 29 21:32:16 angelo-ubuntu avahi-daemon[5620]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 1.19.91.57.
Sep 29 21:32:16 angelo-ubuntu avahi-daemon[5620]: Interface wlan0.IPv4 no longer relevant for mDNS.


**debug.log**
> 
Sep 29 21:32:00 angelo-ubuntu kernel: [26005.829090] wlan0: No ProbeResp from current AP 00:1c:f0:ba:a1:5e - assume out of range
Sep 29 21:32:05 angelo-ubuntu kernel: [26010.046632] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 29 21:32:05 angelo-ubuntu kernel: [26010.060808] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 29 21:32:05 angelo-ubuntu kernel: [26010.257111] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 29 21:32:05 angelo-ubuntu kernel: [26010.457096] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 29 21:32:05 angelo-ubuntu kernel: [26010.657088] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 29 21:32:08 angelo-ubuntu NetworkManager: <debug> [1254252728.001517] periodic_update(): Roamed from BSSID 00:1C:F0:BA:A1:5E (default) to (none) ((none)) 
Sep 29 21:32:16 angelo-ubuntu kernel: [26021.135491] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 29 21:32:16 angelo-ubuntu kernel: [26021.333126] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 29 21:32:16 angelo-ubuntu kernel: [26021.536668] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 29 21:32:16 angelo-ubuntu kernel: [26021.733045] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out


**kern.log**
> 
Sep 30 00:08:59 angelo-ubuntu kernel: [35424.181690] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:08:59 angelo-ubuntu kernel: [35424.188960] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:08:59 angelo-ubuntu kernel: [35424.388070] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:08:59 angelo-ubuntu kernel: [35424.592062] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:08:59 angelo-ubuntu kernel: [35424.790438] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:09:10 angelo-ubuntu kernel: [35435.225665] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:09:10 angelo-ubuntu kernel: [35435.232964] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:09:10 angelo-ubuntu kernel: [35435.429246] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:09:10 angelo-ubuntu kernel: [35435.628097] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:09:10 angelo-ubuntu kernel: [35435.828123] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:09:21 angelo-ubuntu kernel: [35446.198042] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:09:21 angelo-ubuntu kernel: [35446.205272] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:09:21 angelo-ubuntu kernel: [35446.405056] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:09:21 angelo-ubuntu kernel: [35446.605033] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:09:21 angelo-ubuntu kernel: [35446.805030] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:09:32 angelo-ubuntu kernel: [35457.273797] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:09:32 angelo-ubuntu kernel: [35457.282102] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:09:32 angelo-ubuntu kernel: [35457.484036] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:09:32 angelo-ubuntu kernel: [35457.682379] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:09:33 angelo-ubuntu kernel: [35457.881065] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:09:43 angelo-ubuntu kernel: [35468.232477] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:09:43 angelo-ubuntu kernel: [35468.239298] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:09:43 angelo-ubuntu kernel: [35468.245854] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:09:43 angelo-ubuntu kernel: [35468.445186] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:09:43 angelo-ubuntu kernel: [35468.645086] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:09:44 angelo-ubuntu kernel: [35468.845077] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:09:54 angelo-ubuntu kernel: [35479.297309] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:09:54 angelo-ubuntu kernel: [35479.304806] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:09:54 angelo-ubuntu kernel: [35479.504193] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:09:54 angelo-ubuntu kernel: [35479.704066] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:09:55 angelo-ubuntu kernel: [35479.907475] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:09:59 angelo-ubuntu kernel: [35483.870041] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:09:59 angelo-ubuntu kernel: [35484.068053] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:09:59 angelo-ubuntu kernel: [35484.268064] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:09:59 angelo-ubuntu kernel: [35484.472058] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:10:56 angelo-ubuntu kernel: [35541.556644] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:10:56 angelo-ubuntu kernel: [35541.563161] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:10:56 angelo-ubuntu kernel: [35541.761085] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:10:57 angelo-ubuntu kernel: [35541.961089] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:10:57 angelo-ubuntu kernel: [35542.161094] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:11:07 angelo-ubuntu kernel: [35552.514968] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:07 angelo-ubuntu kernel: [35552.522063] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:07 angelo-ubuntu kernel: [35552.721551] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:11:08 angelo-ubuntu kernel: [35552.920066] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:11:08 angelo-ubuntu kernel: [35553.121085] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:11:18 angelo-ubuntu kernel: [35563.585832] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:18 angelo-ubuntu kernel: [35563.593132] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:18 angelo-ubuntu kernel: [35563.792104] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:11:19 angelo-ubuntu kernel: [35563.997081] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:11:19 angelo-ubuntu kernel: [35564.197076] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:11:29 angelo-ubuntu kernel: [35574.550206] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:29 angelo-ubuntu kernel: [35574.558993] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:29 angelo-ubuntu kernel: [35574.757088] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:11:30 angelo-ubuntu kernel: [35574.956238] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:11:30 angelo-ubuntu kernel: [35575.157092] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:11:40 angelo-ubuntu kernel: [35585.568309] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:40 angelo-ubuntu kernel: [35585.575645] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:40 angelo-ubuntu kernel: [35585.776092] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:11:41 angelo-ubuntu kernel: [35585.972046] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:11:41 angelo-ubuntu kernel: [35586.176084] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:11:51 angelo-ubuntu kernel: [35596.502753] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:51 angelo-ubuntu kernel: [35596.510043] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:51 angelo-ubuntu kernel: [35596.709301] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:11:52 angelo-ubuntu kernel: [35596.912024] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:11:52 angelo-ubuntu kernel: [35597.108035] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:11:56 angelo-ubuntu kernel: [35600.874039] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:56 angelo-ubuntu kernel: [35601.072099] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:11:56 angelo-ubuntu kernel: [35601.272051] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:11:56 angelo-ubuntu kernel: [35601.472087] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out


**messages.log**
> 
Sep 29 21:42:36 angelo-ubuntu -- MARK --
Sep 29 22:02:36 angelo-ubuntu -- MARK --
Sep 29 22:22:36 angelo-ubuntu -- MARK --
Sep 29 22:42:36 angelo-ubuntu -- MARK --
Sep 29 23:02:36 angelo-ubuntu -- MARK --
Sep 29 23:22:36 angelo-ubuntu -- MARK --
Sep 29 23:42:36 angelo-ubuntu -- MARK --
Sep 30 00:02:36 angelo-ubuntu -- MARK --
Sep 30 00:12:37 angelo-ubuntu exiting on signal 15


**syslog**
> 
Sep 30 00:11:08 angelo-ubuntu kernel: [35553.121085] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:11:17 angelo-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Sep 30 00:11:17 angelo-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Sep 30 00:11:18 angelo-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Sep 30 00:11:18 angelo-ubuntu kernel: [35563.585832] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:18 angelo-ubuntu kernel: [35563.593132] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:18 angelo-ubuntu kernel: [35563.792104] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:11:19 angelo-ubuntu kernel: [35563.997081] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:11:19 angelo-ubuntu kernel: [35564.197076] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:11:22 angelo-ubuntu NetworkManager: <info>  wlan0: link timed out. 
Sep 30 00:11:28 angelo-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Sep 30 00:11:28 angelo-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Sep 30 00:11:29 angelo-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Sep 30 00:11:29 angelo-ubuntu kernel: [35574.550206] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:29 angelo-ubuntu kernel: [35574.558993] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:29 angelo-ubuntu kernel: [35574.757088] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:11:30 angelo-ubuntu kernel: [35574.956238] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:11:30 angelo-ubuntu kernel: [35575.157092] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:11:39 angelo-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Sep 30 00:11:39 angelo-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Sep 30 00:11:40 angelo-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Sep 30 00:11:40 angelo-ubuntu kernel: [35585.568309] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:40 angelo-ubuntu kernel: [35585.575645] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:40 angelo-ubuntu kernel: [35585.776092] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:11:41 angelo-ubuntu kernel: [35585.972046] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:11:41 angelo-ubuntu kernel: [35586.176084] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:11:44 angelo-ubuntu NetworkManager: <info>  wlan0: link timed out. 
Sep 30 00:11:50 angelo-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Sep 30 00:11:50 angelo-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Sep 30 00:11:51 angelo-ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Sep 30 00:11:51 angelo-ubuntu kernel: [35596.502753] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:51 angelo-ubuntu kernel: [35596.510043] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:51 angelo-ubuntu kernel: [35596.709301] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:11:52 angelo-ubuntu kernel: [35596.912024] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:11:52 angelo-ubuntu kernel: [35597.108035] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:11:56 angelo-ubuntu NetworkManager: <info>  Activation (wlan0/wireless): association took too long, failing activation. 
Sep 30 00:11:56 angelo-ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 9 
Sep 30 00:11:56 angelo-ubuntu NetworkManager: <info>  Activation (wlan0) failed for access point (default) 
Sep 30 00:11:56 angelo-ubuntu NetworkManager: <info>  Marking connection 'Auto default' invalid. 
Sep 30 00:11:56 angelo-ubuntu NetworkManager: <info>  Activation (wlan0) failed. 
Sep 30 00:11:56 angelo-ubuntu NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Sep 30 00:11:56 angelo-ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Sep 30 00:11:56 angelo-ubuntu kernel: [35600.874039] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 1
Sep 30 00:11:56 angelo-ubuntu kernel: [35601.072099] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 2
Sep 30 00:11:56 angelo-ubuntu kernel: [35601.272051] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e try 3
Sep 30 00:11:56 angelo-ubuntu kernel: [35601.472087] wlan0: direct probe to AP 00:1c:f0:ba:a1:5e timed out
Sep 30 00:12:17 angelo-ubuntu x-session-manager[5961]: WARNING: Client '/org/gnome/SessionManager/Client10' failed to reply before timeout 
Sep 30 00:12:30 angelo-ubuntu console-kit-daemon[5354]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Sep 30 00:12:30 angelo-ubuntu init: tty4 main process (4677) killed by TERM signal
Sep 30 00:12:30 angelo-ubuntu init: tty5 main process (4678) killed by TERM signal
Sep 30 00:12:30 angelo-ubuntu init: tty2 main process (4681) killed by TERM signal
Sep 30 00:12:30 angelo-ubuntu init: tty3 main process (4682) killed by TERM signal
Sep 30 00:12:30 angelo-ubuntu init: tty6 main process (4683) killed by TERM signal
Sep 30 00:12:30 angelo-ubuntu init: tty1 main process (5894) killed by TERM signal
Sep 30 00:12:33 angelo-ubuntu nm-system-settings:    SCPlugin-Ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/net_0a_00_27_00_00_00)
Sep 30 00:12:37 angelo-ubuntu bluetoothd[5533]: Unregistered interface org.bluez.NetworkPeer on path /org/bluez/5533/hci0
Sep 30 00:12:37 angelo-ubuntu bluetoothd[5533]: Unregistered interface org.bluez.NetworkHub on path /org/bluez/5533/hci0
Sep 30 00:12:37 angelo-ubuntu bluetoothd[5533]: Unregistered interface org.bluez.NetworkRouter on path /org/bluez/5533/hci0
Sep 30 00:12:37 angelo-ubuntu bluetoothd[5533]: bridge pan0 removed
Sep 30 00:12:37 angelo-ubuntu bluetoothd[5533]: Stopping SDP server
Sep 30 00:12:37 angelo-ubuntu bluetoothd[5533]: Exit
Sep 30 00:12:37 angelo-ubuntu exiting on signal 15


All sounds correct I'm not able to see errors.
Could someone help me?
Thanks, bye bye.

---

