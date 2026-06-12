---
title: "Could not acquire name on session bus"
date: 2009-09-06
forum: General Help
---

### Post by rpaco on 2009-09-06
Jaunty 9.04.Kernel 2.6.28-15 Dell D600 laptop
Having just fixed the new Intel2100/backports wireless problem and the new network problems brought with Jaunty, via the helpful threads in the network forum section, (modding the samba config file and adding winbinding) having re-booted today I now have a new problem which "seems" to happen only if I log in as "me" and not if I log in as "root".
Having logged in, as the screen is formed, the status bar shows lots of windows with cog wheels, maybe 20 - 30. These eventually disappear, then the main menu bars etc are formed. But I have multiple layers of an error box in centre screen saying "Could not acquire name on session bus". Then most of the menu apps and procs do not work. 
If I re-start and log in as root then everything is ok. 
I have tried booting into recover mode and "repairing broken packages" but then when it comes to the point of connection to the inet I get a 5 times repeated error "E:Method http has died unexpectedly" and the repair stops ans reverets to normal boot. Have also tried booting into last version, but no difference. I  suspect fixing the network has broken something else. I cannot acces the log file viewer or nautilus from my own login, only as root. Any ideas please.
Additional info: Have finally managed to get System Monitor running and there seem to be 30 plus sessions of x-session manager running.

---

### Post by rpaco on 2009-09-07
Ok if anyone wants to know the three actions scheduler procs had been disabled and the registry was not being consulted properly. 
This does not seem to have a connection to the other numerous Jaunty lockups issues, which I have a suspicion are network and/or fileserver/nutilus related.

---

### Post by rpaco on 2009-09-07
Sorry its all come back, still only happening when I log in as me, all ok when I log in as root.
Here is the first part of my .xsession-errors file from my home directory.
<<
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-h0KBjI/socket
SSH_AUTH_SOCK=/tmp/keyring-h0KBjI/socket.ssh

(gnome-settings-daemon:3552): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Cannot register the panel shell: there is already one running.
Cannot register the panel shell: there is already one running.
** (gnome-panel:3566): DEBUG: Adding applet 0.
** (gnome-panel:3566): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:3566): DEBUG: Adding applet 1.
** (gnome-panel:3566): DEBUG: Adding applet 2.
** (gnome-panel:3566): DEBUG: Adding applet 3.
cupsd: Child exited with status 1!
** (gnome-panel:3566): DEBUG: Adding applet 4.
Failure: Module initalization failed
x-session-manager[3582]: WARNING: Failed to acquire org.gnome.SessionManager
x-session-manager[3581]: WARNING: Failed to acquire org.gnome.SessionManager
x-session-manager[3580]: WARNING: Failed to acquire org.gnome.SessionManager
x-session-manager[3583]: WARNING: Failed to acquire org.gnome.SessionManager
** (gnome-panel:3566): DEBUG: Adding applet 5.

** (update-notifier:3592): WARNING **: already running?

** (gnome-panel:3566): DEBUG: Adding applet 6.
** (gnome-panel:3566): DEBUG: Adding applet 7.
** (gnome-panel:3566): DEBUG: Adding applet 8.
** (gnome-panel:3566): DEBUG: Adding applet 9.
** (gnome-panel:3566): DEBUG: Adding applet 10.
** (gnome-panel:3566): DEBUG: Adding applet 11.
** (nm-applet:3586): DEBUG: applet_common_device_state_changed
** (nm-applet:3586): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:3586): DEBUG: applet_common_device_state_changed
** (nm-applet:3586): DEBUG: old state indicates that this was not a disconnect 0

** (nm-applet:3586): WARNING **: <WARN>  constructor(): Invalid connection: 'NMSettingWireless' / 'band' invalid: 4


** (nm-applet:3586): WARNING **: <WARN>  constructor(): Invalid connection: 'NMSettingWireless' / 'band' invalid: 4


** (nm-applet:3586): WARNING **: <WARN>  constructor(): Invalid connection: 'NMSettingWireless' / 'ssid' invalid: 2


** (nm-applet:3586): WARNING **: <WARN>  constructor(): Invalid connection: 'NMSettingWireless' / 'band' invalid: 4


** (nm-applet:3586): WARNING **: <WARN>  constructor(): Invalid connection: 'NMSettingWireless' / 'band' invalid: 4

** (nm-applet:3586): DEBUG: applet_common_device_state_changed
** (nm-applet:3586): DEBUG: applet_common_device_state_changed
** (nm-applet:3586): DEBUG: applet_common_device_state_changed
** (nm-applet:3586): DEBUG: applet_common_device_state_changed
** (nm-applet:3586): DEBUG: applet_common_device_state_changed
** (nm-applet:3586): DEBUG: foo_client_state_changed_cb
** (gnome-panel:3566): DEBUG: Adding applet 12.
** (gnome-panel:3566): DEBUG: Adding applet 13.
** (gnome-panel:3566): DEBUG: Adding applet 14.
** (gnome-panel:3566): DEBUG: Adding applet 15.
Unable to open desktop file /home/xxxx/Desktop/ooo-base.desktop for panel launcher: No such file or directory
** (nm-applet:3586): DEBUG: applet_common_device_state_changed
** (nm-applet:3586): DEBUG: applet_common_device_state_changed
** (nm-applet:3586): DEBUG: foo_client_state_changed_cb
** Message: Initializing gksu extension...
>>
There is a lot more

---

### Post by rpaco on 2009-09-08
Bump

---

### Post by funkyworklehead on 2011-01-28
I had a similar problem and the solutions in this thread helped me:

[http://www.uluga.ubuntuforums.org/showthread.php?t=1480094](http://www.uluga.ubuntuforums.org/showthread.php?t=1480094)

---

