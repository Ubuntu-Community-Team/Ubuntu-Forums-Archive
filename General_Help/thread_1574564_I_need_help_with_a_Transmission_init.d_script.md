---
title: "I need help with a Transmission init.d script"
date: 2010-09-14
forum: General Help
---

### Post by thebrandon on 2010-09-14
For some reason when my server starts up the Transmission daemon starts fine but I cant access the webui, I just get the error message :

403: Forbidden

Unauthorized IP Address.

Either disable the IP address whitelist or add your address to it.

If you're editing settings.json, see the 'rpc-whitelist' and 'rpc-whitelist-enabled' entries.

If you're still using ACLs, use a whitelist instead. See the transmission-daemon manpage for details.

So I have been trying to change the settings in the settings.json file but no matter what I change I get the exact same results.  The only thing that does work is for me to use the command transmission-daemon -a *.*.*.* and all is good.  I dont know if Transmission is looking at a different settings file than the one I have been editing or what.  So basically I figured maybe I could use a script or adjust the one thats already in the init.d folder to add that -a *.*.*.* at the end when it starts the daemon.  How would I go about this?

Also, if anyone is curious, path to the settings.json file I am editing is : ~/.config/transmission/settings.json

Oh and here is my settings.json file, maybe I just have something wrong:
```
{
    "alt-speed-down": 50, 
    "alt-speed-enabled": false, 
    "alt-speed-time-begin": 540, 
    "alt-speed-time-day": 127, 
    "alt-speed-time-enabled": false, 
    "alt-speed-time-end": 1020, 
    "alt-speed-up": 50, 
    "bind-address-ipv4": "0.0.0.0", 
    "bind-address-ipv6": "::", 
    "blocklist-date": 1284303977, 
    "blocklist-enabled": false, 
    "blocklist-updates-enabled": true, 
    "dht-enabled": true, 
    "download-dir": "/home/brandon/Downloads", 
    "encryption": 1, 
    "filter-mode": "show-all", 
    "incomplete-dir": "/home/brandon/Downloads", 
    "incomplete-dir-enabled": false, 
    "inhibit-desktop-hibernation": false, 
    "lazy-bitfield-enabled": true, 
    "main-window-height": 500, 
    "main-window-is-maximized": 0, 
    "main-window-layout-order": "menu,toolbar,filter,list,statusbar", 
    "main-window-width": 467, 
    "main-window-x": 50, 
    "main-window-y": 50, 
    "message-level": 2, 
    "minimal-view": false, 
    "open-dialog-dir": "/home/brandon", 
    "open-file-limit": 32, 
    "peer-limit-global": 240, 
    "peer-limit-per-torrent": 60, 
    "peer-port": 51413, 
    "peer-port-random-high": 65535, 
    "peer-port-random-low": 49152, 
    "peer-port-random-on-start": false, 
    "peer-socket-tos": 0, 
    "pex-enabled": true, 
    "play-download-complete-sound": true, 
    "port-forwarding-enabled": true, 
    "preallocation": 1, 
    "prompt-before-exit": true, 
    "proxy": "", 
    "proxy-auth-enabled": false, 
    "proxy-auth-password": "", 
    "proxy-auth-username": "", 
    "proxy-enabled": false, 
    "proxy-port": 80, 
    "proxy-type": 0, 
    "ratio-limit": 2.0000, 
    "ratio-limit-enabled": false, 
    "rename-partial-files": true, 
    "rpc-authentication-required": false, 
    "rpc-bind-address": "0.0.0.0", 
    "rpc-enabled": true, 
    "rpc-password": "{7a2106cf3cea9d3f0f441f43d0732f80ca117948zOlM4FoI", 
    "rpc-port": 9091, 
    "rpc-username": "brandon", 
    "rpc-whitelist": "192.168.2.4", 
    "rpc-whitelist-enabled": false, 
    "show-backup-trackers": false, 
    "show-desktop-notification": true, 
    "show-extra-peer-details": false, 
    "show-filterbar": true, 
    "show-notification-area-icon": false, 
    "show-options-window": true, 
    "show-statusbar": true, 
    "show-toolbar": true, 
    "show-tracker-scrapes": false, 
    "sort-mode": "sort-by-name", 
    "sort-reversed": false, 
    "speed-limit-down": 100, 
    "speed-limit-down-enabled": false, 
    "speed-limit-up": 100, 
    "speed-limit-up-enabled": false, 
    "start-added-torrents": true, 
    "statusbar-stats": "total-ratio", 
    "trash-original-torrent-files": false, 
    "umask": 18, 
    "upload-slots-per-torrent": 14, 
    "user-has-given-informed-consent": true, 
    "watch-dir": "/home/brandon/Downloads", 
    "watch-dir-enabled": false
}
```

