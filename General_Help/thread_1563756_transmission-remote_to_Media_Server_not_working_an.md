---
title: "transmission-remote to Media Server not working anymore"
date: 2010-08-29
forum: General Help
---

### Post by wannabegeek on 2010-08-29
hi all...

This thread belongs in 'Networking' probably but that category seems to get less traffic.
Perhaps the mod will move it there after some discussion is generated...

Got this from transmission-remote x.x.x.x -l
```

daniel@Geek:~$ transmission-remote 10.0.0.10 -l
Unexpected response: <h1>403: Forbidden</h1><p>Unauthorized IP Address.</p><p>Either disable the IP address whitelist or add your address to it.</p><p>If you're editing settings.json, see the 'rpc-whitelist' and 'rpc-whitelist-enabled' entries.</p><p>If you're still using ACLs, use a whitelist instead.  See the transmission-daemon manpage for details.</p>
Accept-Encoding: deflate, gzip
Content-Length: 233https://forum.transmissionbt.com/viewtopic.php?f=8&t=6752
Content-Type: application/x-www-form-urlencoded

{"arguments":{"fields":["error","errorString","eta","id","isFinished","leftUntq

```I think I can figure it out, but I don't know where the config files go/are for transmission-remote. 

thanks 
wbg


EDIT: ok it was easy to find...I feel dumb...I tried again after adding my static behind router ip for my laptop, 10.0.0.11, to the list with the same syntax...got the same message, perhaps I need to restart something...and does it work with the regular GUI transmission ?

---

### Post by wannabegeek on 2010-08-29
guessed at a restart command...
```

lucky@lucky-desktop:~/.config$ sudo /etc/init.d/transmission-daemon restart
 * Restarting bittorrent daemon transmission-daemon                                                                                                  [12:52:58.034] Couldn't read "/home/lucky/.config/user-dirs.dirs": Permission denied

```                

I find that error baffling since I used sudo....and ls -l shows root ownership...

---

### Post by wannabegeek on 2010-08-29
Got it working but not sure exactly sure which step made it happen. 

First off, I was only able to restart transmission-daemon by becoming root sudo su
then $/etc/init.d/transmission-daemon restart

Also, there is a second config file in /etc/transmission-daemon/settings.json
I don't know why that would but it's there. I have the settings.json below that I used for both config files in /etc/transmission-daemon and  /home/.config/transmission-daemon

I added the IP address of all machines behind my router as 10.0.0.* , disabled authentication and changed the rpc-user name to ""  
[php]
lucky@lucky-desktop:/etc/transmission-daemon$ cat settings.json 
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
    "blocklist-enabled": true, 
    "dht-enabled": true, 
    "download-dir": "\/var\/lib\/transmission-daemon\/downloads", 
    "download-limit": 100, 
    "download-limit-enabled": 0, 
    "encryption": 1, 
    "lazy-bitfield-enabled": true, 
    "max-peers-global": 200, 
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
    "port-forwarding-enabled": false, 
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
    "rpc-authentication-required": false, 
    "rpc-bind-address": "0.0.0.0", 
    "rpc-enabled": true, 
    "rpc-password": "{6952374043c91bc203e8f8bdc1e126067eeed2cdXlimen37", 
    "rpc-port": 9091, 
    "rpc-username": "", 
    "rpc-whitelist": "127.0.0.1,10.0.0.*", 
    "rpc-whitelist-enabled": true, 
    "speed-limit-down": 100, 
    "speed-limit-down-enabled": false, 
    "speed-limit-up": 100, 
    "speed-limit-up-enabled": false, 
    "umask": 18, 
    "upload-limit": 100, 
    "upload-limit-enabled": 0, 
    "upload-slots-per-torrent": 14
}
[/php]

---

