---
title: "transmission-deamon issue after reboot"
date: 2011-06-22
forum: General Help
---

### Post by pakjebakmeel on 2011-06-22
Hi all,

Got a little annoyance on my hands here, I've installed transmission-daemon on my headless Ubuntu 11.04 server and use the web interface to manage it. This is all working fine. However, after a reboot it seems that transmission daemon starts but the webinterface is unavailable. I get this in the syslog after a reboot:

```

Jun 22 10:54:27 localhost transmission-daemon[703]: Transmission 2.31 (12441) started (session.c:706)
Jun 22 10:54:27 localhost transmission-daemon[703]: RPC Server Adding address to whitelist: 192.168.*.* (rpc-server.c:805)
Jun 22 10:54:27 localhost transmission-daemon[703]: RPC Server Serving RPC and Web requests on port 127.0.0.1:9091/transmission/ (rpc-server.c:982)
Jun 22 10:54:27 localhost transmission-daemon[703]: RPC Server Whitelist enabled (rpc-server.c:986)
Jun 22 10:54:27 localhost transmission-daemon[703]: RPC Server Password required (rpc-server.c:989)
Jun 22 10:54:27 localhost transmission-daemon[703]: Port Forwarding Stopped (port-forwarding.c:181)
Jun 22 10:54:27 localhost transmission-daemon[703]: UDP Failed to set receive buffer: requested 4194304, got 262142 (tr-udp.c:75)
Jun 22 10:54:27 localhost transmission-daemon[703]: UDP Please add the line "net.core.rmem_max = 4194304" to /etc/sysctl.conf (tr-udp.c:80)
Jun 22 10:54:27 localhost transmission-daemon[703]: UDP Failed to set send buffer: requested 1048576, got 262142 (tr-udp.c:86)
Jun 22 10:54:27 localhost transmission-daemon[703]: UDP Please add the line "net.core.wmem_max = 1048576" to /etc/sysctl.conf (tr-udp.c:91)
Jun 22 10:54:27 localhost transmission-daemon[703]: DHT Reusing old id (tr-dht.c:305)
Jun 22 10:54:27 localhost transmission-daemon[703]: DHT Bootstrapping from 71 nodes (tr-dht.c:153)
Jun 22 10:54:27 localhost transmission-daemon[703]: Using settings from "/home/debian-transmission/.config/transmission" (daemon.c:489)
Jun 22 10:54:27 localhost transmission-daemon[703]: Saved "/home/debian-transmission/.config/transmission/settings.json" (bencode.c:1722)
Jun 22 10:54:27 localhost transmission-daemon[703]: transmission-daemon requiring authentication (daemon.c:509)

```When I restart the daemon the web interface becomes available again. I use this command:

```

sudo /etc/init.d/transmission-daemon restart

```After restarting the daemon I get this in the syslog:

```


Jun 22 11:00:44 localhost transmission-daemon[1152]: Transmission 2.31 (12441) started (session.c:706)
Jun 22 11:00:44 localhost transmission-daemon[1152]: RPC Server Adding address to whitelist: 192.168.*.* (rpc-server.c:805)
Jun 22 11:00:44 localhost transmission-daemon[1152]: RPC Server Serving RPC and Web requests on port 127.0.0.1:9091/transmission/ (rpc-server.c:982)
Jun 22 11:00:44 localhost transmission-daemon[1152]: RPC Server Whitelist enabled (rpc-server.c:986)
Jun 22 11:00:44 localhost transmission-daemon[1152]: RPC Server Password required (rpc-server.c:989)
Jun 22 11:00:44 localhost transmission-daemon[1152]: Port Forwarding Stopped (port-forwarding.c:181)
Jun 22 11:00:44 localhost transmission-daemon[1152]: UDP Failed to set receive buffer: requested 4194304, got 262142 (tr-udp.c:75)
Jun 22 11:00:44 localhost transmission-daemon[1152]: UDP Please add the line "net.core.rmem_max = 4194304" to /etc/sysctl.conf (tr-udp.c:80)
Jun 22 11:00:44 localhost transmission-daemon[1152]: UDP Failed to set send buffer: requested 1048576, got 262142 (tr-udp.c:86)
Jun 22 11:00:44 localhost transmission-daemon[1152]: UDP Please add the line "net.core.wmem_max = 1048576" to /etc/sysctl.conf (tr-udp.c:91)
Jun 22 11:00:44 localhost transmission-daemon[1152]: DHT Reusing old id (tr-dht.c:305)
Jun 22 11:00:44 localhost transmission-daemon[1152]: DHT Bootstrapping from 71 nodes (tr-dht.c:153)
Jun 22 11:00:44 localhost transmission-daemon[1152]: Using settings from "/home/debian-transmission/.config/transmission" (daemon.c:489)
Jun 22 11:00:44 localhost transmission-daemon[1152]: Saved "/home/debian-transmission/.config/transmission/settings.json" (bencode.c:1722)
Jun 22 11:00:44 localhost transmission-daemon[1152]: transmission-daemon requiring authentication (daemon.c:509)
Jun 22 11:01:00 localhost transmission-daemon[1152]: Searching for web interface file "/home/debian-transmission/.local/share/transmission/web/index.html" (platform.c:540)
Jun 22 11:01:00 localhost transmission-daemon[1152]: Searching for web interface file "/usr/share/transmission/web/index.html" (platform.c:540)

```Note the last 2 lines, they are not written to the syslog upon system boot. It seems the daemon starts fine but somehow it does not load the web files, hence the web interface is unavailable.