---

### Post by thebrandon on 2010-09-14
Well I just realized on huge mistake I have been making and that was that I was editing the wrong settings.json file.  I should have been editing the one in ~/.config/transmission-daemon/settings.json but when I went back and made changes to it I still get the same results, here is the correct settings file :

```
{
    "alt-speed-down": 50, 
    "alt-speed-enabled": false, 
    "alt-speed-time-begin": 540, 
    "alt-speed-time-day": 127, 
    "alt-speed-time-enabled": false, 
    "alt-speed-time-end": 1020, 
    "alt-speed-up": 50, 
    "bind-address-ipv4": "0.0.0.0", 
    "bind-address-ipv6": "::", 
    "blocklist-enabled": false, 
    "dht-enabled": true, 
    "download-dir": "/home/brandon/Downloads", 
    "encryption": 1, 
    "incomplete-dir": "/home/brandon/Downloads", 
    "incomplete-dir-enabled": false, 
    "lazy-bitfield-enabled": true, 
    "message-level": 2, 
    "open-file-limit": 32, 
    "peer-limit-global": 240, 
    "peer-limit-per-torrent": 60, 
    "peer-port": 51413, 
    "peer-port-random-high": 65535, 
    "peer-port-random-low": 49152, 
    "peer-port-random-on-start": false, 
    "peer-socket-tos": 0, 
    "pex-enabled": true, 
    "port-forwarding-enabled": true, 
    "preallocation": 1, 
    "proxy": "", 
    "proxy-auth-enabled": false, 
    "proxy-auth-password": "", 
    "proxy-auth-username": "", 
    "proxy-enabled": false, 
    "proxy-port": 80, 
    "proxy-type": 0, 
    "ratio-limit": 2.0000, 
    "ratio-limit-enabled": false, 
    "rename-partial-files": true, 
    "rpc-authentication-required": false, 
    "rpc-bind-address": "0.0.0.0", 
    "rpc-enabled": true, 
    "rpc-password": "{d6e9c24411cb941e21beeb7e7f8d98a1c2dc33a5N1YgXXMh", 
    "rpc-port": 9091, 
    "rpc-username": "", 
    "rpc-whitelist": "*.*.*.*", 
    "rpc-whitelist-enabled": false, 
    "speed-limit-down": 100, 
    "speed-limit-down-enabled": false, 
    "speed-limit-up": 100, 
    "speed-limit-up-enabled": false, 
    "umask": 18, 
    "upload-slots-per-torrent": 14
}
```

---

### Post by thebrandon on 2010-09-15
Well if there is anyone who stumbles upon this and is having the same problem the nice folks over at the transmission forum put me straight.  The settings file I was changing wasnt the right one, the correct file to change is /etc/transmission-daemon/settings/json .

My posts over at the transmission forum can be found here :

[https://forum.transmissionbt.com/viewtopic.php?f=8&t=10539&start=0](https://forum.transmissionbt.com/viewtopic.php?f=8&t=10539&start=0)

---

