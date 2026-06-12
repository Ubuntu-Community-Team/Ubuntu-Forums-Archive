---
title: "Kicked out - loggout"
date: 2011-06-15
forum: General Help
---

### Post by Retor on 2011-06-15
Hi

I was just logged out out of my own system for no apparent reason. 

I'm using Ubuntu 11.04 on a Toshiba Satellite R830-13D.

Any ideas as to why? 

Here are logs from the time:

auth.log
```
Jun 15 23:09:40 Toshen polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.32, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale nb_NO.UTF-8) (disconnected from bus)
Jun 15 23:09:40 Toshen gdm-session-worker[1254]: pam_unix(gdm:session): session closed for user name
Jun 15 23:09:41 Toshen gnome-keyring-daemon[1359]: dbus failure unregistering from session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

Syslog
```
un 15 23:09:40 Toshen NetworkManager[749]: <info> (wlan0): device state change: 8 -> 3 (reason 38)
Jun 15 23:09:40 Toshen NetworkManager[749]: <info> (wlan0): deactivating device (reason: 38).
Jun 15 23:09:40 Toshen acpid: client 1076[0:0] has disconnected
Jun 15 23:09:40 Toshen acpid: client connected from 9582[0:0]
Jun 15 23:09:40 Toshen acpid: 1 client rule loaded
Jun 15 23:09:41 Toshen NetworkManager[749]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1571
Jun 15 23:09:41 Toshen kernel: [14467.004121] wlan0: deauthenticating from 00:19:e3:fa:6e:d1 by local choice (reason=3)
Jun 15 23:09:41 Toshen kernel: [14467.131107] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun 15 23:09:41 Toshen kernel: [14467.131111] cfg80211: Restoring regulatory settings
Jun 15 23:09:41 Toshen kernel: [14467.131128] cfg80211: Calling CRDA to update world regulatory domain
Jun 15 23:09:41 Toshen kernel: [14467.135415] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Jun 15 23:09:41 Toshen kernel: [14467.135419] cfg80211: World regulatory domain updated:
Jun 15 23:09:41 Toshen kernel: [14467.135420] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 15 23:09:41 Toshen kernel: [14467.135422] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 15 23:09:41 Toshen kernel: [14467.135424] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 15 23:09:41 Toshen kernel: [14467.135426] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 15 23:09:41 Toshen kernel: [14467.135427] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 15 23:09:41 Toshen kernel: [14467.135429] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 15 23:09:41 Toshen wpa_supplicant[769]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun 15 23:09:42 Toshen rtkit-daemon[1262]: Successfully made thread 9660 of process 9660 (n/a) owned by '106' high priority at nice level -11.
Jun 15 23:09:42 Toshen rtkit-daemon[1262]: Supervising 1 threads of 1 processes of 1 users.
Jun 15 23:09:42 Toshen rtkit-daemon[1262]: Successfully made thread 9663 of process 9660 (n/a) owned by '106' RT at priority 5.
Jun 15 23:09:42 Toshen rtkit-daemon[1262]: Supervising 2 threads of 1 processes of 1 users.
Jun 15 23:09:42 Toshen rtkit-daemon[1262]: Successfully made thread 9664 of process 9660 (n/a) owned by '106' RT at priority 5.
Jun 15 23:09:42 Toshen rtkit-daemon[1262]: Supervising 3 threads of 1 processes of 1 users.
Jun 15 23:09:42 Toshen gdm-simple-greeter[9651]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
```

kern.log
```
Jun 15 23:09:41 Toshen kernel: [14467.004121] wlan0: deauthenticating from 00:19:e3:fa:6e:d1 by local choice (reason=3)
Jun 15 23:09:41 Toshen kernel: [14467.131107] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun 15 23:09:41 Toshen kernel: [14467.131111] cfg80211: Restoring regulatory settings
Jun 15 23:09:41 Toshen kernel: [14467.131128] cfg80211: Calling CRDA to update world regulatory domain
Jun 15 23:09:41 Toshen kernel: [14467.135415] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Jun 15 23:09:41 Toshen kernel: [14467.135419] cfg80211: World regulatory domain updated:
Jun 15 23:09:41 Toshen kernel: [14467.135420] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 15 23:09:41 Toshen kernel: [14467.135422] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 15 23:09:41 Toshen kernel: [14467.135424] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 15 23:09:41 Toshen kernel: [14467.135426] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 15 23:09:41 Toshen kernel: [14467.135427] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 15 23:09:41 Toshen kernel: [14467.135429] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
```

---

### Post by Rifester on 2011-06-15
Probably a result of the random logout bug...   Many bugs have been filed on Launchpad.  

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/778490](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/778490)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/774978](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/774978)

While I was entering the links it was updated stating the fix has been released...

---

### Post by Retor on 2011-06-16
Ah, goody - Thanks! :D

---

### Post by Rifester on 2011-06-16
You are welcome!   The fix came with updates last night.  So far it seems to have fixed the problem!

---

