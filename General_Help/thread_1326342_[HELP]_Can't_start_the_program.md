---
title: "[HELP] Can't start the program"
date: 2009-11-14
forum: General Help
---

### Post by SudoKenneth on 2009-11-14
Hello Ubuntu community!

I recently installed ubuntu, and i must say, it's HARD!

My first mission is to install the Peerguardian program, and of course i found the epic guide ( [http://ubuntuforums.org/showthread.php?t=95793](http://ubuntuforums.org/showthread.php?t=95793) )

And the installation went well until the point where i was supposed to start the program with:

Code: sudo peerguardian.sh start

I got the message in my terminal:

------------ 2009-11-14 05:05:51 PM CET Begin PeerGuardian start
File level1.gz last updated 2009-11-14 05:55:47.000000000 +0100
--2009-11-14 17:05:51--  [http://www.bluetack.co.uk/config/level1.gz](http://www.bluetack.co.uk/config/level1.gz)
Resolving [www.bluetack.co.uk]("http://www.bluetack.co.uk")... 67.18.178.4
Connecting to [www.bluetack.co.uk|67.18.178.4|:80]("http://www.bluetack.co.uk%7C67.18.178.4%7C:80")... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://rps8755.ovh.net/blocklists/level1.gz](http://rps8755.ovh.net/blocklists/level1.gz) [following]
--2009-11-14 17:05:51--  [http://rps8755.ovh.net/blocklists/level1.gz](http://rps8755.ovh.net/blocklists/level1.gz)
Resolving rps8755.ovh.net... 94.23.197.115
Connecting to rps8755.ovh.net|94.23.197.115|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3738543 (3.6M) [application/octet-stream]
Server file no newer than local file `level1.gz' -- not retrieving.

No blocklists needed updating.
Starting PeerGuardian
mv: cannot stat `/var/log/PG.log': No such file or directory
peerguardnf: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
------------ 2009-11-14 05:05:51 PM CET End PeerGuardian Script
get@get:~$ sudo gedit /usr/local/bin/peerguardian.sh
get@get:~$ 


What am i doing wrong?

Ty

---