The lines I suspect that have something to do with my problem as they DO NOT appear on a system reboot but only when rebooting the deamon:
```

Jun 22 11:01:00 localhost transmission-daemon[1152]: Searching for web interface file "/home/debian-transmission/.local/share/transmission/web/index.html" (platform.c:540)
Jun 22 11:01:00 localhost transmission-daemon[1152]: Searching for web interface file "/usr/share/transmission/web/index.html" (platform.c:540)

```Config files:

/etc/default/transmission-daemon
```

# defaults for transmission-daemon
# sourced by /etc/init.d/transmission-daemon

# Change to 0 to disable daemon
ENABLE_DAEMON=1

# This directory stores some runtime information, like torrent files
# and links to the config file, which itself can be found in
# /etc/transmission-daemon/settings.json
CONFIG_DIR="/home/debian-transmission/.config/transmission"

# Default options for daemon, see transmission-daemon(1) for more options
OPTIONS="--config-dir $CONFIG_DIR"

```/home/debian-transmission/.config/transmission/settings.json
```

{
    "alt-speed-down": 2000,
    "alt-speed-enabled": true,
    "alt-speed-time-begin": 540,
    "alt-speed-time-day": 127,
    "alt-speed-time-enabled": true,
    "alt-speed-time-end": 1320,
    "alt-speed-up": 100,
    "bind-address-ipv4": "0.0.0.0",
    "bind-address-ipv6": "::",
    "blocklist-enabled": false,
    "blocklist-url": "http://www.example.com/blocklist",
    "cache-size-mb": 4,
    "dht-enabled": true,
    "download-dir": "/mnt/sdb1/Downloads/transmission",
    "download-limit": 100,
    "download-limit-enabled": 0,
    "encryption": 2,
    "idle-seeding-limit": 30,
    "idle-seeding-limit-enabled": false,
    "incomplete-dir": "/mnt/sdb1/Downloads/transmission/.incomplete",
    "incomplete-dir-enabled": true,
    "lazy-bitfield-enabled": true,
    "lpd-enabled": false,
    "max-peers-global": 200,
    "message-level": 2,
    "open-file-limit": 32,
    "peer-congestion-algorithm": "",
    "peer-limit-global": 500,
    "peer-limit-per-torrent": 75,
    "peer-port": 49263,
    "peer-port-random-high": 49300,
    "peer-port-random-low": 49160,
    "peer-port-random-on-start": true,
    "peer-socket-tos": "default",
    "pex-enabled": true,
    "port-forwarding-enabled": false,
    "preallocation": 1,
    "prefetch-enabled": 1,
    "ratio-limit": 2,
    "ratio-limit-enabled": false,
    "rename-partial-files": true,
    "rpc-authentication-required": true,
    "rpc-bind-address": "192.168.3.10",
    "rpc-enabled": true,
    "rpc-password": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
    "rpc-port": 9091,
    "rpc-url": "/transmission/",
    "rpc-username": "pakjebakmeel",
    "rpc-whitelist": "192.168.*.*",
    "rpc-whitelist-enabled": true,
    "script-torrent-done-enabled": false,
    "script-torrent-done-filename": "",
    "speed-limit-down": 0,
    "speed-limit-down-enabled": false,
    "speed-limit-up": 400,
    "speed-limit-up-enabled": true,
    "start-added-torrents": true,
    "trash-original-torrent-files": true,
    "umask": 2,
    "upload-limit": 100,
    "upload-limit-enabled": 0,
    "upload-slots-per-torrent": 14,
    "utp-enabled": true
}

```Any idea? Anyone seen this before? Kinda stuck here. Bit of expert advise where to look?

Thanks,

---

### Post by pakjebakmeel on 2011-06-27
Anyone? any clues?

---

### Post by pakjebakmeel on 2011-08-07
This has been solved now.. I ran:

sudo update-rc.d transmission-daemon -f remove

To remove all startup entries for transmission-daemon; next I ran:

sudo update-rc.d transmission-daemon defaults 80

To re-add startup entries but now a bit further down the booting process, it was on position 20 before. This seems to have solved my issue.

Thought I would just post my fix for anyone having this issue. :KS

---

