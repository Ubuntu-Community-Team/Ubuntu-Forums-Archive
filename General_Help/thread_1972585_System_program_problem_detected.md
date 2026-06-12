---
title: "System program problem detected"
date: 2012-05-03
forum: General Help
---

### Post by jg1 on 2012-05-03
After a Herculean struggle finally got a satisfactory "clean"-ish dual boot Windows7/Ubuntu 12.04 on my new Dell XPS17.  I'm not a fan of "Unity" which is non-intuitive and awkward in use - and bouncy icons are a pain - but that's not the story.
After booting up I've started to get little message panels flashing up on the screen with no clues as to why:

 ?      System program problem detected
        Do you want to report the problem now?
           Cancel / Report Problem

It doesn't seem to matter whether I do anything on the machine or just let it sit idle, the msgs will still appear.  

Reaching into the Sys log I find the messages leading up to the on-screen msg are as follows:

…............
May  3 22:30:18 jg-XPS17 dbus[853]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
May  3 22:30:18 jg-XPS17 dbus[853]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
May  3 22:30:18 jg-XPS17 rtkit-daemon[1543]: Successfully called chroot.
May  3 22:30:18 jg-XPS17 rtkit-daemon[1543]: Successfully dropped privileges.
May  3 22:30:18 jg-XPS17 rtkit-daemon[1543]: Successfully limited resources.
May  3 22:30:18 jg-XPS17 rtkit-daemon[1543]: Running.
May  3 22:30:18 jg-XPS17 rtkit-daemon[1543]: Watchdog thread running.
May  3 22:30:18 jg-XPS17 rtkit-daemon[1543]: Canary thread running.
May  3 22:30:18 jg-XPS17 rtkit-daemon[1543]: Successfully made thread 1541 of process 1541 (n/a) owned by '104' high priority at nice level -11.
May  3 22:30:18 jg-XPS17 rtkit-daemon[1543]: Supervising 1 threads of 1 processes of 1 users.
May  3 22:30:18 jg-XPS17 NetworkManager[869]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
May  3 22:30:18 jg-XPS17 rtkit-daemon[1543]: Successfully made thread 1547 of process 1541 (n/a) owned by '104' RT at priority 5.
May  3 22:30:18 jg-XPS17 rtkit-daemon[1543]: Supervising 2 threads of 1 processes of 1 users.
May  3 22:30:18 jg-XPS17 rtkit-daemon[1543]: Successfully made thread 1548 of process 1541 (n/a) owned by '104' RT at priority 5.
May  3 22:30:18 jg-XPS17 rtkit-daemon[1543]: Supervising 3 threads of 1 processes of 1 users.
May  3 22:30:19 jg-XPS17 NetworkManager[869]: <info> Policy set 'Vnet' (wlan0) as default for IPv4 routing and DNS.
May  3 22:30:19 jg-XPS17 NetworkManager[869]: <info> Activation (wlan0) successful, device activated.
May  3 22:30:19 jg-XPS17 NetworkManager[869]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
May  3 22:30:19 jg-XPS17 dbus[853]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May  3 22:30:19 jg-XPS17 dbus[853]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May  3 22:30:19 jg-XPS17 rtkit-daemon[1543]: Successfully made thread 1570 of process 1570 (n/a) owned by '104' high priority at nice level -11.
May  3 22:30:19 jg-XPS17 rtkit-daemon[1543]: Supervising 4 threads of 2 processes of 1 users.
May  3 22:30:19 jg-XPS17 pulseaudio[1570]: [pulseaudio] pid.c: Daemon already running.
May  3 22:30:19 jg-XPS17 avahi-daemon[956]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::76e5:bff:fee3:ad50.
May  3 22:30:19 jg-XPS17 avahi-daemon[956]: New relevant interface wlan0.IPv6 for mDNS.
May  3 22:30:19 jg-XPS17 avahi-daemon[956]: Registering new address record for fe80::76e5:bff:fee3:ad50 on wlan0.*.
May  3 22:30:24 jg-XPS17 gnome-session[1637]: WARNING: Session 'ubuntu' runnable check failed: Exited with code 5
May  3 22:30:25 jg-XPS17 rtkit-daemon[1543]: Successfully made thread 1719 of process 1719 (n/a) owned by '1000' high priority at nice level -11.
May  3 22:30:25 jg-XPS17 rtkit-daemon[1543]: Supervising 4 threads of 2 processes of 2 users.
May  3 22:30:25 jg-XPS17 rtkit-daemon[1543]: Successfully made thread 1724 of process 1719 (n/a) owned by '1000' RT at priority 5.
May  3 22:30:25 jg-XPS17 rtkit-daemon[1543]: Supervising 5 threads of 2 processes of 2 users.
May  3 22:30:25 jg-XPS17 rtkit-daemon[1543]: Successfully made thread 1727 of process 1719 (n/a) owned by '1000' RT at priority 5.
May  3 22:30:25 jg-XPS17 rtkit-daemon[1543]: Supervising 6 threads of 2 processes of 2 users.
May  3 22:30:25 jg-XPS17 dbus[853]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
May  3 22:30:25 jg-XPS17 dbus[853]: [system] Successfully activated service 'org.freedesktop.UDisks'
May  3 22:30:25 jg-XPS17 nautilus: [N-A] Nautilus-Actions Tracker 3.1.4 initializing...
May  3 22:30:27 jg-XPS17 nautilus: [N-A] Nautilus-Actions Menu Extender 3.1.4 initializing...
May  3 22:30:27 jg-XPS17 ntpdate[1581]: adjust time server 91.189.94.4 offset 0.205946 sec
May  3 22:30:27 jg-XPS17 hp-systray: hp-systray[1733]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
May  3 22:30:28 jg-XPS17 kernel: [   32.777149] wlan0: no IPv6 routers present
May  3 22:30:37 jg-XPS17 NetworkManager[869]: <info> (wlan0): IP6 addrconf timed out or failed.
May  3 22:30:37 jg-XPS17 NetworkManager[869]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May  3 22:30:37 jg-XPS17 NetworkManager[869]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May  3 22:30:37 jg-XPS17 NetworkManager[869]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May  3 22:30:41 jg-XPS17 goa[1967]: goa-daemon version 3.4.0 starting [main.c:112, main()]

