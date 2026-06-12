---
title: "&quot;Permission denied&quot; when adding torrents with transmission-daemon"
date: 2012-07-13
forum: General Help
---

### Post by katakaio on 2012-07-13
Hey all,

I've been running transmission-daemon on a headless Precise server for some time now with now complaints. However, it recently started throwing a "Permission denied" whenever I added a new torrent. It seems that it's complaining about the download location, even though that hasn't changed. The folder is in the *debian-transmission* group, but I've even tried a temporary chmod 777 with no luck. I have confirmed that it can successfully download to the default location (/var/lib/transmission-daemon/downloads), but I need the current download location in my home directory to work. Any thoughts? I've included the settings.json file just in case.

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
    "cache-size-mb": 4,
    "dht-enabled": false,
    "download-dir": "/home/katakaio/Torrents",
    "download-limit": 100,
    "download-limit-enabled": 0,
    "download-queue-enabled": true,
    "download-queue-size": 5,
    "encryption": 2,
    "idle-seeding-limit": 30,
    "idle-seeding-limit-enabled": false,
    "incomplete-dir": "/var/lib/transmission-daemon/downloads",
    "incomplete-dir-enabled": false,
    "lpd-enabled": false,
    "max-peers-global": 200,
    "message-level": 2,
    "peer-congestion-algorithm": "",
    "peer-limit-global": 240,
    "peer-limit-per-torrent": 60,
    "peer-port": 49787,
    "peer-port-random-high": 65535,
    "peer-port-random-low": 49152,
    "peer-port-random-on-start": true,
    "peer-socket-tos": "default",
    "pex-enabled": false,
    "port-forwarding-enabled": true,
    "preallocation": 1,
    "prefetch-enabled": 1,
    "queue-stalled-enabled": true,
    "queue-stalled-minutes": 30,
    "ratio-limit": 1.5000,
    "ratio-limit-enabled": true,
    "rename-partial-files": true,
    "rpc-authentication-required": true,
    "rpc-bind-address": "0.0.0.0",
    "rpc-enabled": true,
    "rpc-password": "password",
    "rpc-port": 9091,
    "rpc-url": "/transmission/",
    "rpc-username": "katakaio",
    "rpc-whitelist": "127.0.0.1",
    "rpc-whitelist-enabled": false,
    "scrape-paused-torrents-enabled": true,
    "script-torrent-done-enabled": false,
    "script-torrent-done-filename": "",
    "seed-queue-enabled": false,
    "seed-queue-size": 10,
    "speed-limit-down": 100,
    "speed-limit-down-enabled": false,
    "speed-limit-up": 100,
    "speed-limit-up-enabled": false,
    "start-added-torrents": true,
    "trash-original-torrent-files": false,
    "umask": 2,
    "upload-limit": 100,
    "upload-limit-enabled": 0,
    "upload-slots-per-torrent": 14,
    "utp-enabled": true
}
```

Thanks!

---

### Post by d4m1r on 2012-07-13
Try creating a new user and assign them ownership of the folder or even run it as root once to verify if it really is a permission issue or something else.

---

### Post by katakaio on 2012-07-16
Problem solved - thank you d4m1r for pointing me in the right direction! Even though my user account was already a part of the group *debian-transmission*, adding my account to the group again seems to have solved the permissions problem. It seems like this association may be broken after a new install of transmission-daemon, even though the account is listed as belonging to that group.

Thanks again!

---

