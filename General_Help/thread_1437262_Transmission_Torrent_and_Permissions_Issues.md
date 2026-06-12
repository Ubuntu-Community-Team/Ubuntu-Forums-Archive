---
title: "Transmission Torrent and Permissions Issues"
date: 2010-03-23
forum: General Help
---

### Post by rockinthesixstring on 2010-03-23
I just got Transmission setup with the following settings.
 
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
"complete-dir": "\/media\/media\/complete", 
"dht-enabled": true, 
"download-dir": "\/media\/media\/Downloads", 
"encryption": 1, 
"lazy-bitfield-enabled": true, 
"message-level": 2, 
"open-file-limit": 32, 
"peer-limit-global": 240, 
"peer-limit-per-torrent": 60, 
"peer-port": 1235, 
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
"rpc-authentication-required": false, 
"rpc-bind-address": "0.0.0.0", 
"rpc-enabled": true, 
"rpc-password": "{79d1b523b0213fd388679b3449077d924677b541BMrnChQF", 
"rpc-port": 2344, 
"rpc-username": "", 
"rpc-whitelist": "127.0.0.1", 
"rpc-whitelist-enabled": false, 
"speed-limit-down": 900, 
"speed-limit-down-enabled": true, 
"speed-limit-up": 200, 
"speed-limit-up-enabled": true, 
"umask": 0, 
"upload-slots-per-torrent": 14
}

```
 
I'm running a Samba server and connecting to my HTPC via a SMB share.
 
When I try and transfer a file out of the **/media/media/downloads** folder, I get the following error...
 
> You need permission to perform this action

You require permission from Unix User\debian-transmission to make changes to this file.

 
Can anyone tell me what I might be doing wrong?  I really need to be able to transfer all of my files out of the downloads directory when they are complete.

---

### Post by geirha on 2010-03-23
Is transmission giving you that error message? Or nautilus?

What are the permissions on that directory currently?
```
ls -ld /media/media/downloads
```

EDIT: Oh, btw, there's no configuration option called "complete-dir".

Set "incomplete-dir" to the location you want data to go when downloading. It will then be moved to "download-dir" when the download is complete.

---

### Post by rockinthesixstring on 2010-03-23
It's actually Windows 7 showing the permissions error.
 
The directory permissions say...
 
```
drwxrwxrwx 4 xbmc xbmc 4096
```
not entirely sure what that means.
 
> **geirha said:**
> Oh, btw, there's no configuration option called "complete-dir".
 
Set "incomplete-dir" to the location you want data to go when downloading. It will then be moved to "download-dir" when the download is complete.
 
Yeah the "complete-dir" never worked.  I just saw it in another forum so I thought I'd give it a try

---

### Post by rockinthesixstring on 2010-03-23
Ok, so my OLD settings.json file had UMASK = 18
 
I changed it to UMASK = 0
I did sudo chmod -R 777 /media/media/Downloads
 
and now everything is accessable.

---

