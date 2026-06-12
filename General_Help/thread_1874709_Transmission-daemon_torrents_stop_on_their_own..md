---
title: "Transmission-daemon torrents stop on their own."
date: 2011-11-03
forum: General Help
---

### Post by false_chicken on 2011-11-03
I have just installed the transmission-daemon on my Ubuntu 11.04 server and I thought it was working fine but I noticed that when I use the gtk remote to add a torrent the file will start to download only to stop a few minutes later. Any ideas why this is? Here is my config file:



{
"alt-speed-down": 500,
"alt-speed-enabled": false,
"alt-speed-time-begin": 480,
"alt-speed-time-day": 127,
"alt-speed-time-enabled": true,
"alt-speed-time-end": 0,
"alt-speed-up": 10,
"bind-address-ipv4": "192.168.2.150",
"bind-address-ipv6": "::",
"blocklist-enabled": false,
"dht-enabled": true,
"download-dir": "/media/storage/torrents/complete",
"download-limit": 100,
"download-limit-enabled": 0,
"encryption": 2,
"incomplete-dir": "/media/storage/torrents/incoming",
"incomplete-dir-enabled": true,
"lazy-bitfield-enabled": true,
"max-peers-global": 200,
"message-level": 2,
"open-file-limit": 32,
"peer-limit-global": 400,
"peer-limit-per-torrent":100 ,
"peer-port": 20500,
"peer-port-random-high": 20599,
"peer-port-random-low": 20500,
"peer-port-random-on-start": true,
"peer-socket-tos": 0,
"pex-enabled": true,
"port-forwarding-enabled": false,
"preallocation": 1,
"proxy": "",
"proxy-auth-enabled": false,
"proxy-auth-password": "",
"proxy-auth-username": "",
"proxy-enabled": false,
"proxy-port": 80,
"proxy-type": 0,
"ratio-limit": 0.2500,
"ratio-limit-enabled": true,
"rename-partial-files": true,
"rpc-authentication-required": true,
"rpc-bind-address": "0.0.0.0",
"rpc-enabled": true,
"rpc-password": "password",
"rpc-port": 9091,
"rpc-username": "transmission",
"rpc-whitelist": "127.0.0.1,*.*.*.*,192.168.2.2",
"rpc-whitelist-enabled": false,
"speed-limit-down": 1500,
"speed-limit-down-enabled": true,
"speed-limit-up": 50,
"speed-limit-up-enabled": true,
"umask": 2,
"upload-limit": 100,
"upload-limit-enabled": 0,
"upload-slots-per-torrent": 4,
"watch-dir": "/home/mjdescy/dl/watch",
"watch-dir-enabled": false
}

---