System then “stops” and after a few seconds a message flashes on the screen as follows:

?      System program problem detected
       Do you want to report the problem now?
       Cancel  /   Report Problem

After a few more seconds, processing continues as follows:

May  3 22:31:28 jg-XPS17 dbus[853]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
May  3 22:31:29 jg-XPS17 AptDaemon: INFO: Initializing daemon
May  3 22:31:29 jg-XPS17 AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
May  3 22:31:29 jg-XPS17 dbus[853]: [system] Successfully activated service 'org.freedesktop.PackageKit'
May  3 22:31:29 jg-XPS17 AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
May  3 22:31:30 jg-XPS17 AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/7ea91b8224224548900597873d2ed41e
May  3 22:31:30 jg-XPS17 AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/7ea91b8224224548900597873d2ed41e
May  3 22:31:31 jg-XPS17 AptDaemon.PackageKit: INFO: Get updates()
May  3 22:31:32 jg-XPS17 AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/7ea91b8224224548900597873d2ed41e
May  3 22:37:29 jg-XPS17 AptDaemon: INFO: Quitting due to inactivity
May  3 22:37:29 jg-XPS17 AptDaemon: INFO: Quitting was requested
…...............

What does the message mean?  Is it important?  How can I fix it?

The only thing that suggests a failure is a message about 16 secs prior to the on screen msg that says:
WARNING: Session 'ubuntu' runnable check failed: Exited with code 5
Any ideas what this might be?

I note that there are a lot more questions on this forum than answers but I've got my fingers crossed that someone will be kind enough to help
jg1

---

### Post by jg1 on 2012-05-03
Poking about a bit more, I'm now having problems with wireless comms and some Apps are taking forever to load.  I also tried to see what the problem report looked like.  Unfortunately I cant manage to print it or copy & paste so I've attached a few screen grabs
jg1

---

### Post by jg1 on 2012-05-03
Last five...

---

